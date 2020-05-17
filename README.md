# MatrixViewer`
Large and complicated matrices can be challenging to understand and visualize. Utilising Jupyter Notebooks, DataShader, HoloViews, and 
Bokeh, the size of Matrix that can be viewed in MatrixViewer is only really limited by the amount of memory available. Plots are dynamically updated when zooming in on features, and properties 
of the data are dynamically aggregated allowing for quick detection of features such as extreme values and strong connections. If installed, the matrices can be solved and analyzed using the python interfaces to a variey of external solvers such as PETSc (for Linear system solvers), SLEPc (for eigenvalue analysis), or AMGX (for gpu solvers).

<p>
<img src="https://github.com/ChristopherLemon/MatrixViewer/blob/master/Wiki/MatrixPlot.jpg" width="45%" title="Large Matrix Visualization">
<img src="https://github.com/ChristopherLemon/MatrixViewer/blob/master/Wiki/MatrixPlotZoom.jpg" width="45%" title="Dynamic Zoom">
</p>
<p>
<img src="https://github.com/ChristopherLemon/MatrixViewer/blob/master/Wiki/MatrixAggregate.jpg" width="45%" title="Dynamically Aggregated Data">
<img src="https://github.com/ChristopherLemon/MatrixViewer/blob/master/Wiki/MatrixAggregateZoom.jpg" width="45%" title="Dynamic Zoom">
</p>

# Setup 
cd into the matrix_viewer directory, and install the relevant python packages.

To Ulilize Datashader\Holoviews visualization cells in Jupyter notebook:

    python -m venv mat_env
    source mat_env/bin/activate

    pip install "holoviews[recommended]"
    pip install datashader

To utilize PETSc linear solver:

First install dependencies

    pip install mpi4py (Requires an mpi implementation on path, if mpi is to be used with PETSc)
    pip install numpy

PETSc can be configured using a number of non-default different options. To use any of these options set
the PETSC_CONFIGURE_OPTIONS environment variable. For example,

    export PETSC_CONFIGURE_OPTIONS="--download-fblaslapack=1 --download-hypre=1 --download spai=1"

If PETSc is already installed set PETSC_DIR, and PETSC_ARCH appropriately. If PETSc is not
installed, then install with pip. PETSc can be configured using a number of non-default different options. To use any of these options set the PETSC_CONFIGURE_OPTIONS environment variable. For example,

    export PETSC_CONFIGURE_OPTIONS="--download-fblaslapack=1 --download-hypre=1 --download spai=1"

    pip install petsc

Then install petsc4py:

    pip install petsc4py

To utilize SLEPc eigensolvers, PETSC must already be installed. If SLEPc is alread installed then set the
SLEPC_DIR environment variable. If SLEPc is not installed, then install with pip:

    pip install slepc

Then install slepc4py

    pip install slepc4py

To Utilize AMGX solver:

First install python dependencies

    pip install scipy cython

Install AMGX library. 

    git clone https://github.com/NVIDIA/AMGX.git
    mkdir build
    cd build
    cmake ../
    make -j16 all

Then install pyamgx

    git clone https://github.com/shwina/pyamgx
    export AMGX_DIR=/path/to/AMGX
    export AMGX_BUILD_DIR=/path/to/AMGX/build
    cd pyamgx
    pip install .

Finally, launch Jupyter notebook

    jupyter notebook
    
Select the MatrixViewer notebook. The notebook reads amtrix market format matrices - the default directory for these matrices is named MTX

