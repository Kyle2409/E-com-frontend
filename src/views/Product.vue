<template>
<addProductModal/>
<div class=" mt-100">
    <div class="row">
        <div class="col-md-8 col-sm-12"  v-for="product in products" :key="product.id" >
            <div class="card mb-30" v-if="products">
                    <div class="inner">
                        <div class="main-img">
                            <img :src="product.img" class="card-img img-fluid" width="96" height="350" alt="">
                            </div>
                    </div>
                <div class="card-body text-center">
                    <h4 class="card-title">{{product.title}}</h4>
                    <h6 class="card-title">{{product.description}}</h6>
                    <h3 class="text">R{{product.price}}</h3>
                    <a class="btn btn-outline-primary btn-sm">Add To Cart</a>
                    <button class="btn btn-primary">update</button>
                    <button class="btn btn-danger" @click="deleteProduct(product.id)" >delete</button>
                </div>

            </div>
        </div>
            </div>
        </div>
</template>

<script>
import addProductModal from "@/components/addProductModal.vue";
import editProductModal from "@/components/editProductModal.vue";
export default {
    name: "Products",
  components: {
    addProductModal,
    editProductModal,
  },
 data() {
     return{
        products: null
     } 
 },
mounted() {
    fetch('https://eds-backend.herokuapp.com/products')
    .then(res => res.json())
    .then(json=>{
        console.log(json);
        this.products =json;
    })
    .catch (err => console.log(err));
},
}
</script>

<style>
.mt-100 {
    margin-top: 100px
}

.card {
    border-radius: 7px !important;
    border-color: #e1e7ec
}

.mb-30 {
    margin-bottom: 30px !important
}

.card-img-tiles {
    display: block;
    border-bottom: 1px solid #e1e7ec
}

a {
    color: #0da9ef;
    text-decoration: none !important
}

.card-img-tiles>.inner {
    display: table;
    width: 100%
}

.card-img-tiles .main-img,
.card-img-tiles .thumblist {
    display: table-cell;
    width: 65%;
    padding: 15px;
    vertical-align: middle
}

.card-img-tiles .main-img>img:last-child,
.card-img-tiles .thumblist>img:last-child {
    margin-bottom: 0
}

.card-img-tiles .main-img>img,
.card-img-tiles .thumblist>img {
    display: block;
    width: 100%;
    margin-bottom: 6px
}

.thumblist {
    width: 35%;
    border-left: 1px solid #e1e7ec !important;
    display: table-cell;
    width: 65%;
    padding: 15px;
    vertical-align: middle
}

.card-img-tiles .thumblist>img {
    display: block;
    width: 100%;
    margin-bottom: 6px
}

.btn-group-sm>.btn,
.btn-sm {
    padding: .45rem .5rem !important;
    font-size: .875rem;
    line-height: 1.5;
    border-radius: .2rem
}
</style>