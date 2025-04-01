<template>
  <view class="container">
    <!-- 搜索框 -->
    <view class="search-box">
      <nut-input v-model="searchKeyword" placeholder="请输入商品关键词" type="text" />
    </view>

    <!-- 轮播图 -->
    <nut-swiper :autoplay="3000" :loop="true">
      <nut-swiper-item v-for="(item, index) in swiperList" :key="index">
        <image :src="item.image" mode="aspectFill" />
      </nut-swiper-item>
    </nut-swiper>

    <!-- 宫格布局-商品分类 -->
    <uni-grid :column="4">
      <uni-grid-item v-for="(category, index) in categories" :key="index">
        <image :src="category.icon" mode="aspectFit" />
        <text>{{ category.name }}</text>
      </uni-grid-item>
    </uni-grid>

    <!-- 商品列表 -->
    <view class="product-list">
      <nut-card v-for="(product, index) in productList" :key="index">
        <template #header>
          <image :src="product.image" mode="aspectFill" />
        </template>
        <template #body>
          <text class="product-name">{{ product.name }}</text>
          <text class="product-price">¥{{ product.price }}</text>
        </template>
        <template #footer>
          <nut-button type="primary" @click="handleBuy(product)">购买</nut-button>
        </template>
      </nut-card>
    </view>
  </view>
</template>

<script>
import { ref } from 'vue';

export default {
  setup() {
    const searchKeyword = ref('');
    const swiperList = ref([
      { image: 'https://via.placeholder.com/750x300' },
      { image: 'https://via.placeholder.com/750x300' },
      { image: 'https://via.placeholder.com/750x300' }
    ]);
    const categories = ref([
      { icon: 'https://via.placeholder.com/50', name: '分类1' },
      { icon: 'https://via.placeholder.com/50', name: '分类2' },
      { icon: 'https://via.placeholder.com/50', name: '分类3' },
      { icon: 'https://via.placeholder.com/50', name: '分类4' }
    ]);
    const productList = ref([
      { image: 'https://via.placeholder.com/200', name: '商品1', price: '100' },
      { image: 'https://via.placeholder.com/200', name: '商品2', price: '200' },
      { image: 'https://via.placeholder.com/200', name: '商品3', price: '300' }
    ]);

    const handleBuy = (product) => {
      console.log('购买商品:', product);
      // 跳转到购买页面
    };

    return {
      searchKeyword,
      swiperList,
      categories,
      productList,
      handleBuy
    };
  }
};
</script>

<style>
.container {
  padding: 20px;
}

.search-box {
  margin-bottom: 20px;
}

.product-list {
  margin-top: 20px;
}

.product-name {
  font-size: 16px;
  font-weight: bold;
}

.product-price {
  font-size: 14px;
  color: #f44;
}
</style>