## Begin With
- Open Tableau and load the adult_dataset.csv and Adult_NW1.csv. in it
- Drag the Adult_NW1.csv to the interface and make a relation of both files as shown below.
  ![Image](https://github.com/user-attachments/assets/4ffdcbd0-1792-4c4c-8ddd-85f66f4244a2)

### 1. 1D Visualization
- Add `Age` in ROWS and `Race` in Color section.
- Visualization : `Stacked Bars`
  ![Image](https://github.com/user-attachments/assets/1fbdbeca-a1c5-4874-87f8-2d52bb8f9a36)

### 2. 2D Visualization
- Add `Occupation` in COLUMNS and `Age` in ROWS.
- **Income** in Color and `Race` in Label.
- Visualization : No need to change.
  ![Image](https://github.com/user-attachments/assets/02a44b33-6b1a-40af-b61a-8283c9af2526)

### 3. 3D Visualization
- Add `Occupation` and `Marital-Status` in COLUMNS and `Age` in ROWS.
- `Race` in Color.
- Visualization : No need to change.
  ![Image](https://github.com/user-attachments/assets/6398fde1-8eeb-499c-929b-d9988f00899f)

### 4. Tree/ Hierarchical Data Visualization
- Add `Age` to Color and Size, `Income` and `Occupation` in Label.
- Visualization : No need to change, by default Treemap is selected.
  ![Image](https://github.com/user-attachments/assets/efd4edb5-37fa-4590-b1d1-d6b0defbb3be)

### 5. Network Data Visualization
- Add `Line X` in COLUMNS, right click and check for Dimension and Continuous.
- Add `Line Y` and **Circle Y** in ROWS and do the same, then right click on `Circle Y` and click on `Dual Axis`.
- In Marks field, click on `Line Y` and change Automatic to Line, add `Measure Names` in Color `Relationship1` in Detail.
- Click on `Circle Y` and change Automatic to Circle, add `Node` in Color and Lable part, `Relationship1` in Detail.
- Visualization : Default
  ![Image](https://github.com/user-attachments/assets/9db704e6-7905-45ef-94df-c2b7534c3093)

### 6. Multidimensional Visualization
- Add `Hours-Per-Week` in COLUMNS, right click and chose AVG for it.
- Add `Age` in ROWS, right click and chose AVG for it.
- In Filters, add `Gender`, in Colors add `Education`, in Size add `SUM(Capital-Gain)`, in Tooltip add `Income`, `Occupation` and `Race` and set the to ATTRIBUTE, finally add `Node` in Detail.
- Visualization : Default
  ![Image](https://github.com/user-attachments/assets/dbc0e7b8-09b4-45ff-85a0-990a11c4032b)

### 7. Temporal Visualization
- Right-click anywhere in the Data pane
- Select "Create Calculated Field...".
- In the dialog box: Name the field and Enter the formula - `1994 - [Age]`
- Here it is named as `Year of Birth`, add it in COLUMNS and `Occupation` in ROWS, right click on it and change to CNTD.
- Add `Education` and `Gender` in Filters and `Income` in Colors.
- Visualization : Line Continuous
  ![Image](https://github.com/user-attachments/assets/91a6c340-d748-49ce-bf4d-70ed12a13512)

### Final Dashboard Creation
![Image](https://github.com/user-attachments/assets/92c0aceb-e16d-42ae-b9c6-8761298a8df6)
