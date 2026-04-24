<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>排球数据记录</title>
<style>
*{box-sizing:border-box;-webkit-tap-highlight-color:transparent;}
body{
  font-family:-apple-system,BlinkMacSystemFont,"Segoe UI",sans-serif;
  background:#f5f7fa;
  margin:0;
  padding:12px;
}
.container{
  max-width:600px;
  margin:0 auto;
}
h1{
  text-align:center;
  font-size:22px;
  margin-bottom:12px;
}
.card{
  background:#fff;
  border-radius:12px;
  padding:16px;
  margin-bottom:12px;
  box-shadow:0 2px 6px #0002;
}
.row{
  display:flex;
  align-items:center;
  justify-content:space-between;
  margin:8px 0;
}
.label{
  font-size:16px;
  width:80px;
}
.btn{
  width:44px;
  height:44px;
  border:none;
  border-radius:8px;
  font-size:22px;
  background:#eef2ff;
  color:#2563eb;
}
.btn:active{
  background:#dbe4ff;
}
.count{
  font-size:20px;
  width:40px;
  text-align:center;
}
.reset{
  width:100%;
  background:#fee2e2;
  color:#dc2626;
  margin-top:8px;
}
</style>
</head>
<body>
<div class="container">
  <h1>🏐 排球对局记录</h1>

  <div class="card">
    <div class="row">
      <div class="label">发球</div>
      <button class="btn minus" data-key="serve">-</button>
      <div class="count" id="serve">0</div>
      <button class="btn plus" data-key="serve">+</button>
    </div>
    <div class="row">
      <div class="label">进攻</div>
      <button class="btn minus" data-key="attack">-</button>
      <div class="count" id="attack">0</div>
      <button class="btn plus" data-key="attack">+</button>
    </div>
    <div class="row">
      <div class="label">一传</div>
      <button class="btn minus" data-key="pass">-</button>
      <div class="count" id="pass">0</div>
      <button class="btn plus" data-key="pass">+</button>
    </div>
    <div class="row">
      <div class="label">拦网</div>
      <button class="btn minus" data-key="block">-</button>
      <div class="count" id="block">0</div>
      <button class="btn plus" data-key="block">+</button>
    </div>
    <button class="btn reset" id="resetAll">重置本局</button>
  </div>
</div>

<script>
const state={serve:0,attack:0,pass:0,block:0};
const $=s=>document.querySelector(s);

// 加/减
document.querySelectorAll('.plus').forEach(b=>{
  b.addEventListener('click',()=>{
    const k=b.dataset.key;
    state[k]++;
    $(`#${k}`).textContent=state[k];
  });
});
document.querySelectorAll('.minus').forEach(b=>{
  b.addEventListener('click',()=>{
    const k=b.dataset.key;
    if(state[k]>0) state[k]--;
    $(`#${k}`).textContent=state[k];
  });
});

// 重置
$('#resetAll').addEventListener('click',()=>{
  for(let k in state) state[k]=0;
  $('#serve').textContent=0;
  $('#attack').textContent=0;
  $('#pass').textContent=0;
  $('#block').textContent=0;
});
</script>
</body>
</html># 111
