<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover" />
<title>约会申请</title>
<style>
  :root{
    --pink:#ff7f98;
    --pink-dark:#ff5f7d;
    --pink-light:#fff0f3;
    --green:#7ec8a4;
    --green-dark:#54b789;
    --green-light:#edf9f3;
    --cream:#fffaf3;
    --text:#4a3a3a;
    --muted:#9a7f7f;
    --card:#ffffff;
    --shadow:0 14px 34px rgba(255, 127, 152, .16);
  }
  *{box-sizing:border-box;-webkit-tap-highlight-color:transparent;}
  body{
    margin:0;
    font-family:-apple-system,BlinkMacSystemFont,"PingFang SC","Microsoft YaHei",Arial,sans-serif;
    color:var(--text);
    background:
      radial-gradient(circle at 12% 6%, rgba(255,127,152,.16) 0 130px, transparent 131px),
      radial-gradient(circle at 90% 20%, rgba(126,200,164,.18) 0 110px, transparent 111px),
      linear-gradient(180deg,#fff8fa 0%,#fffaf3 46%,#f7fff9 100%);
    min-height:100vh;
    padding:18px 14px 34px;
  }
  .phone{
    width:100%;
    max-width:430px;
    margin:0 auto;
  }
  .topbar{
    display:flex;
    align-items:center;
    justify-content:space-between;
    margin:4px 4px 14px;
    color:#7b6262;
    font-size:13px;
  }
  .capsule{
    width:74px;height:28px;border-radius:99px;background:rgba(255,255,255,.72);
    box-shadow:inset 0 0 0 1px rgba(255,127,152,.13);
    display:flex;align-items:center;justify-content:center;gap:5px;
  }
  .dot{width:6px;height:6px;border-radius:50%;background:var(--pink);display:block;}
  .hero{
    position:relative;
    overflow:hidden;
    background:linear-gradient(135deg,#ffeaf0 0%,#fff9fb 48%,#effaf4 100%);
    border-radius:28px;
    padding:24px 20px 22px;
    box-shadow:var(--shadow);
    border:1px solid rgba(255,255,255,.8);
  }
  .hero:before{content:"";position:absolute;right:-36px;top:-30px;width:126px;height:126px;border-radius:50%;background:rgba(255,127,152,.16);}
  .hero:after{content:"♡";position:absolute;right:26px;top:28px;font-size:48px;color:rgba(255,95,125,.38);transform:rotate(12deg);}
  .tag{display:inline-flex;align-items:center;gap:6px;background:#fff;border-radius:999px;padding:7px 12px;color:var(--pink-dark);font-size:13px;font-weight:600;box-shadow:0 8px 20px rgba(255,127,152,.13);}
  h1{margin:14px 0 6px;font-size:34px;letter-spacing:.03em;color:#443333;line-height:1.05;}
  .sub{font-size:14px;color:#8f7373;margin:0;}
  .mascot{position:absolute;right:18px;bottom:18px;width:76px;height:76px;border-radius:50%;background:#fff;box-shadow:0 10px 22px rgba(255,127,152,.17);display:flex;align-items:center;justify-content:center;font-size:42px;}
  form{margin-top:16px;display:flex;flex-direction:column;gap:12px;}
  .card{
    background:rgba(255,255,255,.88);
    border:1px solid rgba(255,127,152,.12);
    border-radius:22px;
    padding:16px;
    box-shadow:0 8px 22px rgba(111,82,82,.06);
    backdrop-filter:blur(12px);
  }
  .label{display:flex;align-items:center;gap:8px;font-weight:700;font-size:15px;margin-bottom:10px;}
  .no{width:24px;height:24px;border-radius:50%;background:var(--pink-light);color:var(--pink-dark);display:inline-flex;align-items:center;justify-content:center;font-size:12px;font-weight:800;}
  .no.green{background:var(--green-light);color:var(--green-dark);}
  input,textarea{
    width:100%;border:0;outline:0;background:#fff8fa;border-radius:16px;padding:13px 14px;font-size:15px;color:var(--text);
    box-shadow:inset 0 0 0 1px rgba(255,127,152,.14);
  }
  input:focus,textarea:focus{box-shadow:inset 0 0 0 2px rgba(255,127,152,.45),0 0 0 4px rgba(255,127,152,.08);}
  textarea{min-height:104px;resize:none;line-height:1.6;}
  .chips{display:flex;flex-wrap:wrap;gap:9px;}
  .chip{
    border:0;background:#fff8fa;color:#6c5353;border-radius:999px;padding:10px 13px;font-size:14px;line-height:1;
    box-shadow:inset 0 0 0 1px rgba(255,127,152,.15);cursor:pointer;transition:.18s ease;user-select:none;
  }
  .chip.active{background:linear-gradient(135deg,var(--pink),var(--pink-dark));color:white;box-shadow:0 8px 16px rgba(255,95,125,.25);transform:translateY(-1px);}
  .chip.green.active{background:linear-gradient(135deg,var(--green),var(--green-dark));box-shadow:0 8px 16px rgba(84,183,137,.22);}
  .promise{display:flex;gap:10px;align-items:flex-start;background:var(--green-light);border-radius:16px;padding:13px 14px;color:#4b7860;font-size:14px;line-height:1.55;}
  .check{width:20px;height:20px;flex:0 0 auto;border-radius:50%;background:var(--green);color:#fff;display:flex;align-items:center;justify-content:center;font-size:13px;font-weight:800;}
  .btns{display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-top:4px;}
  button{border:0;border-radius:18px;padding:15px 10px;font-size:16px;font-weight:800;color:#fff;cursor:pointer;transition:.16s ease;box-shadow:0 12px 22px rgba(255,95,125,.25);}
  button:active{transform:scale(.97);}
  .submit{background:linear-gradient(135deg,var(--pink),var(--pink-dark));}
  .reset{background:linear-gradient(135deg,var(--green),var(--green-dark));box-shadow:0 12px 22px rgba(84,183,137,.22);}
  .approval{margin-top:12px;background:linear-gradient(135deg,#fff,#fff3f6);border-radius:22px;padding:16px;border:1px dashed rgba(255,127,152,.35);}
  .approval-title{font-weight:800;color:var(--pink-dark);margin-bottom:12px;display:flex;align-items:center;gap:8px;}
  .approval-grid{display:grid;grid-template-columns:1fr;gap:10px;}
  .mini-field{background:#fff;border-radius:15px;padding:12px 13px;font-size:14px;color:#826767;box-shadow:inset 0 0 0 1px rgba(255,127,152,.12);}
  .footer{text-align:center;color:#aa8c8c;font-size:12px;line-height:1.7;margin:16px 10px 0;}
  .toast-mask{position:fixed;inset:0;background:rgba(75,55,55,.28);display:none;align-items:center;justify-content:center;padding:24px;z-index:20;}
  .toast-mask.show{display:flex;animation:fade .18s ease both;}
  .modal{width:100%;max-width:340px;background:#fff;border-radius:28px;padding:28px 22px;text-align:center;box-shadow:0 18px 50px rgba(74,58,58,.22);animation:pop .28s cubic-bezier(.2,1.4,.45,1) both;}
  .modal-icon{width:72px;height:72px;border-radius:50%;background:linear-gradient(135deg,#ffe7ed,#ecfff4);display:flex;align-items:center;justify-content:center;margin:0 auto 14px;font-size:38px;}
  .modal h3{margin:0 0 8px;font-size:22px;color:#443333;}
  .modal p{margin:0 0 18px;color:#8b6f6f;font-size:14px;line-height:1.7;}
  .modal button{width:100%;box-shadow:none;}
  .summary{margin-top:12px;text-align:left;background:#fff8fa;border-radius:16px;padding:12px;color:#765f5f;font-size:13px;line-height:1.65;max-height:180px;overflow:auto;}
  .error{animation:shake .25s ease both;box-shadow:inset 0 0 0 2px rgba(255,95,125,.7)!important;}
  @keyframes fade{from{opacity:0}to{opacity:1}}
  @keyframes pop{from{opacity:0;transform:scale(.86) translateY(16px)}to{opacity:1;transform:scale(1) translateY(0)}}
  @keyframes shake{0%,100%{transform:translateX(0)}25%{transform:translateX(-5px)}75%{transform:translateX(5px)}}
</style>
</head>
<body>
  <main class="phone">
    <div class="topbar">
      <span>💌 约会审批小程序</span>
      <div class="capsule"><span class="dot"></span><span class="dot" style="background:#7ec8a4"></span></div>
    </div>

    <section class="hero">
      <span class="tag">女朋友审批专用 · 高通过率版</span>
      <h1>约会申请</h1>
      <p class="sub">请认真填写，越用心越容易批准通过～</p>
      <div class="mascot">🐰</div>
    </section>

    <form id="dateForm" novalidate>
      <section class="card">
        <div class="label"><span class="no">1</span>申请人昵称</div>
        <input id="nickname" name="nickname" type="text" placeholder="请输入你的昵称" required />
      </section>

      <section class="card">
        <div class="label"><span class="no green">2</span>约会类型</div>
        <div class="chips multi" data-name="type">
          <span class="chip">🍽️ 吃饭</span><span class="chip">🎬 看电影</span><span class="chip">🚶 散步</span>
          <span class="chip">🧋 奶茶</span><span class="chip">🛍️ 逛街</span><span class="chip">✨ 其他</span>
        </div>
      </section>

      <section class="card">
        <div class="label"><span class="no">3</span>申请时间</div>
        <input id="time" name="time" type="datetime-local" required />
      </section>

      <section class="card">
        <div class="label"><span class="no green">4</span>约会地点</div>
        <input id="location" name="location" type="text" placeholder="请输入约会地点" required />
      </section>

      <section class="card">
        <div class="label"><span class="no">5</span>预计时长</div>
        <input id="duration" name="duration" type="text" placeholder="例如：2小时 / 一下午 / 直到你开心" />
      </section>

      <section class="card">
        <div class="label"><span class="no green">6</span>申请理由</div>
        <textarea id="reason" name="reason" maxlength="200" placeholder="认真写下你想和我约会的理由吧～\n比如：想见你、想陪你、想带你去吃好吃的。"></textarea>
      </section>

      <section class="card">
        <div class="label"><span class="no">7</span>加分项</div>
        <div class="chips multi" data-name="bonus">
          <span class="chip green">🗺️ 主动做攻略</span><span class="chip green">📷 负责拍照</span><span class="chip green">🚗 负责接送</span>
          <span class="chip green">🧋 请喝奶茶</span><span class="chip green">💗 情绪价值拉满</span><span class="chip green">👏 全程夸我</span>
        </div>
      </section>

      <section class="card">
        <div class="label"><span class="no green">8</span>费用承担</div>
        <div class="chips single" data-name="cost">
          <span class="chip">你请客</span><span class="chip">我请客</span><span class="chip green">都行，先约到再说</span>
        </div>
      </section>

      <section class="card">
        <div class="label"><span class="no">9</span>准时承诺</div>
        <div class="promise"><span class="check">✓</span><span>本人保证不迟到、不失联、不敷衍，并且全程认真营业。</span></div>
      </section>

      <div class="btns">
        <button class="submit" type="submit">提交审批</button>
        <button class="reset" type="button" id="resetBtn">打回重填</button>
      </div>
    </form>

    <section class="approval">
      <div class="approval-title">💘 审批区域</div>
      <div class="approval-grid">
        <div class="mini-field">审批结果：批准通过 / 打回重填</div>
        <div class="mini-field">女朋友签字：________________</div>
        <div class="mini-field">审批日期：____年__月__日</div>
      </div>
    </section>

    <p class="footer">温馨提示：本申请表最终解释权归女朋友所有。<br>通过率UP秘诀：真诚 + 细节 + 用心 💗</p>
  </main>

  <div class="toast-mask" id="modal">
    <div class="modal">
      <div class="modal-icon">💌</div>
      <h3>申请已提交！</h3>
      <p>约会申请已发送给女朋友审批，请耐心等待最终结果～</p>
      <div class="summary" id="summary"></div>
      <button class="submit" type="button" id="closeModal">知道啦</button>
    </div>
  </div>

<script>
  const $ = (s, r=document) => r.querySelector(s);
  const $$ = (s, r=document) => [...r.querySelectorAll(s)];

  $$('.chips.multi .chip').forEach(chip => {
    chip.addEventListener('click', () => chip.classList.toggle('active'));
  });

  $$('.chips.single').forEach(group => {
    $$('.chip', group).forEach(chip => {
      chip.addEventListener('click', () => {
        $$('.chip', group).forEach(c => c.classList.remove('active'));
        chip.classList.add('active');
      });
    });
  });

  function selectedText(selector){
    return $$(selector + ' .chip.active').map(c => c.textContent.trim()).join('、') || '暂未选择';
  }

  function markError(el){
    el.classList.add('error');
    el.scrollIntoView({behavior:'smooth', block:'center'});
    setTimeout(()=>el.classList.remove('error'),650);
  }

  $('#dateForm').addEventListener('submit', e => {
    e.preventDefault();
    const nickname = $('#nickname');
    const time = $('#time');
    const location = $('#location');

    if(!nickname.value.trim()){ alert('请先填写申请人昵称哦～'); markError(nickname); return; }
    if(!time.value){ alert('请先选择申请时间哦～'); markError(time); return; }
    if(!location.value.trim()){ alert('请先填写约会地点哦～'); markError(location); return; }

    const data = {
      申请人昵称: nickname.value.trim(),
      约会类型: selectedText('[data-name="type"]'),
      申请时间: time.value.replace('T',' '),
      约会地点: location.value.trim(),
      预计时长: $('#duration').value.trim() || '暂未填写',
      申请理由: $('#reason').value.trim() || '暂未填写',
      加分项: selectedText('[data-name="bonus"]'),
      费用承担: selectedText('[data-name="cost"]')
    };

    $('#summary').innerHTML = Object.entries(data).map(([k,v])=>`<div><b>${k}：</b>${v}</div>`).join('');
    $('#modal').classList.add('show');
  });

  $('#closeModal').addEventListener('click', () => $('#modal').classList.remove('show'));
  $('#modal').addEventListener('click', e => { if(e.target.id === 'modal') $('#modal').classList.remove('show'); });

  $('#resetBtn').addEventListener('click', () => {
    if(confirm('确定要打回重填吗？')){
      $('#dateForm').reset();
      $$('.chip.active').forEach(c => c.classList.remove('active'));
      window.scrollTo({top:0, behavior:'smooth'});
    }
  });
</script>
</body>
</html>
