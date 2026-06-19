# MERGE INTERVALS 
USED WHEN -
There is given any range/interval in question 
and some keywords in question 
overlap , conflict , merge, freetime, simultaneous usage 
rooms , load ,cpu , meeting

## Q1.Meeting Rooms II
``` java
class Solution {
    public int minMeetingRooms(int[] start, int[] end) {
        // code here
        Arrays.sort(start);
        Arrays.sort(end);
        int room = 0;
        int res =0;
        int i =0;
        int j =0;
        while(i<start.length && j<end.length){
            if(start[i]<end[j]){
                room++;
                res=Math.max(res,room);
                i++;
            }else{
                room--;
                j++;
            }
        }
        return res;
    }
}
```

