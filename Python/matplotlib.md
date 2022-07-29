# Python, MatPlotlib과 Seaborn을 이용한 데이터 시각화


### Line Marker
`plt.plot`의 makrer 인수를 사용하여 각 라인의 데이터 포인트에 대한 마커를 표시할 수 있다. Matplotlib은 원, 십자형, 사각형, 다이아몬드 등과 같은 다양한 마커를 제공한다.
```python
plt.plot(years, apples, marker='o') # 동그라미 마커
plt.plot(years, oranges, marker='x') # x 마커

plt.xlabel('Year')
plt.ylabel('Yield (tons per hectare)')

plt.title("Crop Yields in Kanto")
plt.legend(['Apples', 'Oranges']);
```
기본적인 o, x 마커 외에도 다양한 마커를 지원한다.  [Marker Information](https://matplotlib.org/3.1.1/api/markers_api.html)

### Styling Lines and Markers
`plt.plot` 함수는 라인 및 마커 스타일을 지정하기 위한 인자를 지원한다.
* color 또는 c : 색깔이나 선
* linestyle 또는 ls : 점선이나 실선인지 등 선의 스타일
* linewidth 또는 lw : 선의 두께 결정
* markersize 또는 ms : 마커 크기 결정
* markeredgecolor 또는 mec : ㅇ마커 테두리 색 정하기
* markeredgecolor 또는 mew : 마커 테두리 선 두께 정하기
* markerfacecolor 또는 mfc : 마커 색 채우기
* alpha : plot의 투명도 조절
``` python
plt.plot(years, apples, marker='s', c='b', ls='-', lw=2, ms=8, mew=2, mec='navy')
plt.plot(years, oranges, marker='o', c='r', ls='--', lw=3, ms=10, alpha=.5)

plt.xlabel('Year')
plt.ylabel('Yield (tons per hectare)')

plt.title("Crop Yields in Kanto")
plt.legend(['Apples', 'Oranges']);
```
plot을 스타일에 대한 자세한 내용은 해당 Document에서 확인할 수 있다. [matplotlib document](https://matplotlib.org/3.1.1/api/markers_api.html)

`fmt`인자는 마커의 모양, 선 스타일 및 선 색상을 지정하는 약어를 제공한다. plt.plot의 세 번째 인자로 전달하여 사용한다.
> fmt = [marker][line][color]

만약 `fmt`에 선 스타일을 지정하지 않을 경우 마커만 그려지게 된다.
### Changing the Figure Size (그림 크기 변경)
`plt.figure` 함수를 사용하여 Figure의 크기를 변경할 수 있다.
``` python
plt.figure(figsize=(12, 6)) # 가로 12, 세로 6
```
### Seaborn을 이용한 Style 개선
Seaborn 라이브러리에서 기본으로 제공되는 스타일을 사용하면 보기 좋은 그래프를 구성할 수 있다. 
`sns.set_style` 함수를 사용하여 스타일을 전역변수로 사용할 수 있다.
``` python
sns.set_style("whitegird")
```
```matplotlib.rcParams``` Dictionary를 수정하여 기본 스타일을 직접 편집할 수 있다.
``` python
matplotlib.rcParams['font.size'] = 14
matplotlib.rcParams['figure.figsize'] = (9, 5)
matplotlib.rcParams['figure.facecolor'] = '#00000000'
```
### Scatter Plot(산점도)
산점도에서, 2개의 변수값은 2차원 좌표에 점으로 표시된다. 또한, 세 번째 변수를 사용하여 포인트의 크기나 색상을 결정할 수 있다.

[Iris flower dataset](https://en.wikipedia.org/wiki/Iris_flower_data_set): 세 종의 꽃에 대한 꽃받침과 꽃잎의 샘플 측정을 제공한다.
Iris 데이터셋은 Seaborn 라이브러리에 포함되어 있으며 Pandas 데이터 프레임으로 로드 할 수 있다.
``` python
flowers_df = sns.load_dataset("iris")
```

## 히스토그램
히스토그램은 값 범위에 따라 간격을 만들고 각 간격의 관측치 수를 나타내는 수직 막대를 표시하여 변수의 분포를 나타낸다.

#### bin 크기 제어 및 개수 제어
bin 인자를 사용하여 그래프 수와 크기를 조절할 수 있다.
![plotimage](/image/output.png)
