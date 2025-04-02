# 合併排序法 (Merge Sort) 示範程式
# 作者：Claude
# 日期：2025年4月2日

def merge_sort(arr):
    """
    合併排序法主函數
    參數:
        arr: 要排序的列表
    返回:
        排序後的列表
    """
    # 基本情況：如果列表長度小於等於1，則已排序
    if len(arr) <= 1:
        return arr
    
    # 分解：將列表分成兩半
    mid = len(arr) // 2
    left_half = arr[:mid]
    right_half = arr[mid:]
    
    # 遞歸排序兩半
    left_half = merge_sort(left_half)
    right_half = merge_sort(right_half)
    
    # 合併兩個已排序的部分
    return merge(left_half, right_half)

def merge(left, right):
    """
    合併兩個已排序的列表
    參數:
        left: 左半部排序列表
        right: 右半部排序列表
    返回:
        合併後的排序列表
    """
    result = []
    i = j = 0
    
    # 比較並依序取出較小的元素
    while i < len(left) and j < len(right):
        if left[i] <= right[j]:
            result.append(left[i])
            i += 1
        else:
            result.append(right[j])
            j += 1
    
    # 加入剩餘的元素
    result.extend(left[i:])
    result.extend(right[j:])
    
    return result

# 測試與示範
if __name__ == "__main__":
    # 測試案例1: 隨機整數列表
    test_array1 = [38, 27, 43, 3, 9, 82, 10]
    print("原始列表1:", test_array1)
    sorted_array1 = merge_sort(test_array1)
    print("排序後1:", sorted_array1)
    
    # 測試案例2: 已排序列表
    test_array2 = [1, 2, 3, 4, 5]
    print("\n原始列表2:", test_array2)
    sorted_array2 = merge_sort(test_array2)
    print("排序後2:", sorted_array2)
    
    # 測試案例3: 逆序列表
    test_array3 = [9, 8, 7, 6, 5, 4, 3, 2, 1]
    print("\n原始列表3:", test_array3)
    sorted_array3 = merge_sort(test_array3)
    print("排序後3:", sorted_array3)
    
    # 測試案例4: 包含重複元素的列表
    test_array4 = [5, 2, 5, 3, 1, 2, 4, 3]
    print("\n原始列表4:", test_array4)
    sorted_array4 = merge_sort(test_array4)
    print("排序後4:", sorted_array4)
    
    print("\n合併排序法步驟展示:")
    print("以[38, 27, 43, 3]為例")
    print("1. 分解: [38, 27] 和 [43, 3]")
    print("2. 繼續分解: [38], [27], [43], [3]")
    print("3. 合併: [27, 38] 和 [3, 43]")
    print("4. 最終合併: [3, 27, 38, 43]")
    
