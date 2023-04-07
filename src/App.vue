<script setup>
const start = () => {
    // скрываем кнопку старта
    document.querySelector('.start').style.display = 'none'

    const app = document.querySelector('#app')

    // создаем в цикле 3000 div.box и добавляем их в #app
    for (let i = 0; i < 3000; i++) {
        const box = document.createElement('div')
        box.classList.add('item')
        app.appendChild(box)
    }

    // получаем все div.box
    const boxes = document.querySelectorAll('.item')

    // в цикле навешиваем событие mouseover на каждый div.item
    for (let i = 0; i < boxes.length; i++) {
        boxes[i].addEventListener('mouseover', changeColor)
    }
}

const changeColor = (event) => {
    // генерируем случайный код цвета
    const color = '#' + Math.floor(Math.random() * 16777215).toString(16)

    // меняем цвет div.item
    event.target.style.backgroundColor = color

    // воспроизводим короткий звуковой сингнал
    const audio = new Audio('https://www.soundjay.com/buttons/button-1.mp3')
    audio.play()

    // удаляем событие mouseover
    event.target.removeEventListener('mouseover', changeColor)
}
</script>

<template>
    <button @click="start" class="start">нажми меня</button>
</template>
