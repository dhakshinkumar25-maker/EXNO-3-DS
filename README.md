## EXNO-3-DS

# AIM:
To read the given data and perform Feature Encoding and Transformation process and save the data to a file.

# ALGORITHM:
STEP 1:Read the given Data.
STEP 2:Clean the Data Set using Data Cleaning Process.
STEP 3:Apply Feature Encoding for the feature in the data set.
STEP 4:Apply Feature Transformation for the feature in the data set.
STEP 5:Save the data to the file.

# FEATURE ENCODING:
1. Ordinal Encoding
An ordinal encoding involves mapping each unique label to an integer value. This type of encoding is really only appropriate if there is a known relationship between the categories. This relationship does exist for some of the variables in our dataset, and ideally, this should be harnessed when preparing the data.
2. Label Encoding
Label encoding is a simple and straight forward approach. This converts each value in a categorical column into a numerical value. Each value in a categorical column is called Label.
3. Binary Encoding
Binary encoding converts a category into binary digits. Each binary digit creates one feature column. If there are n unique categories, then binary encoding results in the only log(base 2)ⁿ features.
4. One Hot Encoding
We use this categorical data encoding technique when the features are nominal(do not have any order). In one hot encoding, for each level of a categorical feature, we create a new variable. Each category is mapped with a binary variable containing either 0 or 1. Here, 0 represents the absence, and 1 represents the presence of that category.

# Methods Used for Data Transformation:
  # 1. FUNCTION TRANSFORMATION
• Log Transformation
• Reciprocal Transformation
• Square Root Transformation
• Square Transformation
  # 2. POWER TRANSFORMATION
• Boxcox method
• Yeojohnson method

# CODING AND OUTPUT:
       import pandas as pd
    df=pd.read_csv("Encoding Data.csv")
    df

<img width="316" height="330" alt="image" src="https://github.com/user-attachments/assets/4a2723a4-06dc-4d30-b5c8-9c978d121064" />

    from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
    pm=['Hot','Warm','Cold']
    e1=OrdinalEncoder(categories=[pm])
    e1.fit_transform(df[["ord_2"]])
    
<img width="159" height="172" alt="image" src="https://github.com/user-attachments/assets/d0b0fb27-2be1-4d5d-807a-7abbba5b281d" />

    df['bo2']=e1.fit_transform(df[["ord_2"]])
    
<img width="338" height="330" alt="image" src="https://github.com/user-attachments/assets/101c8502-51ee-46e9-a060-dbe717a087ec" />


    le=LabelEncoder()
    dfc=df.copy()
    dfc['ord_2']=le.fit_transform(dfc['ord_2'])
    dfc

<img width="320" height="327" alt="image" src="https://github.com/user-attachments/assets/f03b364e-2968-4501-a6bb-869547955377" />

    from sklearn.preprocessing import OneHotEncoder
    ohe=OneHotEncoder(sparse_output=False)
    df2=df.copy()
    enc=pd.DataFrame(ohe.fit_transform(df2[['nom_0']]))
    df2=pd.concat([df2,enc],axis=1)
    df2

<img width="398" height="318" alt="image" src="https://github.com/user-attachments/assets/36adccdb-1a9c-4952-8ae6-a7579ded460f" />


    pd.get_dummies(df2,columns=["nom_0"])



<img width="458" height="336" alt="image" src="https://github.com/user-attachments/assets/7830532d-5047-4315-962b-8730ad62b2d6" />

    pip install --upgrade category_encoders

<img width="654" height="506" alt="image" src="https://github.com/user-attachments/assets/b4d3d3a0-41db-43f5-a684-4a99af32362a" />
    from category_encoders import BinaryEncoder
    df=pd.read_csv("data.csv")
    df

<img width="427" height="330" alt="image" src="https://github.com/user-attachments/assets/80db4f9f-abc0-4715-985c-5d775c02d1ff" />

    be=BinaryEncoder()
    nd=be.fit_transform(df['Ord_2'])
    dfb=pd.concat([df,nd],axis=1)
    dfb1=df.copy()
    dfb


<img width="583" height="323" alt="image" src="https://github.com/user-attachments/assets/78ce748a-b139-430a-a220-fa07798dffae" />


    from category_encoders import TargetEncoder
    te=TargetEncoder()
    cc=df.copy()
    new=te.fit_transform(X=cc['City'],y=cc['Target'])
    cc=pd.concat([cc,new],axis=1)
     cc

<img width="461" height="339" alt="image" src="https://github.com/user-attachments/assets/c88da20e-de7e-4c1e-a0f7-20aa56f15fba" />

    import pandas as pd
    from scipy import stats
    import numpy as np
    df=pd.read_csv("Data_to_Transform.csv")
    df

<img width="620" height="384" alt="image" src="https://github.com/user-attachments/assets/c9ccc561-5bc0-4021-b604-10d834e13dbd" />

    df.skew()

