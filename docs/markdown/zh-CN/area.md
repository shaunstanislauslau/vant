## Area 省市县选择组件

### 使用指南

```javascript
import { Area } from 'vant';

Vue.use(Area);
```

### 代码演示

#### 基础用法

要初始化一个`Area`组件，你需要传入一个`area-list`属性，数据格式具体可看下面数据格式章节

```html
<van-area :area-list="areaList" />
```

#### 选中省市县

如果想选中某个省市县，需要传入一个`value`属性，绑定对应的省市县`code`

```html
<van-area :area-list="areaList" value="110101" />
```

#### 配置显示列

可以通过`columns-num`属性配置省市县显示的列数，默认情况下会显示省市县，当你设置为`2`，则只会显示省市选择

```html
<van-area :area-list="areaList" :columns-num="2" title="标题" />
```

### API

| 参数 | 说明 | 类型 | 默认值 | 可选值 |
| --- | --- | --- | --- | --- |
| value | 当前选中的省市区`code` | `String` | - | - |
| title | 顶部栏标题 | `String` | `''`   | - |
| area-list | 省市县数据，格式见下方 | `Object` | - | - |
| columns-num | 省市县显示列数，3-省市县，2-省市，1-省 | `String`,`Number` | `3` | - |
| loading | 是否显示加载状态 | `Boolean` | `false` | - |
| item-height | 选项高度 | `Number` | `44` | - |
| visible-item-count | 可见的选项个数 | `Number` | `5` | - |

### Event

| 事件 | 说明 | 回调参数 |
| --- | --- | --- |
| confirm | 点击右上方完成按钮 | 一个数组参数，具体格式看下方数据格式章节 |
| cancel | 点击取消按钮时 | - |

### 数据格式

#### 省市县列表数据格式

整体是一个 Object，包含 `province_list`, `city_list`, `county_list` 三个 key。

每项以省市区编码作为 key，省市区名字作为 value。编码为 6 位数字，前两位代表省份，中间两位代表城市，后两位代表区县，以 0 补足 6 位。如北京编码为 `11`，以零补足 6 位，为 `110000`。

`AreaList`具体格式如下：

```javascript
{
  province_list: {
    110000: '北京市',
    120000: '天津市'
  },
  city_list: {
    110100: '北京市',
    110200: '县',
    120100: '天津市',
    120200: '县'
  },
  county_list: {
    110101: '东城区',
    110102: '西城区',
    110105: '朝阳区',
    110106: '丰台区'
    120101: '和平区',
    120102: '河东区',
    120103: '河西区',
    120104: '南开区',
    120105: '河北区',
    // ....
  }
}
```

完整数据见 [Area.json](https://github.com/youzan/vant/blob/dev/docs/demos/mock/area.js)

#### 点击完成时返回的数据格式

返回的数据整体为一个数组，数组内包含 `columnsNum` 个数据， 每个数据对应一列选项中被选中的数据。

`code` 代表被选中的地区编码， `name` 代表被选中的地区名称

```javascript
[
  {
    code: '110000',
    name: '北京市'
  },
  {
    code: '110100',
    name: '北京市'
  },
  {
    code: '110101',
    name: '东城区'
  }
];
```
