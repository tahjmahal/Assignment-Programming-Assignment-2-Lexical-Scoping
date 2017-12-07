# Assignment-Programming-Assignment-2-Lexical-Scoping
Example: Caching the Inverse of a Matrix
## CAaching Inverse of a matrix:
## the function will create a unique "matrix" object that can cashe its inverse

makeCacheMatrix<- function(x = matrix()) {
  inv<- NULL
  set<- function(y) {
    x <<- y
    inv<<- NULL
  }
  get<- function() x
  setInverse<- function(inverse) inv<<- inverse
  getInverse<- function() inv
  list(set = set,
       get = get,
       setInverse = setInverse,
       getInverse = getInverse)
}

cacheSolve<- function(x, ...) {
  ## calculate a matrix which is the inverse of 'x'
  inv<- x$getInverse()
  if (!is.null(inv)) {
    message("getting cached data")
    return(inv)
  }
  mat <- x$get()
  inv<- solve(mat, ...)
  x$setInverse(inv)
  inv
}
