this is dsa 
1]Greedy Approach Sort according end time i think






class Solution {
    int n;
    int dp[]=null;
    int getNextJobIdx(ArrayList<int[]>job,int left,int end){
        int right=n-1;
        int result=n+1;
        while(left<=right){
            int mid=left+(right-left)/2;
            if(job.get(mid)[0]>=end){
                right=mid-1;
                result=mid;
            }
            else left=mid+1;
        }
        return result;
    }
    int solve(ArrayList<int[]>job,int i){
        // if(i>=n)return 0;
        // if(dp[i]!=-1)return dp[i];
        // int nextJobIdx=getNextJobIdx(job,i+1,job.get(i)[1]);
        // int take=job.get(i)[2]+solve(job,nextJobIdx);
        // int notTake=solve(job,i+1);
        // return dp[i]=Math.max(take,notTake);
        int idx=0;
        // for( ;i<n;i++){
        //     int nextJobIdx=getNextJobIdx(job,idx+1,job.get(i)[1]);
        //     int take= (nextJobIdx>=n)?0:dp[nextJobIdx] + job.get(i)[2] ;
        //     int notTake=(i<n-1)?dp[i+1] :0;
        //     dp[i]=Math.max(take,notTake);               //not possible bottomup
        //     idx=nextJobIdx;
        // }
        // return dp[n-1];
    }
    public int jobScheduling(int[] startTime, int[] endTime, int[] profit) {
        this.n=startTime.length;
        ArrayList<int[]>job=new ArrayList<>();
        for(int i=0;i<n;i++){
            job.add(new int[3]);
            job.get(i)[0]=startTime[i];
            job.get(i)[1]=endTime[i];
            job.get(i)[2]=profit[i];
        }
        dp=new int[n];
        // Arrays.fill(dp,-1);
        Collections.sort(job,(a,b)->a[0]-b[0]);
        return solve(job,0);
        
    }
}