<img width="256" height="94" alt="image" src="https://github.com/user-attachments/assets/0def9ccb-bc71-4909-bb57-070f88ebb949" />

    np.log(df["Highly Positive Skew"])

<img width="420" height="196" alt="image" src="https://github.com/user-attachments/assets/c30f1ffa-2174-49e6-8f0c-6043c5673eef" />

    np.reciprocal(df["Moderate Positive Skew"])

<img width="480" height="203" alt="image" src="https://github.com/user-attachments/assets/fac3e337-a1d9-4dd8-ac57-9e58493f9cb7" />

    np.sqrt(df["Highly Positive Skew"])

<img width="443" height="202" alt="image" src="https://github.com/user-attachments/assets/2ca4f8c0-6bf0-4bdb-8b97-902d68e1f162" />

    np.square(df["Highly Positive Skew"])

<img width="402" height="195" alt="image" src="https://github.com/user-attachments/assets/b9c15df0-7a4f-4696-bf28-a27e3f6c23bc" />

    import pandas as pd
    from scipy import stats
    import numpy as np
    df=pd.read_csv("Data_to_Transform.csv")
    df["Highly Positive Skew_boxcox"], parameters=stats.boxcox(df["Highly Positive Skew"])
    df

<img width="627" height="395" alt="image" src="https://github.com/user-attachments/assets/e5d23cab-7c10-4f38-811a-2ec6d8064b89" />

    df["Moderate Negative Skew_yeojohnson"], perameters=stats.yeojohnson(df["Moderate Negative Skew"])
    df.skew()


<img width="350" height="124" alt="image" src="https://github.com/user-attachments/assets/9416da4f-2534-449f-9258-7ea9f444e1ca" />

    df["Highly Negative Skew_yeojohnson"], perameters=stats.yeojohnson(df["Highly Negative Skew"])
    df.skew()

<img width="382" height="144" alt="image" src="https://github.com/user-attachments/assets/e0e1012d-d136-402c-82ab-22c15e3efbe0" />

    from sklearn.preprocessing import QuantileTransformer
    qt=QuantileTransformer(output_distribution='normal')
    df["Moderate Negative Skew_1"]=qt.fit_transform(df[["Moderate Negative Skew"]])
    df


<img width="639" height="401" alt="image" src="https://github.com/user-attachments/assets/9bc66fa1-87d5-487b-9586-c6a888e4d724" />

    import seaborn as sns
    import statsmodels.api as sm
    import matplotlib.pyplot as plt
    sm.qqplot(df["Moderate Negative Skew"],line='45')
    plt.show()
 

<img width="576" height="395" alt="image" src="https://github.com/user-attachments/assets/b848a9ec-3b7d-473e-b21e-7f744cb1295b" />

    sm.qqplot(np.reciprocal(df["Moderate Negative Skew"]),line='45')
    plt.show()

<img width="577" height="397" alt="image" src="https://github.com/user-attachments/assets/50221d68-f8f7-4288-a431-d19ca1c392b6" />

    from  sklearn.preprocessing import QuantileTransformer
    qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)
    df["Moderate Negative Skew"]=qt.fit_transform(df[["Moderate Negative Skew"]])
    sm.qqplot(df["Moderate Negative Skew"],line='45')
    plt.show()


<img width="601" height="409" alt="image" src="https://github.com/user-attachments/assets/0abd71cb-7a22-45e9-b041-cf7511155680" />

    df["Highly Negative Skew_1"]=qt.fit_transform(df[["Highly Negative Skew"]])
    sm.qqplot(df['Highly Negative Skew'],line='45')
    plt.show()


<img width="614" height="402" alt="image" src="https://github.com/user-       attachments/assets/9d9ff308-1f05-4088-97aa-a5092b4dd7f7" />
    sm.qqplot(df['Highly Negative Skew_1'],line='45')
    plt.show()

<img width="550" height="408" alt="image" src="https://github.com/user-attachments/assets/e1f74053-4b60-49d5-8278-cf43a5a158c9" />

    dt=pd.read_csv("titanic_dataset.csv")
    from sklearn.preprocessing import QuantileTransformer
    qt=QuantileTransformer(output_distribution='normal',n_quantiles=891)
    dt["Age_1"]=qt.fit_transform(dt[["Age"]])
    sm.qqplot(dt['Age'],line='45')
    plt.show()

<img width="580" height="398" alt="image" src="https://github.com/user-attachments/assets/c8b9b7e1-dc07-494d-ba45-d5f101a49888" />

    sm.qqplot(dt['Age_1'],line='45')
    plt.show()


<img width="583" height="406" alt="image" src="https://github.com/user-attachments/assets/cb5d9d88-e3b7-41a6-b9cd-6aac916cd85c" />


       Thus the given data, Feature Encoding, Transformation process and save the data to a file was performed successfully.

       

# RESULT:
       Thus the given data, Feature Encoding, Transformation process and save the data to a file was performed successfully.


       
