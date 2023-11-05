# 필요한 라이브러리 임포트
import pandas as pd
import numpy as np
from matplotlib import pyplot as plt
import seaborn

# 데이터 불러오기
data = pd.read_csv('data/president_heights.csv')

# 데이터 일부 출력
print(data.head())

# heights 배열 생성
heights = np.array(data['height(cm)'])

# 기술통계 계산
mean_height = np.mean(heights)
std_dev_height = np.std(heights)
min_height = np.min(heights)
max_height = np.max(heights)
percentile_25th = np.percentile(heights, 25)
median_height = np.median(heights)
percentile_75th = np.percentile(heights, 75)

print(f"Mean height = {mean_height}")
print(f"Standard deviation = {std_dev_height}")
print(f"Minimum height = {min_height}")
print(f"Maximum height = {max_height}")
print(f"25th percentile = {percentile_25th}")
print(f"Median = {median_height}")
print(f"75th percentile = {percentile_75th}")

# 가장 크고 작은 대통령의 인덱스 찾기
max_idx = np.argmax(heights)
min_idx = np.argmin(heights)

max_name = data.iloc[max_idx]['name']
min_name = data.iloc[min_idx]['name']

print("The tallest president is", max_name)
print("The smallest president is", min_name)

# 시각화
%matplotlib inline
%config InlineBackend.figure_format = 'svg'
seaborn.set()

plt.hist(heights, bins=10, edgecolor='black')
plt.title('Height Distribution of US President')
plt.xlabel('Height (cm)')
plt.ylabel('Number of Presidents')
plt.show()
