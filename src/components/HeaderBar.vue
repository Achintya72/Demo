<script>
import user from '../assets/user.png'
import person from '../assets/person.svg'
export default {
    name: 'HeaderBar',
    props: ['modelValue'],
    emits: ['update:modelValue'],
    data() {
        return {
            user,
            person,
            searchField: "",
            searchType: this.modelValue,
            searchTypePopupVisible: false,
            searchTypes: [
                'Open Order',
                'Customer',
                'Acquisition',
                'Item',
                'Part Number',
                'Vendor',
                'Purchase'
            ],
            sortBy: "Best Match",
            active: false,
            myLocations: false
        }
    },
    methods: {
        toggleSearchTypePopup() {
            this.searchTypePopupVisible = !this.searchTypePopupVisible
            console.log(this.searchTypePopupVisible)
        },
        changeFilter(t) {
            this.searchType = t;
            this.searchTypePopupVisible = false;
            this.$emit('update:modelValue', t)
        }
    }

}
</script>
<template>
    <div>
        <div class='nav'>
            <div class='nav_first'>
                <div class="nav_logo">
                    <h1>MSC</h1>
                </div>
                <div class="nav_search">
                    <button @click="toggleSearchTypePopup">Options<span class="nav_option">{{ searchType[0]
                    }}</span><span class="nav_option_icon">▼</span></button>
                    <input type='text' :placeholder="`Search ${this.searchType}s`" v-model="searchField" />
                    <div id="search_type_filter" v-if="searchTypePopupVisible">
                        <span class="search_type" :id="type == searchType && 'active'" @click="changeFilter(type)"
                            v-for="type in searchTypes">{{ type
                            }}</span>
                    </div>
                </div>

            </div>
            <div class='nav_second'>
                <div class="nav_menu">
                    <stong class="pb-8">Bill To:#</stong>
                    <small class="pb-8 font-size-12">Not Selected</small>
                </div>
                <div class="nav_menu">
                    <stong class="pb-8">Ship To:#</stong>
                    <small class="pb-8 font-size-12">Not Selected</small>
                </div>
                <div class="nav_menu">
                    <stong class="pb-8">Contect:</stong>
                    <small class="pb-8 font-size-12">Not Selected</small>
                </div>
                <div class="nav_menu_thired">
                    <stong class="pb-8">Order:#</stong>
                    <small class="pb-8 font-size-12">Items:</small>
                    <div class="nav_menu_button ">
                        <button class="success">Close</button>|
                        <button class="warn">Delete</button>
                    </div>
                </div>
                <div class="nav_menu_thired">
                    <div>
                        <img src={person} alt="" />
                        <stong>GottumuS ▼</stong>
                    </div>

                    <!-- <small>▼</small> -->
                </div>

            </div>

        </div>
        <div class='nav_bottom'>
            <select id="sortBy" v-model="sortBy">
                <option>Best Match</option>
                <option>Newest Order</option>
                <option>Total</option>
            </select>
            <input type="checkbox" id="active" value="Active" v-model='active'>
            <label for="active">Active</label>
            <input type="checkbox" id="my-locations" value="My Locations" v-model='myLocations'>
            <label for="my-locations">My Locations</label>
        </div>
    </div>

</template>


<style scoped>
.nav {
    background-color: #3D3C3E;
    display: flex;
    justify-content: space-between;
    height: 105px;
    width: 100%;
    margin: 0;
}

.nav_logo>h1 {
    font-size: 75px;
    font-weight: 800;
    font-style: italic;
    color: #FE3331;
    padding-right: 20px;
    padding-left: 10px;
}

#search_type_filter {
    display: flex;
    flex-direction: column;
    background-color: white;
    font-family: 'Open-Sans', sans-serif;
    border-radius: 5px;
    width: 150px;
    padding: 5px 10px;
    box-shadow: rgba(0, 0, 0, 0.25) 5px 5px 10px;
    position: absolute;
    top: 75px;
}

.search_type {
    padding: 5px;
    font-size: 0.75rem;
}

#active {

    font-weight: 900;
}

.nav_bottom {
    height: 40px;
    font-family: 'Open Sans', sans-serif;
    color: white;
    background-image: linear-gradient(#666667, #414041, #414041);
    display: flex;
    justify-content: right;
    align-items: center;
    padding: 0 10px;
}

.nav_first {
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 35%;
}

.nav_search {
    /* width: 30px; */
    margin-top: -10px;
    display: flex;
    align-items: center;
    font-weight: 500;
    /* flex: 1; */
}

.nav_search>button {
    display: flex;
    align-items: center;
    justify-content: space-around;
    border-radius: 15px 0 0 15px;
    background-color: #F0EEF0;
    padding: 5px;
    border: none;
    height: 34px;
    width: 100px;
}

.nav_search>input {
    border-radius: 0 15px 15px 0;
    padding: 5px;
    width: 130px;
    outline: none;
    height: 23px;
}

.nav_second {
    display: flex;
    width: 65%;
}

.nav_menu {
    display: flex;
    justify-content: flex-start;
    align-items: center;
    flex-direction: column;
    flex: 1;
    padding-top: 20px;
    color: white;
    border-right: 3px solid #4D4C4E;
}

.nav_option {
    width: 20px;
    height: 20px;
    background-color: #36768A;
    color: white;
    display: flex;
    align-items: center;
    justify-content: center;
    /* font-weight: 500; */
}

.nav_option_icon {
    color: #36768A;
}

.nav_menu_thired {
    display: flex;
    justify-content: flex-start;
    align-items: center;
    flex-direction: column;
    flex: 1;
    padding-top: 20px;
    color: white;
    /* border-right: 3px solid #4D4C4E; */
}

.pb-8 {
    padding-bottom: 8px;
}

.font-size-12 {
    font-size: 12px;
}

.nav_menu_button {
    display: flex;
    min-width: 120px;
    justify-content: space-between;
    /* padding-top:10px; */
}

.nav_menu_button>button {
    padding: 5px;
    border-radius: 4px;
    border: none;
    color: #F5F5F5;
    /* margin-right:10px; */
}

.success {
    background-color: #36768A;
}

.warn {
    background-color: #913734;
}

p {
    margin: 0;
    padding: 0;
}
</style>
