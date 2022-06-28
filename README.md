# Deformation Transfer for Triangle Meshes
unofficial implementation.
see also https://people.csail.mit.edu/sumner/research/deftransfer/Sumner2004DTF.pdf



if you want to see demo.
 see this youtube : [link](https://www.youtube.com/watch?v=rih0KVmWKOM)



# deps
manually install below library
[PCL -1.12.1](https://github.com/PointCloudLibrary/pcl/releases/tag/pcl-1.12.1) kdtree


add it to your system environment path ```path/to/pcl/bin```
or ```set env in cmake```


auto installed libraries
```
libigl  
eigen  
spdlog  
yaml-cpp  
```



# LOGGING
for Eigen testing Use 
PRETTY_LOG_BEGIN(msg, category), PRETTY_LOG_END(msg, category), log_sparse(), log_dense()

```c++

#include <Eigen/Sparse>
#include <Eigen/Core>
#include "pretty_log.h"

// if you disable it. it doesn't write or execute anything 
// between PRETTY_LOG_BEGIN and PRETTY_LOG_END
#define category "category_name" 
PRETTY_LOG_BEGIN("test", "DENSE_WRITE")
your code....
PRETTY_LOG_END("test", "DENSE_WRITE")

// or 
Eigen::SparseMatrix<float> sp;
log_sparse(sp)

//or
Eigen::Matrix<float> mat;
log_dense(mat)

```


# dataset
if you want to test deformation transfer. please download additional datasets from author's webpage.
[face dataset Link](http://graphics.csail.mit.edu/~sumner/research/deftransfer/data.html)  
(If you use these meshes in a manner that relates to my paper, please
reference it.)




# etc
Eigen cross production doesn't take normalize into consideration.

But, numpy library cautiously dealing it.


```c++
// c++ code
Eigen::Vector3 a, b;
// assign a,b...
a.normalize(); b.normalize();
Eigen::Vector3 result  = a.cross(b);
```
equivalent c++ code as python 

```python 
# python code
a = np.array([.. .. ..])
b = np.array([.. .. ..])
c = np.cross(a, b)
```

