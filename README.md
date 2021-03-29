# LCS
s1=input('enter a string:')
s2=input('enter another string:')
if len(s2)>len(s1):
    s2,s1=s1,s2


#Creating lcs matrix with inputted sting in one row and one column and filling rest with zero
lcs=[]
for i in range(len(s2)+2):
    l=[]
    for j in range(len(s1)+2):
        if i>1 and j==0:
            l.append(s2[i-2])
        elif i==0 and j>1:
            l.append(s1[j-2])
        else:
            l.append(0)
    lcs.append(l)        

#main code of lcs
#adding 1 if character matches else putting max of the previous row or column
for i in range(2,len(lcs)):
    for j in range(2,len(lcs[0])):
        if lcs[i][0]==lcs[0][j]:
            lcs[i][j]=1+lcs[i-1][j-1]
        else:
            lcs[i][j]=max(lcs[i-1][j],lcs[i][j-1])
#reading valus 
#bottom up approach
i=len(lcs)-1
s=''
while i>=0:
    j=len(lcs[0])-1
    while j>=0:
        if lcs[i][j]==0:
            i=0
            j=0
        elif lcs[i][j]>lcs[i][j-1]:
            s=lcs[0][j]+s
            i=i-1
            j=j-1
            continue
        j=j-1
    i=i-1    
print('Longest Common Substring is:',s)    

#printing the lcs matrix you can simply use: print(lcs)
for i in range(len(lcs)):
    for j in range(len(lcs[0])):
        print(lcs[i][j],end=' ')
    print()    
