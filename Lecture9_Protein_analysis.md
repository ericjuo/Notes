# Lecture 9. Protein Analysis
課程時間:2小時

## Pytraj
`pytraj` 是 AMBER 軟體套件的 Python 介面，專門用於 **分析分子動力學模擬的軌跡資料（MD trajectory）**。它是 `cpptraj` 的 Python 版本，提供更方便的語法、整合 Python 生態系的彈性。
📁 支援的檔案格式
Topology: .prmtop, .psf, .pdb  

Trajectory:  .dcd, .mdcrd, .xtc, .trr  

```
import pytraj as pt

traj = pt.load('traj.xtc', 'protein.pdb')
```

## RMSD
`mask`可以選取要計算的蛋白範圍
```python
rmsd = pt.analysis.rmsd.rmsd(traj, mask="@CA:21-246", ref=0)
time = np.linspace(0, 20, 2001)
data_rmsd = {
    "time": time,
    "rmsd": rmsd
}
pd.DataFrame(data_rmsd).to_csv(os.path.join(DIR, PREFIX+"_rmsd.csv"), index=False)
plt.plot(time, rmsd)
plt.xlabel("Time (ns)")
plt.ylabel("RMSD ($\AA$)")
plt.show()
```
## RMSF
`byres`代表以殘基為單位計算RMSF
```python
rmsf = pt.rmsf(traj,  mask=":21-246", options='byres')

data_rmsf={
    "residue": rmsf[:,0],
    "rmsf": rmsf[:,1]
}
pd.DataFrame(data_rmsf).to_csv(os.path.join(DIR, PREFIX+"_rmsf.csv"), index=False)
plt.plot(rmsf[:,0], rmsf[:,1])
plt.xlabel("Residue")
plt.ylabel("RMSF ($\AA$)")
```

## SASA
```python
time, sasa = np.loadtxt(os.path.join(DIR, PREFIX+"_sasa.xvg"),comments=["@", "#"],unpack=True)

data_sasa = {
    "time": time,
    "sasa": sasa
}
pd.DataFrame(data_sasa).to_csv(os.path.join(DIR, PREFIX+"_sasa.csv"), index=False)
plt.plot(time, sasa)
plt.xlabel("Time (ns)")
plt.ylabel("SASA ($nm^2$)")
```


## Rg
```python
# Rg
rg = pt.radgyr(traj, mask="@CA:21-246")
time = np.linspace(0, 20, 2001)
data_rg = {
    "time": time,
    "rg": rg
}
pd.DataFrame(data_rg).to_csv(os.path.join(DIR, PREFIX+"_rg.csv"), index=False)
plt.plot(time, rg)
plt.xlabel("Time (ns)")
plt.ylabel("Rg ($\AA$)")
plt.show()
```
## H-bond frequency
```
# H-bonds 
hb = pt.hbond(traj, mask=":21-246")
time = np.linspace(0, 20, 2001)
len(hb.total_solute_hbonds())
data_hb = {
    "time": time,
    "hb": hb.total_solute_hbonds()
}
# pd.DataFrame(data_hb).to_csv(os.path.join(DIR, PREFIX+"_rg.csv"), index=False)
plt.plot(time, hb.total_solute_hbonds())
plt.xlabel("Time (ns)")
plt.ylabel("Counts")
plt.show()
```




## binding energy
- MMPBSA

## plumed


### References
1. https://valdes-tresanco-ms.github.io/gmx_MMPBSA/dev/
2. https://www.plumed-tutorials.org/browse.html
3. https://amber-mdhttps://amber-md.github.io/pytraj/latest/index.html.github.io/pytraj/latest/index.html
4. 