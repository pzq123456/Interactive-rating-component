<template>
    <div class="card-wrapper">
        <div class="card-content" v-if="!isSubmmited">
            <div class="star">
                <img src="../assets/images/icon-star.svg" >
            </div>
            <h1>How did we do?</h1>
            <p>
                Please let us know how we did with your support request. All feedback is appreciated to help us improve our offering!
            </p>
            <div class="ratings-wrapper">
                <div v-for="( rating , index ) in ratingNumList" 
                class="rating" 
                @click="selected(index)"
                :class="{'selected-rating' : rating.selected}">

                    <span>{{ rating.rating }}</span>

                </div>
            </div>
            <button 
            @click="submit"
            >Submit</button>
        </div>

        <div class="card-content thank-you" v-else>

            <img src="../assets/images/illustration-thank-you.svg">
            <div class="selection">
                <span>
                    You selected {{ selectedrating.rating }} out of 5
                </span>
            </div>

                <h1>Thank you!</h1>
                <p>
                    We appreciate you taking the time to give a rating. If you ever need more support, don’t hesitate to get in touch!
                </p>
            </div>
        
    </div>
</template>

<script setup>
import {ref} from 'vue';

const ratingNumList = ref([
    {rating:1,selected:false},
    {rating:2,selected:false},
    {rating:3,selected:false},
    {rating:4,selected:false},
    {rating:5,selected:false},
]);

const selectedrating = ref(null);
const isSubmmited = ref(false);

function selected(index){
    // console.log(ratingNumList.value[index]);
    //ratingNumList.value[index].selected = !ratingNumList.value[index].selected;
    ratingNumList.value.forEach((rating) => (rating.selected = false)); 
        ratingNumList.value[index].selected = true;
        selectedrating.value = ratingNumList.value[index];
}

function submit(){
    if(selectedrating.value){
        isSubmmited.value = true;
    }
}
</script>

<style scoped>
.card-wrapper {
    display: grid;
    place-items: center;
    height: 100vh;
    background-color: var(--very-dark-blue);
    padding: 0 1rem;
}

.card-content {
    /* background-color: var(--dark-blue); */
    /* linear gradient color 
    from var(--dark-blue) to var(--very-dark-blue)
    */
    background: linear-gradient(180deg, var(--dark-blue) 0%, var(--very-dark-blue-2) 100%);
    color: var(--white);
    max-width: 380px;
    width: 100%;
    padding: 2rem;
    border-radius: 10px;
}

.star {
    display: grid;
    place-items: center;
    width: 40px;
    height: 40px;
    border-radius: 50%;
    background-color: var(--medium-grey-2);
    margin-bottom: 1rem;
}

h1 {
    font-size: 1.5rem;
    font-weight: 700;
    margin-bottom: 1rem;
}

p{
    font-size: 0.875rem;
    font-weight: 400;
    margin-bottom: 1rem;
    color: var(--light-grey);
    line-height: 1.8;
}

.ratings-wrapper {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    margin-bottom: 1rem;
    gap: 1rem;
}

.rating {
    display: grid;
    place-items: center;
    width: 50px;
    height: 50px;
    border-radius: 50%;
    background-color: var(--medium-grey-2);
    margin-bottom: 1rem;
    font-size: 1.5rem;
    font-weight: 400;
    color: var(--light-grey);
}

button {
    background-color: var(--orange);
    color: var(--white);
    border: none;
    border-radius: 20px;
    padding: 0.5rem 1rem;
    font-size: 1rem;
    font-weight: 700;
    cursor: pointer;
    width: 100%;
    transition: all 0.3s ease-in-out;
}

button:hover {
    background-color: var(--white);
    color: var(--orange);
}

.rating:hover {
    background-color: var(--orange);
    color: var(--white);
    transition: all 0.3s ease-in-out;
}

.selected-rating{
    background-color: var(--medium-grey);
    color: var(--white);
}

.selection {
    display: grid;
    place-items: center;
    margin-bottom: 1rem;
    background-color: var(--medium-grey-2);
    padding: 0.5rem 1rem;
    border-radius: 20px;
    font-size: 0.875rem;
    font-weight: 400;
    color: var(--orange);
    margin-top: 1rem;
}

.thank-you {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;
}
</style>