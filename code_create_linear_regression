# Linear regression function
mylin=function(X,Y, Xpred){
  X = cbind(1,X)
  Xpred1=cbind(1,Xpred)
  beta = solve(t(X)%*%X)%*%t(X)%*%Y # (xt*x)^-1*xt*y
  Res=Xpred1%*%beta
  return(Res)
}

# Cross validation function

myCV=function(X,Y,Nfolds){
  n=length(Y)
  p=ncol(X)
  set.seed(12345)
  ind=sample(n,n)
  X1=X[ind,]
  Y1=Y[ind]
  sF=floor(n/Nfolds)
  MSE=numeric(2^p-1)
  Nfeat=numeric(2^p-1)
  Features=list()
  curr=0
  
  #we assume 5 features.
  
  for (f1 in 0:1)
    for (f2 in 0:1)
      for(f3 in 0:1)
        for(f4 in 0:1)
          for(f5 in 0:1){
            model= c(f1,f2,f3,f4,f5)
            if (sum(model)==0) next()
            SSE=0
            
            for (k in 1:Nfolds){
              # compute which indices should belong to current fold
              indicies = ((k-1)*sF+1):(k*sF)
			        # implement cross-validation for model with features in "model" and iteration i.
			        xtrain = X1[-indicies, which(model == 1)]
			        xtest = X1[indicies,which(model == 1)]
			        ytrain = Y1[-indicies]
			        yp = Y1[indicies]
              # Get the predicted values for fold 'k', Ypred, and the original values for folf 'k', Yp.
			        ypred = mylin(xtrain, ytrain, xtest)
              SSE=SSE+sum((ypred-yp)^2)
            }
            curr=curr+1
            MSE[curr]=SSE/n
            Nfeat[curr]=sum(model)
            Features[[curr]]=model
            
          }

  # plot MSE against number of features
  library(ggplot2)
  print(ggplot() + geom_point(aes(x = Nfeat, y = MSE)) + ggtitle("MSE Vs Features") + xlab("Number of Features") + ylab("MSE") + theme_classic())
  i=which.min(MSE)
  return(list(CV=MSE[i], Features=Features[[i]], Selected = colnames(X[,which(Features[[i]]==1)])))
}

myCV(as.matrix(swiss[,2:6]), swiss[[1]], 5)
