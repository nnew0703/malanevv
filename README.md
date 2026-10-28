<!DOCTYPE html>
<html lang="th">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>เคาน์เตอร์คิดเงิน</title>
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=IBM+Plex+Sans+Thai:wght@400;500;600;700&display=swap">
<style>
:root{color-scheme:light;--bg:#f2f9fe;--hd:#d4ebfa;--card:#ffffff;--paper:#ffffff;--ink:#0f2f47;--mute:#587890;--line:#c9e2f3;--acc:#0b7fbf;--acc-ink:#ffffff;--warn:#c0392b;--chip:#e3f2fc;
box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
html{scroll-padding-top:env(safe-area-inset-top,0px)}
*{box-sizing:border-box}
body{margin:0;background:var(--bg);color:var(--ink);font:400 16px/1.5 "IBM Plex Sans Thai","Noto Sans Thai",system-ui,sans-serif}
button,input,select{font:inherit;color:inherit}
button{cursor:pointer;border:0;border-radius:10px;background:var(--chip);padding:10px 14px;min-height:44px}
button:focus-visible,input:focus-visible,select:focus-visible{outline:3px solid var(--acc);outline-offset:2px}
.num{font-variant-numeric:tabular-nums}
header{position:sticky;top:env(safe-area-inset-top,0px);z-index:5;background:var(--hd);padding:10px 10px;display:flex;flex-wrap:wrap;gap:4px;align-items:center;border-bottom:1px solid var(--line)}
body::before{content:"";position:fixed;inset:0 0 auto;height:env(safe-area-inset-top,0px);background:var(--hd);z-index:10}
header h1{font-size:16px;margin:0 auto 0 0;font-weight:700}
.tab{background:transparent;padding:8px 9px}
.tab[aria-selected=true]{background:var(--acc);color:var(--acc-ink);font-weight:600}
main{max-width:1000px;margin:0 auto;padding:14px}
.sale{display:grid;gap:14px}
@media(min-width:820px){.sale{grid-template-columns:1fr 380px;align-items:start}.cart{position:sticky;top:76px}}
.chips{display:flex;gap:8px;overflow-x:auto;padding-bottom:8px}
.chips button{white-space:nowrap}
.chips button[aria-pressed=true],.seg button[aria-pressed=true]{background:var(--ink);color:var(--bg)}
.menu{display:grid;grid-template-columns:repeat(auto-fill,minmax(130px,1fr));gap:10px}
.item{background:var(--card);border:1px solid var(--line);text-align:left;padding:12px;min-height:84px;display:flex;flex-direction:column;justify-content:space-between;border-radius:12px;position:relative}
.item:active{transform:scale(.97)}
.item b{font-weight:600}
.item .p{color:var(--mute)}
.item .badge{position:absolute;top:8px;right:8px;background:var(--acc);color:var(--acc-ink);border-radius:99px;min-width:24px;height:24px;padding:0 7px;font-size:13px;display:grid;place-items:center}
.cart{background:var(--paper);border:1px dashed var(--mute);border-radius:6px;padding:16px}
h2{font-size:16px;margin:12px 0 8px}
.cart h2{margin-top:0}
.row{display:flex;align-items:center;gap:8px;padding:6px 0;border-bottom:1px dotted var(--line);flex-wrap:wrap}
.row .n{flex:1;min-width:0}
.row .q{display:flex;align-items:center;gap:4px}
.row .q button{min-height:34px;width:34px;padding:0}
.promo{color:var(--acc);font-weight:600}
.total{display:flex;justify-content:space-between;font-size:26px;font-weight:700;margin:12px 0 4px}
.seg{display:flex;gap:6px;flex-wrap:wrap;margin:6px 0}
.seg button{padding:6px 10px;min-height:36px}
.field{display:flex;gap:8px;align-items:center;margin:8px 0}
.field input{flex:1;min-width:0;border:1px solid var(--line);background:var(--card);border-radius:10px;padding:10px;font-size:18px;text-align:right}
.quick{display:flex;gap:6px;flex-wrap:wrap}
.quick button{padding:6px 12px;min-height:36px}
.change{display:flex;justify-content:space-between;font-weight:600;margin:6px 0}
.mute{color:var(--mute)}
.pay{width:100%;background:var(--acc);color:var(--acc-ink);font-weight:700;font-size:18px;min-height:52px;margin-top:8px}
.pay:disabled{opacity:.4;cursor:not-allowed}
.ghost{background:transparent;color:var(--mute);width:100%;margin-top:6px}
.sum{display:grid;grid-template-columns:repeat(3,1fr);gap:10px;margin-bottom:14px}
.sum div{background:var(--card);border:1px solid var(--line);border-radius:12px;padding:10px}
.sum small{color:var(--mute);display:block}
.sum strong{font-size:19px}
.order{background:var(--card);border:1px solid var(--line);border-radius:12px;margin-bottom:10px;overflow:hidden}
.order summary{list-style:none;display:flex;justify-content:space-between;gap:8px;padding:12px 14px;cursor:pointer;min-height:48px;align-items:center}
.order summary::-webkit-details-marker{display:none}
.sub{color:var(--mute);font-size:14px}
.order .body{padding:0 14px 12px}
.order .acts{display:flex;gap:8px;margin-top:10px}
.order .acts button{flex:1}
.del,.neg{color:var(--warn)}
.empty{color:var(--mute);text-align:center;padding:24px 10px}
.add{display:grid;grid-template-columns:2fr 1fr 1fr 1fr auto;gap:8px;margin-bottom:14px}
.add input,.add select,.mi{border:1px solid var(--line);background:var(--card);border-radius:10px;padding:10px;min-width:0}
.mi{width:68px;padding:8px;text-align:right}
.lb{font-size:13px;color:var(--mute);display:flex;align-items:center;gap:4px}
.card{background:var(--card);border:1px solid var(--line);border-radius:12px;padding:12px;margin-bottom:14px}
@media(max-width:560px){.add{grid-template-columns:1fr 1fr}.add input:first-child{grid-column:1/-1}}
.toast{position:fixed;left:50%;bottom:calc(20px + env(safe-area-inset-bottom,0px));transform:translateX(-50%);background:var(--ink);color:var(--bg);padding:12px 18px;border-radius:99px;z-index:20;max-width:92vw;text-align:center}
.warn{color:var(--warn);font-size:14px;margin:0 0 10px}
.ov{position:fixed;inset:0;background:rgba(15,47,71,.45);z-index:15;display:flex;align-items:flex-end;justify-content:center}
.sheet{background:var(--paper);width:100%;max-width:560px;max-height:88vh;overflow:auto;border-radius:16px 16px 0 0;padding:16px 16px calc(16px + env(safe-area-inset-bottom,0px))}
.th{width:44px;height:44px;object-fit:cover;border-radius:8px;border:1px solid var(--line)}
.cam{display:inline-flex;align-items:center;gap:6px;min-height:44px;padding:0 12px;background:var(--chip);border-radius:10px;cursor:pointer}
[hidden]{display:none!important}
</style>
</head>
<body>
<header>
  <h1>เคาน์เตอร์คิดเงิน</h1>
  <button class="tab" data-t="sale" aria-selected="true">ขาย</button>
  <button class="tab" data-t="hist" aria-selected="false">ประวัติ</button>
  <button class="tab" data-t="day" aria-selected="false">สรุป</button>
  <button class="tab" data-t="stock" aria-selected="false">สต็อก</button>
  <button class="tab" data-t="menu" aria-selected="false">เมนู</button>
</header>
<div id="stat" class="sub" style="text-align:center;padding:6px 10px" hidden></div>
<main>
  <section id="sale" class="sale">
    <div><button class="pay" id="scanB" style="margin:0 0 10px">📷 ถ่ายรูปออเดอร์ลูกค้า</button><input id="scanF" type="file" accept="image/*" capture="environment" hidden><div class="chips" id="chips"></div><div class="menu" id="menu"></div></div>
    <div class="cart" id="cartBox">
      <h2 id="cartTitle">ออเดอร์ใหม่</h2>
      <div id="lines"></div>
      <div id="promoLine"></div>
      <div class="field"><label for="dsc">ลดเพิ่ม (฿)</label><input id="dsc" type="number" inputmode="decimal" min="0" placeholder="0"></div>
      <div class="total"><span>รวม</span><span class="num" id="total">฿0</span></div>
      <div class="change mute"><span>กำไรออเดอร์นี้</span><span class="num" id="cProfit">฿0</span></div>
      <div class="mute">ระดับความเผ็ด</div><div class="seg" id="spc"></div>
      <div class="mute">ประเภท</div><div class="seg" id="otc"></div>
      <div class="mute">ชำระด้วย</div><div class="seg" id="pmc"></div>
      <div id="cashBox">
        <div class="field"><label for="recv">รับเงิน</label><input id="recv" type="number" inputmode="decimal" min="0" placeholder="0"></div>
        <div class="quick" id="quick"></div>
        <div class="change"><span>เงินทอน</span><span class="num" id="chg">฿0</span></div>
      </div>
      <div class="field"><label for="note">โน้ต</label><input id="note" type="text" style="text-align:left;font-size:16px" placeholder="เช่น โต๊ะ 3 / ไม่ใส่ผัก"></div>
      <button class="pay" id="pay" disabled>ชำระเงินและบันทึก</button>
      <button class="ghost" id="clear">ล้างออเดอร์</button>
    </div>
  </section>

  <section id="hist" hidden>
    <div class="sum">
      <div><small>ยอดขายวันนี้</small><strong class="num" id="sToday">฿0</strong></div>
      <div><small>ออเดอร์</small><strong class="num" id="cToday">0</strong></div>
      <div><small>กำไรวันนี้</small><strong class="num" id="pToday">฿0</strong></div>
    </div>
    <div class="chips"><button id="fToday" aria-pressed="true">วันนี้</button><button id="fAll" aria-pressed="false">ทั้งหมด</button></div>
    <div id="orders"></div>
  </section>

  <section id="day" hidden>
    <div class="sum">
      <div><small>ยอดขาย</small><strong class="num" id="dSale">฿0</strong></div>
      <div><small>ต้นทุน+จ่าย</small><strong class="num" id="dCost">฿0</strong></div>
      <div><small>กำไรสุทธิ</small><strong class="num" id="dNet">฿0</strong></div>
    </div>
    <div class="chips" id="rg"><button data-rg="7" aria-pressed="false">7 วัน</button><button data-rg="30" aria-pressed="true">30 วัน</button><button data-rg="0" aria-pressed="false">ทั้งหมด</button></div>
    <p class="warn" id="warnK"></p>
    <h2>เมนูขายดี (จำนวน / กำไรก่อนโปร)</h2>
    <div class="card" id="top"></div>
    <p class="sub" id="wasteLine"></p>
    <h2>จดค่าใช้จ่ายอื่นๆ / ของเสีย</h2>
    <div class="add">
      <input id="xN" placeholder="รายการ">
      <input id="xA" type="number" inputmode="decimal" placeholder="จำนวนเงิน">
      <select id="xT" aria-label="ประเภท"><option value="">ค่าใช้จ่าย</option><option value="w">ของเสีย</option></select>
      <input id="xD" type="date" aria-label="วันที่">
      <button id="xB">บันทึก</button>
    </div>
    <h2>สรุปรายวัน</h2>
    <div id="days"></div>
    <div id="exBox" hidden style="display:flex;gap:8px;flex-wrap:wrap"><button id="exO">ส่งออกออเดอร์ (CSV)</button><button id="exD">ส่งออกสรุปรายวัน (CSV)</button></div>
  </section>

  <section id="stock" hidden>
    <div class="sum">
      <div><small>เตรียมมา (ไม้)</small><strong class="num" id="stP">0</strong></div>
      <div><small>ขายแล้ว (ไม้)</small><strong class="num" id="stS">0</strong></div>
      <div><small>เหลือ (ไม้)</small><strong class="num" id="stL">0</strong></div>
    </div>
    <h2>ของที่เตรียมมาวันนี้ <button id="stCopy" style="min-height:36px;padding:4px 10px;float:right">ใช้ยอดล่าสุด</button></h2>
    <div class="card" id="stList"></div>
    <h2>ต้องซื้อของเพิ่ม</h2>
    <div class="chips" id="sd"><button data-sd="1" aria-pressed="true">พรุ่งนี้</button><button data-sd="3" aria-pressed="false">3 วัน</button><button data-sd="7" aria-pressed="false">7 วัน</button></div>
    <div class="card" id="buyList"></div>
    <p class="sub" id="buyNote"></p>
  </section>

  <section id="menuEd" hidden>
    <div class="card">
      <b>ตั้งค่า</b>
      <div class="row"><span class="n">โปร ซื้อ (ไม้) แถม (ไม้) &nbsp;<small class="mute">ใส่ 0 = ปิดโปร</small></span>
        <label class="lb">ซื้อ<input class="mi num" id="pB" type="number" min="0"></label><label class="lb">แถม<input class="mi num" id="pF" type="number" min="0"></label></div>
    </div>
    <h2>เพิ่มเมนู</h2>
    <div class="row" style="border:0"><label class="cam">📷 ถ่ายรูปสินค้า<input id="aPh" type="file" accept="image/*" capture="environment" hidden></label><span id="aPhN" class="sub">ยังไม่มีรูป</span></div>
    <div class="add">
      <input id="aN" placeholder="ชื่อเมนู">
      <input id="aP" type="number" inputmode="decimal" placeholder="ราคาขาย">
      <input id="aK" type="number" inputmode="decimal" placeholder="ต้นทุน">
      <input id="aC" placeholder="หมวด">
      <button id="aB">เพิ่ม</button>
    </div>
    <h2>รายการเมนู <small class="mute">(ติ๊ก "นับโปร" = นับเป็นไม้ในโปรแถม)</small></h2>
    <button class="ghost" id="resetMenu" style="margin:0 0 10px">โหลดเมนูร้านใหม่ (39 รายการ)</button>
    <div id="menuList"></div>
  </section>
</main>
<div class="ov" id="scanP" hidden><div class="sheet"><h2 style="margin-top:0">ผลจากรูปออเดอร์</h2><div id="scanBody"></div></div></div>
<div class="toast" id="toast" hidden></div>

<script>
const KEY="pos-mala-v2",NOSK=["เส้น/ข้าว","ซุป","เครื่องดื่ม"];
const mk=(id,n,p,c)=>({id,n,p,k:0,c,s:!NOSK.includes(c)});
const DEF={seq:0,orders:[],exp:{},cnt:{},promo:{buy:10,free:1},gp:30,menu:[
 mk("m1","หมูสามชั้น",10,"เนื้อสัตว์"),mk("m2","เนื้อสไลซ์",15,"เนื้อสัตว์"),mk("m3","ไส้กรอก",10,"เนื้อสัตว์"),mk("m4","กุ้ง",20,"เนื้อสัตว์"),
 mk("m5","ลูกชิ้นปลา",7,"ลูกชิ้น"),mk("m6","ลูกชิ้นหมู",7,"ลูกชิ้น"),mk("m7","ปูอัด",7,"ลูกชิ้น"),
 mk("m8","เห็ดเข็มทอง",7,"ผัก/เห็ด"),mk("m9","ผักกาดขาว",5,"ผัก/เห็ด"),mk("m10","เต้าหู้",7,"ผัก/เห็ด"),
 mk("m11","วุ้นเส้น",10,"เส้น/ข้าว"),mk("m12","บะหมี่",10,"เส้น/ข้าว"),mk("m13","ข้าวสวย",10,"เส้น/ข้าว"),
 mk("m14","น้ำซุปหม่าล่า",20,"ซุป"),mk("m15","ชาเย็น",30,"เครื่องดื่ม"),mk("m16","น้ำเปล่า",10,"เครื่องดื่ม")]};
const SPICE=["ไม่เผ็ด","เผ็ดน้อย","เผ็ดกลาง","เผ็ดมาก","เผ็ดสุด"];
const OT={dine:"ทานที่ร้าน",take:"ห่อกลับ"},PM={cash:"เงินสด",qr:"โอน/QR"};
let S=JSON.parse(JSON.stringify(DEF)),cart={},cat="ทั้งหมด",onlyToday=true,dbDoc=null,dl=null,range=30,sp="",ot="dine",pm="cash";
const $=id=>document.getElementById(id);
const baht=n=>"฿"+Number(n).toLocaleString("th-TH");
const esc=s=>String(s).replace(/[&<>"]/g,c=>({"&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;"}[c]));
const lk=t=>{const d=new Date(t);return d.getFullYear()+"-"+String(d.getMonth()+1).padStart(2,"0")+"-"+String(d.getDate()).padStart(2,"0")};
const pad=n=>String(n).padStart(4,"0");
const setStat=t=>{const s=document.getElementById("stat");if(s){s.hidden=false;s.textContent=t}};
window.addEventListener("error",e=>setStat("⚠ ข้อผิดพลาด: "+(e.message||"")));
function toast(m){const t=$("toast");t.textContent=m;t.hidden=false;clearTimeout(toast.h);toast.h=setTimeout(()=>t.hidden=true,2600)}

function newMenu(){const A=[["หมู",10,3.61],["ไก่",10,5],["เห็ดเข็ม",10,0.9],["มันฝรั่ง",10,1.6],["กระเจียบ",10,1],["บ็อกโคลี",10,2.5],["เห็ดหลิ้นขาว",10,0.9],["เห็ดชิเมจิ",10,4],["กุ้งหิมะ",10,5],["ฟองเต้าหู้ซีฟู้ด",10,3.1],["สเต็กหมู",10,5.45],["เต้าหู้ปลา",10,2.5],["สามชั้นสไลด์",10,4],["ไก่สามชั้น",10,2.67],["ปูอัดชีส",10,5.45],["ออมูก",10,2.4],["ไส้กรอกพันเบคอน",10,4],["นักเก็ตสไปซี่",10,5.62],["กุ้งระเบิด",10,4],["ไก่สไปซี่",10,4],["ปลา",10,2.85],["ไส้กรอกแดง",10,2.66],["ปูอัด",10,4.46],["ไก่เกี๊ยว",10,2.69],["จ๊อสาหร่าย",10,3],["ไส้กรอกชีส",12,5.93],["ไส้กรอกอีสาน",12,5.66],["ไส้กรอกหนังกรอบ",12,5.31],["ไส้กรอกนม",12,5.93],["สันในไก่kfc",12,5],["ฟุตลองชีส",12,5.33],["เต้าหู้ชีส",12,6.25],["ชีสบอล",12,5],["ฟุตลองพันเบคอน",12,6.6],["อีสานเล็ก",10,3.52],["ปีกกลางอบ",12,4.82],["ฮอตชีส",12,5.33],["ปูอัดเล็ก",10,3.75],["โบโรน่า",10,3.92]];return A.map(([n,p,k],i)=>({id:"p"+(i+1),n,p,k,c:p>=12?"ไม้ 12 บาท":"ไม้ 10 บาท",s:true}))}
function fix(){if(!Array.isArray(S.menu))S.menu=[];if(!S.menu.length||((S.v||0)<3&&S.menu.every(m=>/^m\d{1,2}$/.test(m.id))))S.menu=newMenu();S.v=3;S.stock=S.stock||{};S.exp=S.exp||{};S.cnt=S.cnt||{};S.promo=S.promo||{buy:10,free:1};if(S.gp==null)S.gp=30;S.menu.forEach(m=>{if(m.s===undefined)m.s=!NOSK.includes(m.c)})}
async function save(){
  const json=JSON.stringify(S);
  try{localStorage.setItem(KEY,json)}catch(e){}
  if(dbDoc){try{await dbDoc.set({json})}catch(e){}}
}
function adopt(json){try{const d=JSON.parse(json);if(d&&Array.isArray(d.orders)&&Array.isArray(d.menu)){S=d;fix();return true}}catch(e){}return false}
async function init(){
  try{const j=localStorage.getItem(KEY);if(j)adopt(j)}catch(e){}
  render();loadPh();
  try{
    if(!window.claude||!claude.use)return;
    try{dl=await claude.use("downloads");$("exBox").hidden=!dl}catch(e){}
    const db=await claude.use("db"),user=await claude.use("user");
    const id=user?await user.id():null;
    if(!db||!id){setStat("⚠ บันทึกในเครื่องนี้เท่านั้น (ยังไม่ได้เชื่อมต่อบัญชี ลองรีเฟรชหน้าและกดอนุญาต)");return}
    col=db.collection("data/users/"+id);dbDoc=col.doc("pos-mala");
    const snap=await dbDoc.get();
    if(snap.exists&&snap.data()&&snap.data().json){if(adopt(snap.data().json))render()}
    else await save();
    loadPh();setStat("✓ บันทึกบนบัญชีของคุณ");
  }catch(e){dbDoc=null;setStat("⚠ บันทึกในเครื่องนี้เท่านั้น (เชื่อมต่อบัญชีไม่ได้)")}
}

const cats=()=>["ทั้งหมด",...new Set(S.menu.map(m=>m.c||"อื่นๆ"))];
function cartItems(){return Object.entries(cart).map(([id,q])=>{const m=S.menu.find(x=>x.id===id);return m?{id,n:m.n,p:m.p,k:m.k||0,s:!!m.s,q}:null}).filter(Boolean)}
function calc(){
  const items=cartItems(),sub=items.reduce((s,i)=>s+i.p*i.q,0),cost=items.reduce((s,i)=>s+i.k*i.q,0);
  const pr=[];items.forEach(i=>{if(i.s)for(let j=0;j<i.q;j++)pr.push(i.p)});pr.sort((a,b)=>a-b);
  const b=+S.promo.buy||0,f=+S.promo.free||0,g=b>0&&f>0?b+f:0,n=pr.length,fr=g?Math.floor(n/g)*f:0;
  const pd=pr.slice(0,fr).reduce((s,x)=>s+x,0);
  const man=Math.min(Math.max(0,parseFloat($("dsc").value)||0),sub-pd);
  const total=sub-pd-man,gp=0;
  return{items,sub,cost,n,g,fr,pd,man,total,gp};
}
const seg=(g,opts,cur)=>opts.map(([v,l])=>`<button data-g="${g}" data-v="${v}" aria-pressed="${v===cur}">${l}</button>`).join("");

function render(){renderSale();renderHist();renderDay();renderStock();renderMenuEd()}
function renderSale(){
  if(!cats().includes(cat))cat="ทั้งหมด";SD=soldBy(lk(Date.now()));
  $("chips").innerHTML=cats().map(c=>`<button data-c="${esc(c)}" aria-pressed="${c===cat}">${esc(c)}</button>`).join("");
  const list=S.menu.filter(m=>cat==="ทั้งหมด"||(m.c||"อื่นๆ")===cat);
  $("menu").innerHTML=list.length?list.map(m=>`<button class="item" data-id="${m.id}"><b>${esc(m.n)}</b><span class="p num">${baht(m.p)}${rem(m)}</span>${cart[m.id]?`<span class="badge num">${cart[m.id]}</span>`:""}</button>`).join(""):`<div class="empty">ยังไม่มีเมนู เพิ่มได้ที่แท็บ "เมนู"</div>`;
  renderCart();
}
function renderCart(){
  const c=calc(),{items,total}=c;
  $("lines").innerHTML=items.length?items.map(i=>`<div class="row"><span class="n">${esc(i.n)}<br><small class="num mute">${baht(i.p)}</small></span><span class="q"><button data-d="-1" data-id="${i.id}" aria-label="ลด">−</button><b class="num" style="min-width:22px;text-align:center">${i.q}</b><button data-d="1" data-id="${i.id}" aria-label="เพิ่ม">+</button></span><span class="num" style="min-width:56px;text-align:right">${baht(i.p*i.q)}</span></div>`).join(""):`<div class="empty">แตะเมนูเพื่อเพิ่มรายการ</div>`;
  $("promoLine").innerHTML=c.g&&items.length?`<div class="row promo"><span class="n">โปร ซื้อ${S.promo.buy}แถม${S.promo.free} · ไม้ ${c.n}${c.fr?` · ฟรี ${c.fr}`:""} (อีก ${c.g-c.n%c.g} ไม้ได้ฟรีเพิ่ม)</span><span class="num">${c.pd?"−"+baht(c.pd):""}</span></div>`:"";
  $("total").textContent=baht(total);
  $("cProfit").textContent=baht(total-c.cost-c.gp);
  $("spc").innerHTML=seg("sp",SPICE.map(x=>[x,x]),sp);
  $("otc").innerHTML=seg("ot",Object.entries(OT),ot);
  $("pmc").innerHTML=seg("pm",Object.entries(PM),pm);
  $("cashBox").hidden=pm!=="cash";
  const r=parseFloat($("recv").value);
  const q=[...new Set([total,20,50,100,500,1000].filter(x=>x>=total&&x>0))].slice(0,5);
  $("quick").innerHTML=q.map(x=>`<button data-r="${x}" class="num">${x===total?"พอดี ":""}${baht(x)}</button>`).join("");
  $("chg").textContent=baht(isNaN(r)?0:Math.max(0,r-total));
  $("pay").disabled=!items.length||(pm==="cash"&&!isNaN(r)&&r<total);
}
const profitO=o=>o.total-(o.cost||0)-(o.gp||0);
function renderHist(){
  const all=S.orders.slice().reverse(),tk=lk(Date.now());
  const today=all.filter(o=>lk(o.t)===tk);
  $("sToday").textContent=baht(today.reduce((s,o)=>s+o.total,0));
  $("cToday").textContent=today.length;
  $("pToday").textContent=baht(today.reduce((s,o)=>s+profitO(o),0));
  $("fToday").setAttribute("aria-pressed",onlyToday);$("fAll").setAttribute("aria-pressed",!onlyToday);
  const show=onlyToday?today:all;
  $("orders").innerHTML=show.length?show.map(o=>{
    const tm=new Date(o.t).toLocaleString("th-TH",onlyToday?{hour:"2-digit",minute:"2-digit"}:{day:"numeric",month:"short",hour:"2-digit",minute:"2-digit"});
    const tags=[OT[o.ot||"dine"],PM[o.pm||"cash"],o.sp,o.note].filter(Boolean).map(esc).join(" · ");
    return `<details class="order"><summary><span><b>ออเดอร์ #${pad(o.no)}</b><br><span class="sub">${tm} · ${o.items.reduce((s,i)=>s+i.q,0)} รายการ<br>${tags}</span></span><b class="num">${baht(o.total)}</b></summary><div class="body">${o.items.map(i=>`<div class="row"><span class="n">${esc(i.n)} × ${i.q}</span><span class="num">${baht(i.p*i.q)}</span></div>`).join("")}${o.pd?`<div class="row promo"><span class="n">โปรแถมฟรี ${o.fr} ไม้</span><span class="num">−${baht(o.pd)}</span></div>`:""}${o.man?`<div class="row"><span class="n">ส่วนลด</span><span class="num">−${baht(o.man)}</span></div>`:""}${o.gp?`<div class="row"><span class="n">ค่า GP เดลิเวอรี</span><span class="num">−${baht(o.gp)}</span></div>`:""}<div class="row"><span class="n">ต้นทุน / กำไร</span><span class="num">${baht(o.cost||0)} / ${baht(profitO(o))}</span></div><div class="row"><span class="n">รับเงิน / ทอน</span><span class="num">${baht(o.recv)} / ${baht(Math.max(0,o.recv-o.total))}</span></div><div class="acts"><button data-again="${o.no}">สั่งซ้ำ</button><button class="del" data-rm="${o.no}">ลบ</button></div></div></details>`}).join(""):`<div class="empty">ยังไม่มีออเดอร์${onlyToday?"วันนี้":""}</div>`;
}

function byDay(){
  const days={},D=k=>days[k]||(days[k]={k,n:0,s:0,c:0,g:0,cash:0,qr:0,x:[]});
  S.orders.forEach(o=>{const d=D(lk(o.t));d.n++;d.s+=o.total;d.c+=o.cost||0;d.g+=o.gp||0;if(o.pm==="qr")d.qr+=o.total;else d.cash+=o.total});
  Object.entries(S.exp).forEach(([k,l])=>{D(k).x=l});
  return days;
}
const exT=d=>d.x.reduce((s,e)=>s+e.a,0),netD=d=>d.s-d.c-d.g-exT(d);
const diffTxt=(cnt,cash)=>{const x=cnt-cash;return x===0?"✓ เงินสดตรงกับระบบ":(x<0?"เงินขาด ":"เงินเกิน ")+baht(Math.abs(x))};
function renderDay(){
  const days=byDay(),cut=range?lk(Date.now()-range*864e5):"";
  const list=Object.values(days).filter(d=>d.k>cut).sort((a,b)=>b.k.localeCompare(a.k));
  const sale=list.reduce((s,d)=>s+d.s,0),net=list.reduce((s,d)=>s+netD(d),0);
  $("dSale").textContent=baht(sale);$("dCost").textContent=baht(sale-net);
  const nt=$("dNet");nt.textContent=baht(net);nt.className="num"+(net<0?" neg":"");
  document.querySelectorAll("[data-rg]").forEach(b=>b.setAttribute("aria-pressed",+b.dataset.rg===range));
  const nk=S.menu.filter(m=>!m.k).length;
  $("warnK").textContent=nk?`มี ${nk} เมนูที่ยังไม่ได้ใส่ต้นทุน (ใส่ได้ที่แท็บเมนู) กำไรจะสูงกว่าจริง`:"";
  const m={};S.orders.filter(o=>lk(o.t)>cut).forEach(o=>o.items.forEach(i=>{const x=m[i.n]||(m[i.n]={q:0,g:0});x.q+=i.q;x.g+=(i.p-(i.k||0))*i.q}));
  const top=Object.entries(m).sort((a,b)=>b[1].q-a[1].q).slice(0,8);
  $("top").innerHTML=top.length?top.map(([n,x],i)=>`<div class="row"><span class="n">${i+1}. ${esc(n)}</span><span class="num">×${x.q}</span><span class="num" style="min-width:72px;text-align:right">${baht(x.g)}</span></div>`).join(""):`<div class="empty">ยังไม่มีข้อมูล</div>`;
  const w=list.reduce((s,d)=>s+d.x.filter(e=>e.w).reduce((a,e)=>a+e.a,0),0);
  $("wasteLine").textContent=w?`ของเสียช่วงนี้รวม ${baht(w)}`:"";
  $("days").innerHTML=list.length?list.map(d=>{
    const e=exT(d),g=d.s-d.c,n=netD(d),cn=S.cnt[d.k];
    const R=(l,v)=>`<div class="row"><span class="n">${l}</span><span class="num">${v}</span></div>`;
    const dt=new Date(d.k+"T00:00:00").toLocaleDateString("th-TH",{weekday:"short",day:"numeric",month:"short",year:"2-digit"});
    return `<details class="order"><summary><span><b>${dt}</b><br><span class="sub">${d.n} ออเดอร์ · ขาย ${baht(d.s)}</span></span><b class="num${n<0?" neg":""}">${baht(n)}</b></summary><div class="body">${R("ยอดขาย",baht(d.s))}${R("ต้นทุนวัตถุดิบ","−"+baht(d.c))}${R(`<b>กำไรขั้นต้น</b>${d.s?` (${Math.round(g/d.s*100)}%)`:""}`,`<b>${baht(g)}</b>`)}${d.g?R("ค่า GP เดลิเวอรี","−"+baht(d.g)):""}${d.x.map((x,i)=>`<div class="row"><span class="n">${esc(x.n)}${x.w?" (ของเสีย)":""}</span><span class="num">−${baht(x.a)}</span><button class="del" data-xd="${d.k}|${i}" style="min-height:32px;padding:2px 10px" aria-label="ลบ ${esc(x.n)}">ลบ</button></div>`).join("")}${R("<b>กำไรสุทธิ</b>",`<b class="${n<0?"neg":""}">${baht(n)}</b>`)}<h2>ปิดยอดเงินสด</h2>${R("ขายเงินสด (ระบบ)",baht(d.cash))}${R("ขายโอน/QR",baht(d.qr))}<div class="field"><label>นับเงินสดได้</label><input type="number" inputmode="decimal" data-cnt="${d.k}" data-cash="${d.cash}" value="${cn??""}"></div><div class="sub" style="text-align:right">${cn==null?"นับเฉพาะเงินที่ได้จากการขาย ไม่รวมเงินตั้งต้น":diffTxt(cn,d.cash)}</div></div></details>`}).join(""):`<div class="empty">ยังไม่มีข้อมูลในช่วงนี้</div>`;
}
function renderMenuEd(){
  $("pB").value=S.promo.buy;$("pF").value=S.promo.free;
  $("menuList").innerHTML=S.menu.map(m=>`<div class="row"><span class="n" style="flex:1 1 100%;display:flex;align-items:center;gap:8px">${PH[m.id]?`<img class="th" src="${PH[m.id]}" alt="">`:""}<span>${esc(m.n)} <small class="mute">${esc(m.c||"")}</small></span></span><label class="lb">ขาย<input class="mi num" type="number" inputmode="decimal" data-p="${m.id}" value="${m.p}"></label><label class="lb">ทุน<input class="mi num" type="number" inputmode="decimal" data-k="${m.id}" value="${m.k||0}"></label><label class="lb"><input type="checkbox" data-s="${m.id}" ${m.s?"checked":""} style="width:20px;height:20px">นับโปร</label><label class="cam" style="margin-left:auto">📷<input type="file" accept="image/*" capture="environment" hidden data-ph="${m.id}"></label><button class="del" data-del="${m.id}" aria-label="ลบ ${esc(m.n)}">ลบ</button></div>`).join("")||`<div class="empty">ยังไม่มีเมนู</div>`;
}

const MAP={sale:"sale",hist:"hist",day:"day",stock:"stock",menu:"menuEd"};
document.querySelectorAll(".tab").forEach(b=>b.onclick=()=>{
  document.querySelectorAll(".tab").forEach(x=>x.setAttribute("aria-selected",x===b));
  Object.entries(MAP).forEach(([t,id])=>$(id).hidden=t!==b.dataset.t);
});
const go=t=>document.querySelector(`.tab[data-t="${t}"]`).click();
$("chips").onclick=e=>{const b=e.target.closest("[data-c]");if(b){cat=b.dataset.c;renderSale()}};
$("menu").onclick=e=>{const b=e.target.closest("[data-id]");if(b){cart[b.dataset.id]=(cart[b.dataset.id]||0)+1;renderSale()}};
$("lines").onclick=e=>{const b=e.target.closest("[data-d]");if(!b)return;const id=b.dataset.id;cart[id]=(cart[id]||0)+Number(b.dataset.d);if(cart[id]<=0)delete cart[id];renderSale()};
$("quick").onclick=e=>{const b=e.target.closest("[data-r]");if(b){$("recv").value=b.dataset.r;renderCart()}};
["spc","otc","pmc"].forEach(id=>$(id).onclick=e=>{const b=e.target.closest("[data-g]");if(!b)return;const g=b.dataset.g,v=b.dataset.v;
  if(g==="sp")sp=sp===v?"":v;else if(g==="ot")ot=v;else pm=v;renderCart()});
$("recv").oninput=renderCart;$("dsc").oninput=renderCart;
function reset(){cart={};sp="";ot="dine";pm="cash";["recv","note","dsc"].forEach(i=>$(i).value="");$("cartTitle").textContent="ออเดอร์ใหม่";renderSale()}
$("clear").onclick=reset;
$("pay").onclick=()=>{
  const c=calc();if(!c.items.length)return;
  const r=parseFloat($("recv").value);
  const o={no:++S.seq,t:Date.now(),items:c.items.map(({n,p,q,k})=>({n,p,q,k})),sub:c.sub,pd:c.pd,fr:c.fr,man:c.man,total:c.total,cost:c.cost,gp:c.gp,pm,ot,sp,recv:pm==="cash"&&!isNaN(r)?r:c.total,note:$("note").value.trim()};
  S.orders.push(o);if(S.orders.length>800)S.orders.shift();
  save();toast(`บันทึก #${pad(o.no)} · ${pm==="cash"?"ทอน "+baht(o.recv-o.total):"โอน"} · กำไร ${baht(profitO(o))}`);
  reset();renderHist();renderDay();renderStock();
};
$("fToday").onclick=()=>{onlyToday=true;renderHist()};
$("fAll").onclick=()=>{onlyToday=false;renderHist()};
$("orders").onclick=e=>{
  const a=e.target.closest("[data-again]"),d=e.target.closest("[data-rm]");
  if(a){
    const o=S.orders.find(x=>x.no==a.dataset.again);if(!o)return;
    cart={};o.items.forEach(i=>{const m=S.menu.find(x=>x.n===i.n);if(m)cart[m.id]=(cart[m.id]||0)+i.q});
    $("cartTitle").textContent=`สั่งซ้ำจาก #${pad(o.no)}`;$("recv").value="";renderSale();go("sale");
  }
  if(d){
    if(d.dataset.sure!=="1"){d.dataset.sure="1";d.textContent="แตะอีกครั้งเพื่อลบ";return}
    S.orders=S.orders.filter(x=>x.no!=d.dataset.rm);save();renderHist();renderDay();renderStock();toast("ลบออเดอร์แล้ว");
  }
};
$("rg").onclick=e=>{const b=e.target.closest("[data-rg]");if(b){range=+b.dataset.rg;renderDay()}};
$("xD").value=lk(Date.now());
$("xB").onclick=()=>{
  const n=$("xN").value.trim(),a=parseFloat($("xA").value),k=$("xD").value||lk(Date.now());
  if(!n||isNaN(a)||a<=0){toast("กรอกรายการและจำนวนเงิน");return}
  (S.exp[k]=S.exp[k]||[]).push({n,a,w:$("xT").value==="w"});$("xN").value="";$("xA").value="";save();renderDay();toast("บันทึกแล้ว");
};
$("days").onclick=e=>{const b=e.target.closest("[data-xd]");if(!b)return;const[k,i]=b.dataset.xd.split("|");S.exp[k].splice(+i,1);if(!S.exp[k].length)delete S.exp[k];save();renderDay()};
$("days").onchange=e=>{
  const t=e.target.closest("[data-cnt]");if(!t)return;
  const k=t.dataset.cnt,v=parseFloat(t.value);
  if(isNaN(v))delete S.cnt[k];else S.cnt[k]=v;save();
  t.parentNode.nextElementSibling.textContent=isNaN(v)?"":diffTxt(v,+t.dataset.cash);
};
$("aB").onclick=()=>{
  const n=$("aN").value.trim(),p=parseFloat($("aP").value),c=$("aC").value.trim()||"อื่นๆ";
  if(!n||isNaN(p)||p<0){toast("กรอกชื่อและราคาให้ครบ");return}
  const id="m"+Date.now().toString(36);S.menu.push({id,n,p,k:parseFloat($("aK").value)||0,c,s:!NOSK.includes(c)});if(newPh){putPh(id,newPh);newPh=null;$("aPhN").textContent="ยังไม่มีรูป"}
  ["aN","aP","aK"].forEach(i=>$(i).value="");save();render();toast("เพิ่มเมนูแล้ว");
};
$("menuList").onclick=e=>{const b=e.target.closest("[data-del]");if(!b)return;S.menu=S.menu.filter(m=>m.id!==b.dataset.del);delete cart[b.dataset.del];save();render()};
$("menuList").onchange=e=>{
  const t=e.target;if(t.dataset.ph){setPhoto(t.dataset.ph,t.files[0]);return}
  const id=t.dataset.p||t.dataset.k||t.dataset.s;if(!id)return;
  const m=S.menu.find(x=>x.id===id);if(!m)return;
  if(t.dataset.s)m.s=t.checked;else{const v=Math.max(0,parseFloat(t.value)||0);if(t.dataset.p)m.p=v;else m.k=v;t.value=v}
  save();renderSale();renderDay();
};
[["pB",v=>S.promo.buy=v],["pF",v=>S.promo.free=v]].forEach(([id,f])=>$(id).onchange=()=>{f(Math.max(0,parseFloat($(id).value)||0));save();renderMenuEd();renderCart()});

const csv=rows=>"\ufeff"+rows.map(r=>r.map(v=>{v=String(v??"");return /[",\n]/.test(v)?'"'+v.replace(/"/g,'""')+'"':v}).join(",")).join("\r\n");
async function exp(name,rows){try{await dl.save({filename:name,data:csv(rows)})}catch(e){if(!e||e.code!=="declined")toast("บันทึกไฟล์ไม่สำเร็จ")}}
$("exO").onclick=()=>exp("ออเดอร์.csv",[["เลขที่","วันเวลา","ประเภท","ชำระ","รายการ","ยอดก่อนลด","โปรแถม","ส่วนลด","ยอดสุทธิ","ต้นทุน","GP","กำไร","ความเผ็ด","โน้ต"],
  ...S.orders.map(o=>[o.no,new Date(o.t).toLocaleString("th-TH"),OT[o.ot||"dine"],PM[o.pm||"cash"],o.items.map(i=>i.n+"x"+i.q).join("; "),o.sub??o.total,o.pd||0,o.man||0,o.total,o.cost||0,o.gp||0,profitO(o),o.sp||"",o.note||""])]);
$("exD").onclick=()=>exp("สรุปรายวัน.csv",[["วันที่","ออเดอร์","ยอดขาย","ต้นทุน","GP","ค่าใช้จ่าย/ของเสีย","กำไรสุทธิ","ขายเงินสด","ขายโอน","นับเงินสดได้"],
  ...Object.values(byDay()).sort((a,b)=>a.k.localeCompare(b.k)).map(d=>[d.k,d.n,d.s,d.c,d.g,exT(d),netD(d),d.cash,d.qr,S.cnt[d.k]??""])]);
fix();
let SD={},PH={},newPh=null,col=null,sdays=1,scanRes={},scanNote="",scanImg="";
function soldBy(day){const m={};S.orders.forEach(o=>{if(lk(o.t)===day)o.items.forEach(i=>m[i.n]=(m[i.n]||0)+i.q)});return m}
function rem(m){const p=(S.stock[lk(Date.now())]||{})[m.id];if(p==null)return"";const l=p-(SD[m.n]||0);return ` · <span class="${l<=0?"neg":""}">เหลือ ${l}</span>`}

/* ---------- stock ---------- */
function renderStock(){
  const td=lk(Date.now()),st=S.stock[td]||{},sold=soldBy(td),sk=S.menu.filter(m=>m.s);
  $("stP").textContent=sk.reduce((s,m)=>s+(st[m.id]||0),0);
  $("stS").textContent=sk.reduce((s,m)=>s+(sold[m.n]||0),0);
  $("stL").textContent=sk.reduce((s,m)=>s+(st[m.id]!=null?st[m.id]-(sold[m.n]||0):0),0);
  $("stList").innerHTML=S.menu.map(m=>{const p=st[m.id],l=p==null?null:p-(sold[m.n]||0);return `<div class="row"><span class="n">${esc(m.n)}<br><small class="mute num">ขายแล้ว ${sold[m.n]||0}</small></span><label class="lb">เตรียม<input class="mi num" type="number" inputmode="numeric" data-sp="${m.id}" value="${p??""}"></label><b class="num${l!=null&&l<=0?" neg":""}" style="min-width:70px;text-align:right">${l==null?"":"เหลือ "+l}</b></div>`}).join("")||`<div class="empty">ยังไม่มีเมนู</div>`;
  document.querySelectorAll("[data-sd]").forEach(b=>b.setAttribute("aria-pressed",+b.dataset.sd===sdays));
  const dts=[...new Set(S.orders.map(o=>lk(o.t)))].filter(d=>d<td).sort().reverse().slice(0,7);
  const use=dts.length?dts:[td],tot={};
  use.forEach(d=>{const s=soldBy(d);for(const n in s)tot[n]=(tot[n]||0)+s[n]});
  const rows=S.menu.map(m=>{const avg=(tot[m.n]||0)/use.length,need=Math.ceil(avg*1.1*sdays),left=st[m.id]!=null?Math.max(0,st[m.id]-(sold[m.n]||0)):0;return{m,avg,left,buy:Math.max(0,need-left)}}).filter(r=>r.avg>0).sort((a,b)=>b.buy-a.buy);
  $("buyList").innerHTML=rows.length?rows.map(r=>`<div class="row"><span class="n">${esc(r.m.n)}<br><small class="mute num">เฉลี่ย ${r.avg.toFixed(1)}/วัน · เหลือ ${r.left}</small></span><b class="num">${r.buy?"ซื้อ "+r.buy:"พอแล้ว"}</b></div>`).join(""):`<div class="empty">ยังไม่มีข้อมูลการขายให้คำนวณ</div>`;
  const est=rows.reduce((s,r)=>s+r.buy*(r.m.k||0),0);
  $("buyNote").textContent=rows.length?`คิดจากยอดขายเฉลี่ย ${dts.length?dts.length+" วันที่ผ่านมา":"วันนี้"} เผื่อ 10% ลบของที่เหลือคืนนี้${est?" · งบต้นทุนโดยประมาณ "+baht(est):""}`:"";
}
$("stList").onchange=e=>{const t=e.target.closest("[data-sp]");if(!t)return;const td=lk(Date.now()),v=parseInt(t.value);S.stock[td]=S.stock[td]||{};if(isNaN(v))delete S.stock[td][t.dataset.sp];else S.stock[td][t.dataset.sp]=Math.max(0,v);save();renderStock();renderSale()};
$("stCopy").onclick=()=>{const td=lk(Date.now()),prev=Object.keys(S.stock).filter(d=>d<td).sort().pop();if(!prev){toast("ยังไม่มีข้อมูลวันก่อนหน้า");return}S.stock[td]=Object.assign({},S.stock[prev],S.stock[td]||{});save();renderStock();renderSale();toast("ใช้ยอดเตรียมจากวันที่ "+prev)};
$("sd").onclick=e=>{const b=e.target.closest("[data-sd]");if(b){sdays=+b.dataset.sd;renderStock()}};

/* ---------- photos ---------- */
function shrink(file,max,q,blob){return new Promise((res,rej)=>{const rd=new FileReader(),im=new Image();im.onload=()=>{const r=Math.min(1,max/Math.max(im.width,im.height)),c=document.createElement("canvas");c.width=Math.round(im.width*r);c.height=Math.round(im.height*r);c.getContext("2d").drawImage(im,0,0,c.width,c.height);blob?c.toBlob(b=>b?res(b):rej(),"image/jpeg",q):res(c.toDataURL("image/jpeg",q))};im.onerror=rej;rd.onload=()=>{im.src=rd.result};rd.onerror=rej;rd.readAsDataURL(file)})}
async function putPh(id,url){PH[id]=url;try{localStorage.setItem("pos-ph-"+id,url)}catch(e){}if(col){try{await col.doc("ph-"+id).set({img:url})}catch(e){}}}
async function loadPh(){for(const m of S.menu){if(PH[m.id])continue;let u=null;try{u=localStorage.getItem("pos-ph-"+m.id)}catch(e){}if(!u&&col){try{const s=await col.doc("ph-"+m.id).get();if(s.exists)u=s.data().img}catch(e){}}if(u)PH[m.id]=u}renderMenuEd()}
async function setPhoto(id,f){if(!f)return;try{await putPh(id,await shrink(f,360,.72));renderMenuEd();toast("บันทึกรูปสินค้าแล้ว")}catch(e){toast("อ่านรูปไม่สำเร็จ")}}
$("aPh").onchange=async e=>{const f=e.target.files[0];if(!f)return;try{newPh=await shrink(f,360,.72);$("aPhN").textContent="มีรูปแล้ว ✓"}catch(err){toast("อ่านรูปไม่สำเร็จ")}};

/* ---------- scan order photo ---------- */
function montage(its){
  const cols=its.length>16?6:4,cw=its.length>16?200:240,ch=its.length>16?220:260,c=document.createElement("canvas");c.width=cols*cw;c.height=Math.ceil(its.length/cols)*ch;
  const g=c.getContext("2d");g.fillStyle="#fff";g.fillRect(0,0,c.width,c.height);
  return Promise.all(its.map(m=>new Promise(r=>{const im=new Image();im.onload=()=>r(im);im.onerror=()=>r(null);im.src=PH[m.id]}))).then(a=>{
    a.forEach((im,i)=>{const m=its[i],x=(i%cols)*cw,y=Math.floor(i/cols)*ch;
      if(im){const s=Math.min((cw-10)/im.width,(ch-50)/im.height);g.drawImage(im,x+5,y+5,im.width*s,im.height*s)}
      g.strokeStyle="#0b7fbf";g.lineWidth=2;g.strokeRect(x+2,y+2,cw-4,ch-4);
      g.fillStyle="#000";g.font="bold 20px sans-serif";g.fillText(m.id+"  ฿"+m.p,x+8,y+ch-26);g.font="15px sans-serif";g.fillText(m.n.slice(0,16),x+8,y+ch-8)});
    return new Promise(r=>c.toBlob(r,"image/jpeg",.82))});
}
function renderScan(){
  const ids=Object.keys(scanRes),tot=ids.reduce((s,id)=>{const m=S.menu.find(x=>x.id===id);return s+(m?m.p*scanRes[id]:0)},0);
  $("scanBody").innerHTML=(scanImg?`<img src="${scanImg}" alt="" style="max-width:100%;max-height:160px;border-radius:10px;display:block;margin:0 auto 8px">`:"")+(ids.length?ids.map(id=>{const m=S.menu.find(x=>x.id===id);return `<div class="row"><span class="n">${esc(m.n)}<br><small class="num mute">${baht(m.p)}</small></span><span class="q"><button data-sd2="-1" data-id="${id}" aria-label="ลด">−</button><b class="num" style="min-width:22px;text-align:center">${scanRes[id]}</b><button data-sd2="1" data-id="${id}" aria-label="เพิ่ม">+</button></span><span class="num" style="min-width:56px;text-align:right">${baht(m.p*scanRes[id])}</span></div>`}).join(""):`<div class="empty">ไม่พบสินค้าในรูป ลองถ่ายใหม่ให้ชัดขึ้น</div>`)+`<div class="total"><span>รวม (ก่อนโปร)</span><span class="num">${baht(tot)}</span></div>`+(scanNote?`<p class="sub">${esc(scanNote)}</p>`:"")+`<p class="sub">ตรวจนับให้ตรงกับของจริงก่อนยืนยัน แก้ได้ด้วยปุ่ม + − โปรแถมจะคำนวณในบิลให้</p><button class="pay" data-act="ok" ${ids.length?"":"disabled"}>ใส่ลงบิล</button><button class="ghost" data-act="no">ยกเลิก</button>`;
}
async function scan(file){
  const its=S.menu.filter(m=>PH[m.id]);
  if(!its.length){toast("ยังไม่มีรูปสินค้า ถ่ายรูปที่แท็บเมนูก่อน");return}
  let sm=null;try{sm=window.claude&&await claude.use("sample")}catch(e){}
  if(!sm){toast("หน้านี้ยังอ่านรูปไม่ได้");return}
  scanRes={};scanNote="";scanImg="";$("scanP").hidden=false;$("scanBody").innerHTML=`<div class="empty">กำลังอ่านรูป…</div>`;
  try{
    const [mont,cb,cu]=await Promise.all([montage(its),shrink(file,1024,.8,true),shrink(file,320,.6)]);
    scanImg=cu;
    const list=its.map(m=>`${m.id} = ${m.n} ราคา ${m.p} บาท`).join("\n");
    const out=await sm.json(`ภาพแรกคือแคตตาล็อกสินค้าของร้านหม่าล่า (ไม้เสียบ) แต่ละช่องมีรหัสและราคากำกับ\nภาพที่สองคือออเดอร์ของลูกค้า ให้ดูชนิดวัตถุดิบ สี และลักษณะไม้ แล้วนับจำนวนสินค้าแต่ละรหัสที่เห็นในภาพที่สอง\nรหัสที่มี:\n${list}\nตอบเป็น JSON เท่านั้น รูปแบบ {"items":[{"id":"m1","qty":3}],"note":"ข้อสังเกตสั้นๆ ถ้าไม่แน่ใจ"} ใส่เฉพาะรหัสที่เห็นจริง ถ้าไม่แน่ใจให้ประมาณจำนวนที่น่าจะเป็นแล้วบอกใน note`,{images:[mont,cb]});
    (out.items||[]).forEach(i=>{if(S.menu.some(m=>m.id===i.id)&&i.qty>0)scanRes[i.id]=Math.round(i.qty)});
    scanNote=out.note||"";renderScan();
  }catch(e){$("scanBody").innerHTML=`<div class="empty">อ่านรูปไม่สำเร็จ ลองใหม่อีกครั้ง</div><button class="ghost" data-act="no">ปิด</button>`}
}
$("scanB").onclick=()=>$("scanF").click();
$("scanF").onchange=e=>{const f=e.target.files[0];e.target.value="";if(f)scan(f)};
$("scanP").onclick=e=>{if(e.target===$("scanP"))$("scanP").hidden=true};
$("scanBody").onclick=e=>{
  const a=e.target.closest("[data-act]"),d=e.target.closest("[data-sd2]");
  if(d){const id=d.dataset.id;scanRes[id]=Math.max(0,(scanRes[id]||0)+Number(d.dataset.sd2));renderScan();return}
  if(!a)return;
  if(a.dataset.act==="ok"){Object.entries(scanRes).forEach(([id,q])=>{if(q>0)cart[id]=(cart[id]||0)+q});$("scanP").hidden=true;renderSale();toast("ใส่ลงบิลแล้ว ตรวจแล้วกดชำระเงิน")}else $("scanP").hidden=true;
};
$("resetMenu").onclick=e=>{const b=e.currentTarget;if(b.dataset.sure!=="1"){b.dataset.sure="1";b.textContent="แตะอีกครั้งเพื่อยืนยัน (ราคา/ต้นทุนที่แก้ไว้จะถูกรีเซ็ต)";return}b.dataset.sure="";b.textContent="โหลดเมนูร้านใหม่ (39 รายการ)";S.menu=newMenu();cart={};save();render();loadPh();toast("โหลดเมนูแล้ว")};
init();
</script>
</body>
</html>
