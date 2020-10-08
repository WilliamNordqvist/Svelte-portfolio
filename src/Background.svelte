<script>
  const getStars = (stars) => {
    let arr = [];
    for (let i = 0; i < stars; i++) {
      arr = [
        ...arr,
        {
          left: Math.floor(Math.random() * 101) + "%",
          bottom: Math.floor(Math.random() * (101 - -50) + -50) + "%",
        },
      ];
    }
    return arr;
  };

  const bigStars = getStars(200);
  const mediumStars = getStars(100);
  const smallStars = getStars(200);

</script>

<style>
  div {
    position: relative;
    width: 100%;
    height: 100%;
    background-color: transparent;
  }

  .star-big,.star-medium,.star-small  {
    position: absolute;
    border-radius: 50%;
    background-color: white;
  }

  .star-big {
    width: 3px;
    height: 3px;
    animation: animStar 150s linear infinite;
  }
  .star-medium {
    width: 2px;
    height: 2px;
    animation: animStar 100s linear infinite;
  }
  .star-small {
    width: 1px;
    height: 1px;
    animation: animStar 130s linear infinite;
  }

  @keyframes animStar {
    from {
      transform: translateY(0px);
    }

    to {
      transform: translateY(-2000px);
    }
  }
</style>

<div>
  {#each bigStars as star, i}
    <div class="star-big" style={`left:${star.left}; bottom:${star.bottom}`} />
  {/each}
  {#each mediumStars as star, i}
    <div class="star-medium" style={`left:${star.left}; bottom:${star.bottom}`} />
  {/each}
  {#each smallStars as star, i}
    <div class="star-small" style={`left:${star.left}; bottom:${star.bottom}`} />
  {/each}
  <slot />
</div>
