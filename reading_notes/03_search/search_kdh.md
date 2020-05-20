## Ž�� �˰���

### ���� Ž��

> ���������� Ž���Ͽ� ����Ʈ�� �� ���Ҹ� Ȯ��

#### �ð� ���⵵

- Worst case : O(n)
- Best case : O(1)
- Average case : O(n)
  - n(n + 1) / 2

### ���� Ž��

> ���ĵ� ����Ʈ���� ����Ʈ�� �߰� ���� ���س����� Ž��

- ���� / ������������ ���ĵ� ���¿����� ����

#### �ð� ���⵵

- Worst case : O(log n)
- Best case : O(1)
- Average case : O(log n)

#### ���̺귯��

- C++������ std::binary_search�� ���� ��밡��

## ���� �˰���

���� Ž�� ������ �ذ��ϴ� �� std::sort�� �̿����� �ʰ� �� ��Ʈ�� �̿��ؼ� �����غô�.

### Quick sort

> ��� O(nlogn)�� �ð����⵵�� ������, �ٸ� O(nlogn)�ð� ���⵵�� ���� �˰��� ���ؼ��� ���� ������.

#### ����

- Unsatble sort�� �ش��Ѵ�.
- divde and conquer ����̴�. - ������ ���� ������ �и��Ͽ� ���� �ذ��ϴ� ����̴�.

#### ����

1. ����Ʈ�� �� ��Ҹ� �����Ͽ� �ǹ�(pivot)�̶� �Ѵ�.
2. ������������ �����ϱ� ���� �ǹ����� ���� ��ҵ��� �ǹ��� �������� �ű��, �ǹ����� ū ��ҵ��� �ǹ��� ���������� �ű��.
3. �ǹ��� ���ĵ� �ڽ��� ��ġ�� ���������Ƿ�, �ǹ� ���� ���ʰ� �������� ����Ʈ�� �ٽ� �����Ѵ�.
4. ����Ʈ�� ������ �ȵ� ������ �ݺ��Ѵ�.

#### ���� �ڵ�

```c++
void partition(vector<int> &V, int start, int end, int &pivot) // start �� ����Ʈ�� ù ����, end�� ����Ʈ�� ������ ���� ����Ʈ�� pivot�� ���۷��� ������ �Ѱ���
{
	int temp;
	int left, right; //left�� ����Ʈ ���� ���� ���Һ��� ���������� �����ϴ� �ε���, right�� ����Ʈ ���� ������ ���Һ��� �������� �����ϴ� �ε���

	pivot = start;
	left = start;
	right = end;
	while (left < right) //left�� right�� �������� ����
	{
		while (V[left] <= V[pivot] && left < end) // left�� ����Ʈ�� �ʰ����� �����鼭, pivot���� ū ���Ұ� ���ö����� ���������� ����
			left++;
		while (V[right] >= V[pivot] && right > start) // right�� ����Ʈ�� �ʰ����� �����鼭, pivot���� ���� ���Ұ� ���ö����� �������� ����
			right--;
		if (left < right)
		{
			SWAP(V[left], V[right], temp);
		}
	}
	if (pivot != right)
	{
		SWAP(V[pivot], V[right], temp);
		pivot = right; // pivot�� ��ġ�� ������ right�� ��ġ�̹Ƿ� ����
	}
}

void quick_sort(vector<int> &V, int start, int end)
{
	int pivot;

	if (start < end)
	{
		partition(V, start, end, pivot); // pivot �������� �κ� ����Ʈ�� ����
		if (pivot != start)
			quick_sort(V, start, pivot - 1);
		if (pivot != end)
			quick_sort(V, pivot + 1, end);
	}
}
```
