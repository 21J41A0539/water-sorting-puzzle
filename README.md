# water-sorting-puzzle
wATER SORTING PUZZLE IS ALL ABOUT THE SORTING ALGORIYHM IN WHICH I HAVE USED ALL TYPE OF SORTING ALGORITHM LIKE ,
BUBBLE SORTING
MERGE SORTING 
HEAP SORTING 
INSERTION SORT
QUICK SORT.......
def bubble_sort(bottles):
    n = len(bottles)
    for i in range(n):
        for j in range(0, n - i - 1):
            if bottles[j] > bottles[j + 1]:
                bottles[j], bottles[j + 1] = bottles[j + 1], bottles[j]
    return bottles

def selection_sort(bottles):
    n = len(bottles)
    for i in range(n):
        min_idx = i
        for j in range(i + 1, n):
            if bottles[j] < bottles[min_idx]:
                min_idx = j
        bottles[i], bottles[min_idx] = bottles[min_idx], bottles[i]
    return bottles

def insertion_sort(bottles):
    for i in range(1, len(bottles)):
        key = bottles[i]
        j = i - 1
        while j >= 0 and bottles[j] > key:
            bottles[j + 1] = bottles[j]
            j -= 1
        bottles[j + 1] = key
    return bottles

def merge_sort(bottles):
    if len(bottles) <= 1:
        return bottles
      mid = len(bottles) // 2
    left = merge_sort(bottles[:mid])
    right = merge_sort(bottles[mid:])
    
    return merge(left, right)

def merge(left, right):
    result = []
    i = j = 0
    while i < len(left) and j < len(right):
        if left[i] < right[j]:
            result.append(left[i])
            i += 1
        else:
            result.append(right[j])
            j += 1
    result.extend(left[i:])
    result.extend(right[j:])
    return result

def quick_sort(bottles):
    if len(bottles) <= 1:
        return bottles
    pivot = bottles[len(bottles) // 2]
    left = [x for x in bottles if x < pivot]
    middle = [x for x in bottles if x == pivot]
    right = [x for x in bottles if x > pivot]
    return quick_sort(left) + middle + quick_sort(right)

# Example usage
bottles = [3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5]
print("Original:", bottles)
print("Bubble Sort:", bubble_sort(bottles.copy()))
print("Selection Sort:", selection_sort(bottles.copy()))
print("Insertion Sort:", insertion_sort(bottles.copy()))
print("Merge Sort:", merge_sort(bottles.copy()))
print("Quick Sort:", quick_sort(bottles.copy()))
