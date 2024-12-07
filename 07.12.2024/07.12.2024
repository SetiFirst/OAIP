import time
import random

def linear_search(arr, target):
    for i in range(len(arr)):
        if arr[i] == target:
            return i
    return -1

def binary_search(arr, target):
    left, right = 0, len(arr) - 1
    while left <= right:
        mid = (left + right) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    return -1

def interpolation_search(arr, target):
    low, high = 0, len(arr) - 1
    while low <= high and target >= arr[low] and target <= arr[high]:
        if low == high:
            if arr[low] == target:
                return low
            return -1
        pos = low + ((target - arr[low]) * (high - low)) // (arr[high] - arr[low])
        if arr[pos] == target:
            return pos
        if arr[pos] < target:
            low = pos + 1
        else:
            high = pos - 1
    return -1


def bubble_sort(arr):
    n = len(arr)
    for i in range(n):
        for j in range(0, n-i-1):
            if arr[j] > arr[j+1]:
                arr[j], arr[j+1] = arr[j+1], arr[j]

def insertion_sort(arr):
    for i in range(1, len(arr)):
        key = arr[i]
        j = i - 1
        while j >= 0 and key < arr[j]:
            arr[j + 1] = arr[j]
            j -= 1
        arr[j + 1] = key

def quick_sort(arr):
    if len(arr) <= 1:
        return arr
    pivot = arr[len(arr) // 2]
    left = [x for x in arr if x < pivot]
    middle = [x for x in arr if x == pivot]
    right = [x for x in arr if x > pivot]
    return quick_sort(left) + middle + quick_sort(right)

def merge_sort(arr):
    if len(arr) > 1:
        mid = len(arr) // 2
        left_half = arr[:mid]
        right_half = arr[mid:]

        merge_sort(left_half)
        merge_sort(right_half)

        i = j = k = 0

        while i < len(left_half) and j < len(right_half):
            if left_half[i] < right_half[j]:
                arr[k] = left_half[i]
                i += 1
            else:
                arr[k] = right_half[j]
                j += 1
            k += 1

        while i < len(left_half):
            arr[k] = left_half[i]
            i += 1
            k += 1

        while j < len(right_half):
            arr[k] = right_half[j]
            j += 1
            k += 1


# Функции для тестирования
def test_search(search_func, arr, target):
    start_time = time.time()
    search_func(arr, target)
    end_time = time.time()
    return end_time - start_time

def test_sort(sort_func, arr):
    start_time = time.time()
    sort_func(arr)
    end_time = time.time()
    return end_time - start_time

# Генерация данных
small_array = [random.randint(0, 100) for _ in range(10)]
medium_array = [random.randint(0, 1000) for _ in range(100)]
large_array = [random.randint(0, 10000) for _ in range(1000)]

# Тестирование поиска
search_algorithms = [linear_search, binary_search, interpolation_search]
search_times = {alg.__name__: [] for alg in search_algorithms}

for alg in search_algorithms:
    search_times[alg.__name__].append(test_search(alg, small_array, small_array[0]))
    search_times[alg.__name__].append(test_search(alg, medium_array, medium_array[0]))
    search_times[alg.__name__].append(test_search(alg, large_array, large_array[0]))

# Тестирование сортировки
sort_algorithms = [bubble_sort, insertion_sort, quick_sort, merge_sort]
sort_times = {alg.__name__: [] for alg in sort_algorithms}

for alg in sort_algorithms:
    sort_times[alg.__name__].append(test_sort(alg, small_array.copy()))
    sort_times[alg.__name__].append(test_sort(alg, medium_array.copy()))
    sort_times[alg.__name__].append(test_sort(alg, large_array.copy()))

# Вывод результатов в консоль
print("Результаты тестирования поиска:")
for alg, times in search_times.items():
    print(f"{alg}:")
    print(f"  Маленький массив: {times[0]:.6f} секунд")
    print(f"  Средний массив: {times[1]:.6f} секунд")
    print(f"  Большой массив: {times[2]:.6f} секунд")

print("\nРезультаты тестирования сортировки:")
for alg, times in sort_times.items():
    print(f"{alg}:")
    print(f"  Маленький массив: {times[0]:.6f} секунд")
    print(f"  Средний массив: {times[1]:.6f} секунд")
    print(f"  Большой массив: {times[2]:.6f} секунд")
