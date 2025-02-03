<script>
  let a = $state(0);

  const func1 = () => {
    let d = a * a;
    if (d <= 4) {
      func2(a, d);
    } else {
      func3(a, d);
    }
  };

  // compiles to "func2(get(a), d);"
  const func2 = (a, d) => {
    if ((typeof a === "number") & (typeof d === "number")) {
      console.log("func2", d);
    }
  };

  // compiles to "func3(get(), d);"
  const func3 = (a, d) => {
    console.log("func3", d);
  };
</script>

<p>
  a: {a}
</p>
<p>To replicate, press "Increment a", then press "a^2"</p>
<p>When "a" is less than 2 it works correctly</p>
<p>
  When "a" is more than 2 it throws "Uncaught TypeError: Cannot read properties
  of undefined (reading 'f')" in console
</p>
<p>This only shows on builds, not on local dev</p>
<button
  onclick={() => {
    a++;
    console.log("increment a", a);
  }}>Increment a</button
>
<button onclick={() => func1()}>a^2</button>
