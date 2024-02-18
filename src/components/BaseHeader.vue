<template>
    <!-- 템플릿 태그 바로 아래에는 하나의 태그만 존재 해야한다(Root)-->
    <header>
        <h1>TODO it!</h1>
    </header>
</template>

<script>
export default {

}
</script>

<!-- scoped : 상위 부모 클래스 다 무시되고 컴포넌트 내에서만 css가 먹는다-->
<style scoped>
h1 {
    color: #2F3B52;
    font-weight: 900;
    margin: 2.5rem 0 1.5rem;
}

</style>