retrieve-id-utils
=======================

批量获取数据，多级存储结构（或者缓存）筛选。

* 每一级数据缓存都有可以配置回流
* 强类型
* 只支持jdk1.8

## Get Started

```xml
<dependency>
    <groupId>com.github.phantomthief</groupId>
    <artifactId>retrieve-id-utils</artifactId>
    <version>1.0.1</version>
</dependency>
```

## Usage

```Java

List<Integer> ids = Arrays.asList(1, 2, 3, 4, 5);
Map<Integer, String> result = RetrieveIdUtils.get(ids, Arrays.asList( //
        new IMultiDataAccess<Integer, String>() {

            @Override
            public Map<Integer, String> get(Collection<Integer> keys) {
                return ...; // 第一级缓存读取
            }

            @Override
            public void set(Map<Integer, String> dataMap) {
            	// 第一级缓存回流
            }
        }, //
        new IMultiDataAccess<Integer, String>() {

            @Override
            public Map<Integer, String> get(Collection<Integer> keys) {
                return ...; // 第二级缓存读取
            }

        }));

```