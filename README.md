ross Validation for Robust SVM models by Gaussian assumption  
==============================================================

Overview
--------
This project implements a robust classification framework by Gaussian assumption
using Support Vector Machines (SVMs). The model integrates optimization techniques 
to evaluated Cross-Validation (CV) schemes.

Structure
---------
CV_CoDo_DN_iter_Set1.m		- CV for Cobb-Douglas model (Feasible set 1) 
CV_CoDo_DN_iter_Set2.m 		- CV for Cobb-Douglas model (Feasible set 2) 
CV_L2_CoDo_DN_Iter_Set1.m	- CV for Cobb-Douglas model with L2-regularization (Feasible set 1) 
CV_L2_CoDo_DN_Iter_Set2.m	- CV for Cobb-Douglas model with L2-regularization (Feasible set 2) 
CV_GRID_TWSVM.m          	- CV for TWSVM model (with linear kernel)
CV_GRID_TWSVM_kernel		- CV for TWSVM model (with nonlinear kernel)
CV_LSOCP_DiNo_Set1.m     	- CV for GMMC model (Feasible set 1) 
CV_LSOCP_DiNo_Set2.m     	- CV for GMMC model (Feasible set 2) 
CV_MEMPM_Gauss.m.        	- CV for MEMPM model
CV_mpm.m                 	- CV for MPM model 
CV_Network.m             	- CV for Neural network
CV_Regula_LogistRegression.m  	- CV for L2/L1-Logistic Regression
medi_auc_accu			- Compute: AUC (Baccu), Accuracy, sensitivity, specificity 
                
Scheme/               - Folder containing classification and optimization models
	build_MEMPM_lin_bi_QI.m
	itera_CoDo_DN_FeSe1.m
	itera_CoDo_DN_FeSe2.m
	itera_L2_CoDo_DN_FeSe1.m
	itera_L2_CoDo_DN_FeSe2.m
	kernelfun.m
	mean_cova.m
	mpm_cvx.m
	qpSOR.m
	solve_FP_RG.m
	SVM_soc_Set1_cvx.m
	SVM_soc_Set2_cvx.m
	TWSVM.m

dataset/                 - Folder containing datasets in *.mat format
    australian.mat
    diabetes.mat
    german_credit.mat
    image_n.mat
    ionosphereN.mat
    segment0_n.mat
    splice.mat
    x18data.mat
    yeast3.mat

Main Components
---------------
1. Main Scripts (CV_*.m): 
   Entry point of the program. Users set parameters and execute the simulation from each script.
2. Models (Scheme/): 
   Contains optimization functions implementing various SVM-based classification techniques.
3. Data (dataset/): 
   Contains .mat files with sample datasets used for classification.


How to Use
----------
Step 1: Set User Parameters
    Modify the `CV_*.m` script to configure the parameters for your simulation. Key parameters include:
    - gauss_assumption: 1 <- Gaussian, 2<- Worst-case.
    - type: Cholesky factorization ('chol') or estimated ('estim').
    - kerfPara.type:  'lin' (lineal kernel) or 'rbf' (nonlinear kernel, RBF)  

Step 2: Run the Script
    Run `CV_*.m` in MATLAB. The script will:
    1. Load the specified dataset from the `dataset` folder.
    2. Perform classification using the configured SVM model.
    3. Evaluate the model with  CV schemes.



Available Methods in the Scheme Directory
------------------------------------------

The following methods are included in the `Scheme` directory, each implementing a specific SVM optimization approach:

- TWSVM			: Solves the Twin SVM model (Jayadeva et al) by SOR algorithm. 
- qpSOR			: Successive overrelaxation technique (SOR) for solving a particular 
			  Quadratic Programing problem
- mpm_cvx		: Solve the Minimax probability machine approach by CVX solver
- SVM_soc_Set1_cvx	: Solves the SOCP Problem associated to RMMC and Feasible Set 1, by CVX solver
- SVM_soc_Set2_cvx	: Solves the SOCP Problem associated to RMMC and Feasible Set 2, by CVX solver 
- solve_FP_RG		: solves a Fractional Programming (FP) Problem by the Rosen Gradient projection method
- build_MEMPM_lin_bi_QI	: Solves the minimum error minimax probability machine (MEMPM, linear version) for binary 
			  classification using sequential biased minimax probability machine (BMPM) method
- itera_CoDo_DN_FeSe1	: Solves the Cobb-Douglas Learning Machine model by a two-step iterative 
 		          algorithm (Feasible Set 1)
- itera_CoDo_DN_FeSe2	: Solves the Cobb-Douglas Learning Machine model by a two-step iterative 
 		          algorithm (Feasible Set 2)
- itera_L2_CoDo_DN_FeSe1: Solves the Cobb-Douglas Learning Machine model with L2-regularization, 
		          by a two-step iterative algorithm (Feasible Set 1) 	
- itera_L2_CoDo_DN_FeSe2: Solves the Cobb-Douglas Learning Machine model with L2-regularization, 
		          by a two-step iterative algorithm (Feasible Set 2)

- Others:
	kernelfun: Constructs the positive (semi-) definite and symmetric kernel matrix
	mean_cova: Compute the mean and covariance matrix of the two classes.
	

Requirements
------------
- MATLAB (Tested with R2021a and later)
- CVX toolbox for convex optimization (Download: https://cvxr.com/cvx/download/)

Examples
--------
Example: Running with the 'australian.mat' dataset
    1. Set load('ionosphereN.mat') in `CV_*.m`.
    2. Run the script in MATLAB.


Contact
-------
For questions or support, contact:
- Miguel Carrasco: macarrasco@miuandes.cl
- Julio López: julio.lopez@udp.cl
- Sebastián Maldonado: semaldonad@fen.uchile.cl
