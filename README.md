# MatrixViewer
Large and complicated matrices can be challenging to understand and visualize. Utilising Jupyter Notebooks, DataShader, HoloViews, and 
Bokeh, the size of Matrix that can be viewed in MatrixViewer is only really limited by the amount of memory available. Plots are dynamically updated when zooming in on features, and properties 
of the data are dynamically aggregated allowing for quick detection of features such as extreme values and strong connections.

<p>
<img src="https://github.com/ChristopherLemon/MatrixViewer/blob/master/Wiki/MatrixPlot.jpg" width="45%" title="Large Matrix Visualization">
<img src="https://github.com/ChristopherLemon/MatrixViewer/blob/master/Wiki/MatrixPlotZoom.jpg" width="45%" title="Dynamic Zoom">
</p>
<p>
<img src="https://github.com/ChristopherLemon/MatrixViewer/blob/master/Wiki/MatrixAggregate.jpg" width="45%" title="Dynamically Aggregated Data">
<img src="https://github.com/ChristopherLemon/MatrixViewer/blob/master/Wiki/MatrixAggregateZoom.jpg" width="45%" title="Dynamic Zoom">
</p>

# Setup 
Requires [Anaconda](https://conda.io/docs/user-guide/install/download.html)

cd into the matrix_viewer directory. Then create the Conda environment required for the Jupyter Notebook

    conda env create -f environment.yml
    
Launch Jupyter

    jupyter notebook
    
Select the MatrixViewer notebook. Copy the matrix into the matrix_viewer/MATRICES directory. The list of matrices to analyse is
contained in the first code block

    file_list = ["MATRICES/matrix.txt"]
    
The matrix is identified by a start pattern (regex_1), followed by rows of matrix data (regex_2), followed by a termination pattern (regex_3), which can be modified for slightly different formats. The default data input is

    G=[
    int int float
    ...
    ...
    int, int, float
    ]
