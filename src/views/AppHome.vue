<template>
    <main class="wrapper">
        <div class="getters">
            <div class="getters--container">
                <AppGetter v-for="userCheck in userAlready" :id="userCheck.id" :name="userCheck.name" :key="userCheck.id"/>
                <div class="getters--counter">
                    <p>{{ userAlready.length }}</p>
                    <p>/</p>
                    <p>6</p>
                </div>
            </div>
            <div class="getters--container">
                <AppGetter v-for="allCheck in allAlready" :id="allCheck.id" :name="allCheck.name" :key="allCheck.id"/>
            </div>
        </div>
        <div class="setters">
            <div class="setters--container">
                <AppSetter
                        v-model="isChecked"
                        @click.native="userHandler(userItem)"
                        v-for="userItem in userSelect"
                        :id="userItem.id"
                        :name="userItem.name"
                        :key="userItem.id"
                />
            </div>
            <div class="setters--container">
                <AppSetter
                        v-model="isChecked"
                        @click.native="allHandler(allItem)"
                        v-for="allItem in allSelect"
                        :id="allItem.id"
                        :name="allItem.name"
                        :key="allItem.id"
                />
            </div>
        </div>
    </main>
</template>

<script>
    import AppGetter from "@/components/AppGetter";
    import AppSetter from "@/components/AppSetter";
    export default {
        name: "AppHome",
        components: {AppSetter, AppGetter},

        data() {
            return {
                userSelect: [
                    {
                        "id": 1,
                        "name": "Shoes 1"
                    },
                    {
                        "id": 2,
                        "name": "Shoes 2"
                    },
                    {
                        "id": 3,
                        "name": "Shoes 3"
                    },
                    {
                        "id": 4,
                        "name": "Shoes 4"
                    },
                    {
                        "id": 5,
                        "name": "T-shirt 1"
                    },
                    {
                        "id": 6,
                        "name": "T-shirt 2"
                    },
                    {
                        "id": 7,
                        "name": "T-shirt 3"
                    },
                    {
                        "id": 8,
                        "name": "T-shirt 4"
                    }
                ],
                allSelect: [
                    {
                        "id": 11,
                        "name": "Jacket 1"
                    },
                    {
                        "id": 12,
                        "name": "Jacket 2"
                    },
                    {
                        "id": 13,
                        "name": "Jacket 3"
                    },
                    {
                        "id": 14,
                        "name": "Jacket 4"
                    },
                    {
                        "id": 15,
                        "name": "Hoodie 1"
                    },
                    {
                        "id": 16,
                        "name": "Hoodie 2"
                    },
                    {
                        "id": 17,
                        "name": "Hoodie 3"
                    },
                    {
                        "id": 18,
                        "name": "Hoodie 4"
                    }
                ],
                userAlready: [],
                allAlready: [],
                isChecked: false
            }
        },

        methods: {
            userHandler(currElem) {
                for (let i = 0; i < this.userAlready.length; i++) {
                    if (this.userAlready[i].id === currElem.id) {
                        this.isChecked = true
                    }
                }

                if (this.userAlready.length < 6) {
                    if (this.isChecked) {
                        this.userAlready = this.userAlready.filter((el) => {return el.id !== currElem.id})

                        this.isChecked = false
                    }

                    else {
                        this.userAlready.push(currElem)
                    }
                }

                if (this.userAlready.length === 5) {
                    
                }
            },

            allHandler(currElem) {
                let allHandlerItems = this.allAlready

                allHandlerItems.length = 0
                allHandlerItems.push(currElem)
            }
        }
    }
</script>

<style lang="scss" scoped>
    .wrapper{
        max-width: 1440px;
        margin: 100px auto;
        display: flex;
        flex-direction: column;
        gap: 50px;
    }
    .setters{
        display: flex;
        justify-content: space-between;

        &--container{
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            border: 1px solid seagreen;
            border-radius: 10px;
            padding: 25px;
            width: 500px;
            gap: 10px;
        }
    }
    .getters{
        display: flex;
        justify-content: space-between;
        position: relative;

        &--container{
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            border: 1px solid seagreen;
            border-radius: 10px;
            padding: 25px;
            width: 500px;
            gap: 10px;
        }

        &--counter{
            display: flex;
            align-items: center;
            gap: 5px;
            position: absolute;
            bottom: 5px;
        }
    }
</style>