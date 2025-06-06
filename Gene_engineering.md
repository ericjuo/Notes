# Gene engineering
## Plasmid extraction

Kit: FavorPrep Plasmid Extraction Mini Kit (FADPE300)
1. Take 2ml of overnight culture into a 2 ml eppendorf in a laminar flow.
2. Pellet cells at 12000rpm for 3 minutes, then discard supernatant.
3. Add 200ul of FADP1 buffer (at 4C refrigerator), and pipette until cells are fully suspended.
4. Add 200ul of FADP2 and invert the tubes 20 times.
5. Add 300ul of FADP3 and invert 20 times. Cell would be lysed at this step.
6. Centrifuge at 12000rpm for 10 minutes.
7. Transfer supernatant onto the filter tube.
8. Centrifuge at 12000rpm for 40 seconds and discard the flow-through.
9. Add 400ul of WP.
10. Centrifuge at 12000rpm for 40 seconds and discard the flow-through.
11. Add 750ul of wash buffer.
12. Centrifuge at 12000rpm for 40 seconds and discard the flow-through.
13. Centrifuge at 12000rpm for 3 minutes and discard the flow-through.
14. Add 40ul of preheated elution buffer. 
15. Place on a 70C heating plate for 1 minutes.
16. Centrifuge at 12000rpm for 3 minutes.
17. Measure concentration with Nano-400A. 



## Restriction enzyme cloning
### PCR
1. Dilute F/R primers to 10uM in a PCR tube (i.e. 1ul 100uM primer + 9ul ddH2O)
2. Prepare PCR mix:  

|Materials|Concentrations|Amount|
|---|---|---|
|Template||40-60 ng Plasmid|
|F primer|10 uM|1.5 ul|
|R primer|10 uM|1.5 ul|
|RealStart DNA polymerase (KOD)|2x|25 ul|
|ddH2O||Up to 50 ul|

3. PCR Program  

<table>
  <tr>
    <th>Step</th>
    <th>Temperature</th>
    <th>Time</th>
    <th>Cycle</th>
  </tr>
  <tr>
    <td>Pre-denature</td>
    <td>94C</td>
    <td>15 min</td>
    <td>1x</td>
  </tr>
  <tr>
    <td>Denature</td>
    <td>94C</td>
    <td>30 s</td>
    <td rowspan="3">25–30x</td>
  </tr>
  <tr>
    <td>Annealing</td>
    <td>55C</td>
    <td>30 s</td>
  </tr>
  <tr>
    <td>Extension</td>
    <td>72C</td>
    <td>1kb/min</td>
  </tr>
  <tr>
    <td>Final extension</td>
    <td>72C</td>
    <td>7 min</td>
    <td>1x</td>
  </tr>
  <tr>
    <td>Cooling</td>
    <td>4C</td>
    <td>∞</td>
    <td></td>
  </tr>
</table>

3. Prepare agarose 1% gel (i.e. 0.25 g Agarose + 25 mL TAE buffer)
4. Run DNA electrophoresis at 120V for 18 min

### Gel extraction

1. Cut the target band
2. Add 500ul of FADF buffer and boil at 70°C to dissolve the gel.
3. Decant all volume into the filter tube and centrifuge at 14000rpm for 30 seconds.
4. Add 750ul of wash buffer and centrifuge at 14000rpm for 30s. Discard the flow-through.
5. Centrifuge again for 3 minutes.
6. Add 25ul pre-heated elution buffer and place on a 70°C heating plate for 1 minutes
7. Centrifuge at 14000rpm for 3 minutes.
8. Measure concentration with Nano-400A.

### Restriction enzyme digestion
1. Digest the PCR product and the vector with restriction enzymes:

|Materials|Amount|
|---|---|
|DNA|1000 ng|
|CutSmart|5 uL|
|RE I|1 uL|
|RE II|1 uL|
|ddH2O|Up to 50 uL|

2. Enzyme digestion at 37C for 1 hour.

3. Run DNA electrophoresis to separate the vector and insert.

4. Clean up the digested PCR product and the vector using gel extraction kit.

5. Elute the PCR product with 20 uL elution buffer.  

### Ligation
1. Ligate the PCR product and the vector at 22C for 1 hour:

|Materials|Amount|
|---|---|
|Vector:Insert|1:6 (Total 15 uL)|
|Buffer A|2 uL|
|Buffer B|2 uL|
|T4 ligase|1 uL|
|Total| 20 uL|

### Transformation

1. Aliquot 20 uL DH5a competent cell from the tube.
2. Add 10 uL ligation liquid into the tube.
3. Place on ice for 10 min.
4. Heat the competent cell at 42C for 90s.
5. Place on ice for 10 min.
6. Add 400 uL LB medium and culture at 37C for 1.5 hr.
7. Concentrate the cell by centrifugating at 4000 rpm for 3 min.
8. Remove 200 uL medium
9. Resuspend the spread the cell on the antibiotic plate.

### Colony PCR (Optional)
1. Prepare PCR mix

|Materials|Amount|
|---|---|
|10 uM F primer|1 uL|
|10 uM R primer|1 uL|
|10 mM dNTP|0.4 uL|
|10x PCR buffer|2 uL|
|rTaw polymerase|0.2 uL|
|ddH2O| Up to 20 uL|
|Total| 20 uL|

2. Pick 5 colonies and mix with the PCR mix.
3. PCR program

<table>
  <tr>
    <th>Step</th>
    <th>Temperature</th>
    <th>Time</th>
    <th>Cycle</th>
  </tr>
  <tr>
    <td>Pre-denature</td>
    <td>94C</td>
    <td>5 min</td>
    <td>1x</td>
  </tr>
  <tr>
    <td>Denature</td>
    <td>94C</td>
    <td>30 s</td>
    <td rowspan="3">15–20x</td>
  </tr>
  <tr>
    <td>Annealing</td>
    <td>55C</td>
    <td>15 s</td>
  </tr>
  <tr>
    <td>Extension</td>
    <td>72C</td>
    <td>1kb/min</td>
  </tr>
  <tr>
    <td>Final extension</td>
    <td>72C</td>
    <td>10 min</td>
    <td>1x</td>
  </tr>
  <tr>
    <td>Cooling</td>
    <td>4C</td>
    <td>∞</td>
    <td></td>
  </tr>
</table>

4. Run DNA electrophoresis

### Restriction enzyme validation

1. Plasmid extraction
2. Digest the contruct with appropriate restriction enzyme.

|Materials|Amount|
|---|---|
|DNA|200 ng|
|CutSmart|1 uL|
|RE I|0.2 uL|
|RE II|0.2 uL|
|ddH2O|Up to 10 uL|
3. Incubate the mixure at 37C for 45 min.
4. Run DNA electrophoresis.

