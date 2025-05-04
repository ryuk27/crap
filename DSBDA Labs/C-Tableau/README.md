## Begin With
- Open Tableau and load the adult_dataset.csv and Adult_NW1.csv. in it
- Drag the Adult_NW1.csv to the interface and make a relation of both files as shown below.
  ![Image](https://github.com/user-attachments/assets/4ffdcbd0-1792-4c4c-8ddd-85f66f4244a2)

## b. 2D (Planar) Data Visualization
- Load the dataset into Tableau.
- Select two dimensions or measures, such as Age and Education (Adult dataset) or Sepal Length and Sepal Width (Iris dataset).
- Drag one dimension (e.g., Age) to the Columns shelf and the second (e.g., Education) to the Rows shelf.
- Tableau will display a scatter plot or other appropriate visualization type.
- You can customize the axes, add color or size encoding, and adjust the marks for better representation.

## c. 3D (Volumetric) Data Visualization
- Tableau doesn't natively support 3D visualizations, but you can simulate 3D effects.
- Choose three variables, like Age, Education, and Hours per Week (Adult dataset) or Sepal Length, Sepal Width, and Petal Length (Iris dataset).
- Place one measure in the Columns shelf, another in the Rows shelf, and the third in the "Size" or "Color" shelf.
- Use a scatter plot or bubble chart to give a visual sense of 3D.
- To enhance the 3D effect, use depth cues like color gradients or size variations.

## d. Temporal Data Visualization
- For temporal analysis, ensure your dataset contains time-related data. In the Adult dataset, you could use Age, or for the Iris dataset, you might need to add a date attribute manually if not available.
- Drag the time-based dimension (e.g., Year or Age in intervals) to the Columns shelf.
- Drag a measure like Income or Sepal Length to the Rows shelf.
- Tableau will create a time series visualization like a line chart.
- Adjust the axis to show the appropriate time intervals and customize the chart with color, tooltips, and labels.

## e. Multidimensional Data Visualization
- Multidimensional visualization allows for more complex interactions between multiple dimensions and measures.
- Use dimensions such as Age, Education, and Hours per Week (Adult dataset) or Sepal Length, Petal Width, and Species (Iris dataset).
- Drag dimensions to the Rows and Columns shelves and measures to the "Color" or "Size" shelf.
- A good example of this is a heatmap or a packed bubble chart.
- Customize the view by adjusting colors, shapes, and filters.

## f. Tree/ Hierarchical Data Visualization
- Hierarchical data is used to visualize relationships like categories or subcategories.
- In the Adult dataset, you can use Education levels as a hierarchical dimension.
- Drag "Education" to the Rows shelf and use the "Detail" shelf to add subcategories like "Education-Num."
- Choose a Treemap or Sunburst chart from the "Show Me" tab to represent the hierarchy.
- Customize the hierarchy to allow for drill-down features.

## g. Network Data Visualization
- Network data visualizations focus on the relationships between entities. While this type of data is not natively part of the Adult or Iris dataset, you can simulate network connections using categorical data.
- Create a relationship between two dimensions (e.g., Age and Education) or create custom network data.
- Use a scatter plot or path analysis to visualize connections.
- Customize the view with lines or arrows connecting related entities, adjusting color to represent different relationships.
