#### 两数之和

给定一个整数数组 nums 和一个目标值 target，请你在该数组中找出和为目标值的那 两个 整数，并返回他们的数组下标。

你可以假设每种输入只会对应一个答案。但是，你不能重复利用这个数组中同样的元素。

示例:

给定 nums = [2, 7, 11, 15], target = 9

因为 nums[0] + nums[1] = 2 + 7 = 9
所以返回 [0, 1]

#### 解法

```C
#include <stdio.h>
#include <stdlib.h>

int printArr(const *arr, const int size);

/***
 * find two number from int array which's summary equals to target
 */
int* twoSum(int* nums, int numsSize, int target) {
    int i, j, tmp, *result;
    // malloc reslut array space of 2 integers
    result = (int *) malloc(sizeof(int) * 2);
    for(i=0; i<numsSize; i++){
        if(nums[i] > target) {
            break;
        }
        // target - nums[i]
        tmp = target - nums[i];
        for(j=i+1; j<numsSize; j++) {
            // compare num[j] and tmp
            if(nums[j] == tmp) {
                result[0] = i;
                result[1] = j;
                return result;
            }
        }

    }

    return result;
}

int printArr(const *arr, const int size)
{
    int i;
    for(i=0; i<size; i++)
    {
        printf("%d\t", arr[i]);
    }

    return 0;
}

void main()
{
    int i, nums[] = {9, 7, 6, 1, 3}, *result;
    result = twoSum(nums, 5, 9);
    printArr(result, 2);
    printf("\n");
    free(result);
}
```
