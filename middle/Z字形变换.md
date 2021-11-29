class Solution {
    public String convert(String s,int rowNum){
        if(rowNum<2){
            return s;
        }
        //使用回旋法，碰见了分界线我们就回头  时间复杂度O（n），空间复杂度O（n）
        int downBounds=Math.min(s.length(),rowNum);
        
        //这个list的size就和我们下边界一致。
        List<StringBuilder> str=new ArrayList();
        
        
        for(int i=0;i <= downBounds-1;i++){
                str.add(new StringBuilder());
        }

        char[] chars=s.toCharArray();
        
        //error
        //进行数据的拼接，对应地址地方的数字进行拼接。
        //for(int j=0;j<=chars.length-1;j++>){
        //    str.get(j%downBounds).append(chars[j]);
        //}

        // 1 代表 向下行，-1代表下行 
        int forwardOrDown=1;
        int currentRowNum=0;
       for (char aChar : chars) {
            str.get(currentRowNum).append(aChar);
            if(currentRowNum==(rowNum-1)){
                forwardOrDown=-1;
            }else if (currentRowNum==0) {
                forwardOrDown=1;
            }
            currentRowNum+=forwardOrDown;
        }
        StringBuilder resu=new StringBuilder();
        for(StringBuilder sb: str){
            resu.append(sb);
        }
        return resu.toString();

    }

    //第二种方式， 感觉有点像高中的求数组规律的数学归纳法。我是不想找规律，要列出很多式子，花费很多时间去归纳总结。嗨呀

    class Solution {
    public String convert(String s, int numRows) {

        if (numRows == 1) return s;

        StringBuilder ret = new StringBuilder();
        int n = s.length();
        int cycleLen = 2 * numRows - 2;

        for (int i = 0; i < numRows; i++) {
            for (int j = 0; j + i < n; j += cycleLen) {
                ret.append(s.charAt(j + i));
                if (i != 0 && i != numRows - 1 && j + cycleLen - i < n)
                    ret.append(s.charAt(j + cycleLen - i));
            }
        }
        return ret.toString();
    }
}

作者：LeetCode
链接：https://leetcode-cn.com/problems/zigzag-conversion/solution/z-zi-xing-bian-huan-by-leetcode/
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
}