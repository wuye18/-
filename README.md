# -你有一个炸弹需要拆除，时间紧迫！你的情报员会给你一个长度为 n 的 循环 数组 code 以及一个密钥 k 。

为了获得正确的密码，你需要替换掉每一个数字。所有数字会 同时 被替换。

如果 k > 0 ，将第 i 个数字用 接下来 k 个数字之和替换。
如果 k < 0 ，将第 i 个数字用 之前 k 个数字之和替换。
如果 k == 0 ，将第 i 个数字用 0 替换。
由于 code 是循环的， code[n-1] 下一个元素是 code[0] ，且 code[0] 前一个元素是 code[n-1] 。

给你 循环 数组 code 和整数密钥 k ，请你返回解密后的结果来拆除炸弹！

int* decrypt(int* code, int codeSize, int k, int* returnSize){
    int repeat[codeSize];
    *returnSize=codeSize;
    for(int i=0;i<codeSize;i++)
        repeat[i]=code[i];
   if(k==0){
       for(int i=0;i<codeSize;i++)
        code[i]=0;
        return code;
   }
   else{
       int sum=0;
       for(int i=0;i<abs(k);i++){
           sum+=repeat[i];
       }
       for(int i=0;i<codeSize;i++){
       if(k>0){
           code[(codeSize-1+i)%codeSize]=sum;
       }
       else{
           code[(abs(k)+i+codeSize)%codeSize]=sum;
       }
       sum-=repeat[i];
       sum+=repeat[(abs(k)+i+codeSize)%codeSize];
       }
      
   }
     return code;
}
