# Algorithm for QR Decomposition
## Aim:
To implement QR decomposition algorithm using the Gram-Schmidt method.
## Equipment’s required:
1.	Hardware – PCs
2.	Anaconda – Python 3.7 Installation / Moodle-Code Runner
## Algorithm:
1.	Intialize the matrix Q and u
2.	The vector u and e is given by

    ![eqn1](./ex4.jpg)

    ![eqn2](./ex6.jpg)

    ![eqn3](./ex3.jpg)

3.	Obtain the Q matrix   
    ![eqn4](./ex1.jpg)
4.	Construct the upper triangular matrix R
    ![eqn5](./ex2.jpg)



## Program:
### Gram-Schmidt Method
```
''' 
Program to QR decomposition using the Gram-Schmidt method
Developed by: J Mohamed Arsath
RegisterNumber: 212225040237
'''
import os
os.environ["OPENBLAS_NUM_THREADS"] = "1"
import numpy as np
def QR_Decomposition(A):
    m, n = A.shape
    Q = np.zeros((m,n))
    R = np.zeros((n,n))
    for j in range(n):
        v = A[:,j].copy()
        for i in range(j):
            R[i,j] = np.dot(Q[:,i].T,A[:,j])
            v = v - R[i,j]*Q[:,i]
        R[j,j] = np.linalg.norm(v)
        Q[:,j] = v/R[j,j]
    return Q,R
A = np.array(eval(input()))
q,r = QR_Decomposition(A)
print("The Q Matrix is\n",q.round(8))
print("The R Matrix is\n",r.round(8))


```

## Output
```
<img width="1162" height="377" alt="image" src="https://github.com/user-attachments/assets/63c00f66-74cf-4bf8-8d02-50de6ae31131" />
<img width="1222" height="713" alt="image" src="https://github.com/user-attachments/assets/4431d027-2968-4c2b-ad21-28dc680fd8a7" />
<img width="1220" height="564" alt="image" src="https://github.com/user-attachments/assets/3b0071a3-5817-4368-8b09-2f9d2015968a" />

```

## Result
Thus the QR decomposition algorithm using the Gram-Schmidt process is written and verified the result.
