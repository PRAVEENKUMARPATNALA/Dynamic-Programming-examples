1. Longest Increasing Subsequence
          
          O(N^2) approach
          def longestIncreasingSubsequence(arr):
              # Write your code here
              l=[1]*n
              for i in range(1,len(arr),1):
                  for j in range(0,i,1):
                      if(arr[i]>arr[j]):
                          x=l[j]+1
                          if(x>l[i]):
                              l[i]=x
              return max(l) 
2. Longest Common Subsequence

          def longestCommonSubsequence(a, b):
              l=[[0]*(len(a)+1) for i in range(len(b)+1)]
              for i in range(1,len(b)+1,1):
                  for j in range(1,len(a)+1,1):
                      if(b[i-1]==a[j-1]):
                          l[i][j]=l[i-1][j-1]+1
                      else:
                          l[i][j]=max(l[i-1][j],l[i][j-1])
              print(l[len(b)][len(a)])
              result=[]
              r=len(b);c=len(a)
              while(l[r][c]>0):
                  x=l[r][c]
                  if(x==l[r-1][c]):
                      r-=1
                  elif(x==l[r][c-1]):
                      c-=1
                  else:
                      result.append(b[r-1])
                      r-=1
                      c-=1
              return result[::-1]
      
3. 0/1 Knapsack Problem

        t=int(input())
        for _ in range(t):
            s,n=map(int,input().split())
            w=[];p=[]
            for i in range(n):
                a,b=map(int,input().split())
                w.append(a)
                p.append(b)
            dp=[[0]*(s+1) for i in range(n+1)]
            for i in range(1,n+1,1):
                for j in range(1,s+1,1):
                    if(w[i-1]>s):
                        dp[i][j]=max(dp[i-1][j],dp[i][j-1])
                    else:
                        if(j-w[i-1]>=0):
                            dp[i][j]=max(dp[i-1][j-w[i-1]]+p[i-1],dp[i-1][j])
                        else:
                            dp[i][j]=max(dp[i-1][j],dp[i][j-1])
            print(dp[i][j])
      
 4. Edit String Problem

    i.  modify
    ii. insert
    iii.delete
    
          t=int(input())
          for _ in range(t):
            a=input()
            b=input()
            dp=[[0]*(len(a)+1) for i in range(len(b)+1)]
            for i in range(len(b)+1):
                for j in range(len(a)+1):
                    if(i==0):
                        dp[i][j]=j
                    elif(j==0):
                        dp[i][j]=i
                    elif(b[i-1]==a[j-1]):
                        dp[i][j]=dp[i-1][j-1]
                    else:
                        dp[i][j]=1+min(dp[i-1][j-1],dp[i-1][j],dp[i][j-1])
            print(dp[i][j])
        
    
