# machineLearning
ML/DL practice 

``` py
class Perceptron(object):

def __inti__(self, eta=0.01, n_iter=50, random_state=1): ＃建構子, self 物件初始化
   self.eta = eta
   self.n_iter = n_iter
   self.random_state = random_state

def fit(self, X, y): ＃給已知資料訓練,估計參數
    rgen = np.random.RandomState(self.random_state)
    self.w_ = rgen.normal(loc=0.0, scale=0.01, size=1 + X.shape[1])＃w初始值設定 
    
    self.errors_ = []

    for _ in range(self.n_iter):
       errors = 0
       for xi, target in zip(X, y):
           update = self.eta*(target – self.predict(xi))
           self.w_[1:] += update*xi
           self.w_[0] += update
           errors += int(update!=0.0)
       self.errors_.append(errors)
    return self

＃ppn.fit(X,y)

```
![image](https://github.com/RandomErwin/machineLearning/blob/main/感知器.png)
![image](https://github.com/RandomErwin/machineLearning/blob/main/收斂.png)
