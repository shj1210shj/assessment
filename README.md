<!doctype html>
<html lang="ko">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>업적/능력 평가 시트 (200점 만점)</title>
  <style>
    :root{
      --bg:#0b1220; --panel:#0f1830; --text:#eef3ff; --muted:#a6b3c8;
      --line:rgba(255,255,255,.12); --accent:#7aa7ff; --good:#52d1b7; --warn:#ffcc66; --bad:#ff6b6b;
      --shadow:0 18px 45px rgba(0,0,0,.35); --r:16px;
      --mono: ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, "Liberation Mono","Courier New", monospace;
      --sans: system-ui, -apple-system, "Segoe UI", Roboto, "Noto Sans KR","Apple SD Gothic Neo","Malgun Gothic", Arial, sans-serif;
    }
    *{box-sizing:border-box}
    body{
      margin:0; font-family:var(--sans); color:var(--text);
      background:
        radial-gradient(1200px 700px at 10% -10%, rgba(122,167,255,.25), transparent 60%),
        radial-gradient(900px 600px at 110% 10%, rgba(82,209,183,.18), transparent 55%),
        linear-gradient(180deg, #070c17, var(--bg));
      min-height:100vh;
    }
    .wrap{max-width:1180px;margin:0 auto;padding:26px 18px 70px}
    header{display:flex;flex-wrap:wrap;gap:14px;align-items:flex-end;justify-content:space-between;margin-bottom:14px}
    .h-title{font-size:22px;font-weight:900;letter-spacing:-.2px}
    .h-sub{color:var(--muted);font-size:13px;line-height:1.45}
    .actions{display:flex;flex-wrap:wrap;gap:8px}
    button{
      border:1px solid var(--line); background:rgba(0,0,0,.15); color:var(--text);
      padding:10px 12px;border-radius:12px;font-weight:800;cursor:pointer;transition:filter .15s ease,transform .06s ease;
    }
    button:hover{filter:brightness(1.08)} button:active{transform:translateY(1px)}
    button.primary{background:linear-gradient(180deg, rgba(122,167,255,.25), rgba(122,167,255,.12));border-color:rgba(122,167,255,.35)}
    button.good{background:linear-gradient(180deg, rgba(82,209,183,.22), rgba(82,209,183,.10));border-color:rgba(82,209,183,.35)}
    button.warn{background:linear-gradient(180deg, rgba(255,204,102,.22), rgba(255,204,102,.10));border-color:rgba(255,204,102,.35)}
    button.danger{background:linear-gradient(180deg, rgba(255,107,107,.22), rgba(255,107,107,.10));border-color:rgba(255,107,107,.35)}
    .grid{display:grid;grid-template-columns: 360px 1fr;gap:14px;align-items:start}
    @media (max-width: 980px){.grid{grid-template-columns:1fr}}

    .card{
      border:1px solid var(--line); border-radius:var(--r); box-shadow:var(--shadow);
      background:linear-gradient(180deg, rgba(255,255,255,.07), rgba(255,255,255,.03));
      overflow:hidden;
    }
    .cardHead{padding:14px;border-bottom:1px solid var(--line);display:flex;align-items:center;justify-content:space-between;gap:10px}
    .cardHead h3{margin:0;font-size:14px;letter-spacing:-.2px}
    .pill{display:inline-flex;align-items:center;gap:8px;padding:8px 10px;border:1px solid var(--line);border-radius:999px;background:rgba(0,0,0,.12);color:var(--muted);font-size:12px}
    .dot{width:8px;height:8px;border-radius:50%}
    .dot.draft{background:var(--warn)} .dot.submitted{background:var(--good)}
    .cardBody{padding:14px}
    .row{display:grid;grid-template-columns: 120px 1fr;gap:10px;align-items:center;margin-bottom:10px}
    label{font-size:12px;color:var(--muted)}
    input, textarea{
      width:100%; border:1px solid var(--line); border-radius:12px; padding:10px 10px;
      background:rgba(0,0,0,.18); color:var(--text); outline:none;
    }
    textarea{min-height:84px;resize:vertical}
    input::placeholder, textarea::placeholder{color:rgba(166,179,200,.65)}
    .hint{color:var(--muted);font-size:12px;line-height:1.45}
    .tabs{display:flex;gap:8px;padding:10px 10px 0;border-bottom:1px solid var(--line);background:rgba(0,0,0,.06)}
    .tab{padding:10px 12px;border-radius:12px 12px 0 0;border:1px solid transparent;color:var(--muted);font-weight:900;cursor:pointer;user-select:none}
    .tab.active{color:var(--text);border-color:var(--line);border-bottom-color:transparent;background:rgba(0,0,0,.14)}
    .sheet{padding:14px}
    .meta{display:flex;flex-wrap:wrap;gap:8px;align-items:center;justify-content:space-between;margin-bottom:10px}
    .chip{display:inline-flex;align-items:center;gap:8px;padding:7px 10px;border-radius:999px;border:1px solid var(--line);background:rgba(0,0,0,.14);color:var(--muted);font-size:12px}
    table{width:100%;border-collapse:separate;border-spacing:0;border:1px solid var(--line);border-radius:14px;background:rgba(0,0,0,.10);overflow:hidden}
    thead th{padding:10px 10px;text-align:left;font-size:12px;color:var(--muted);background:rgba(0,0,0,.12);border-bottom:1px solid var(--line)}
    tbody td{padding:10px 10px;border-bottom:1px solid rgba(255,255,255,.08);vertical-align:top;font-size:13px}
    tbody tr:last-child td{border-bottom:none}
    .scoreCell{width:120px}
    .score{
      width:90px;text-align:center;font-family:var(--mono);font-weight:900;letter-spacing:.2px;
    }
    .cmt{min-height:44px;font-size:12px;padding:8px 10px}
    .kpis{display:grid;grid-template-columns: repeat(3, 1fr);gap:10px;margin-top:12px}
    @media (max-width: 720px){.kpis{grid-template-columns:1fr}}
    .kpi{border:1px solid var(--line);border-radius:14px;background:rgba(0,0,0,.12);padding:12px;display:flex;justify-content:space-between;gap:10px;align-items:flex-end}
    .kpi .lab{color:var(--muted);font-size:12px;font-weight:800}
    .kpi .val{font-family:var(--mono);font-size:18px;font-weight:900}
    .foot{display:flex;flex-wrap:wrap;gap:8px;align-items:center;justify-content:space-between;margin-top:12px}
    .toast{
      position:fixed;left:50%;bottom:18px;transform:translateX(-50%);
      padding:10px 12px;border-radius:999px;border:1px solid var(--line);
      background:rgba(0,0,0,.55);color:var(--text);font-size:12px;
      opacity:0;pointer-events:none;transition:opacity .25s ease, transform .25s ease;box-shadow:0 18px 40px rgba(0,0,0,.35);
    }
    .toast.show{opacity:1;transform:translateX(-50%) translateY(-6px)}

    @media print{
      body{background:white;color:#111}
      header,.actions,.tabs,.foot,.hint,.toast{display:none !important}
      .wrap{max-width:none;padding:0}
      .card{box-shadow:none;background:white;border:1px solid #ddd}
      .cardHead{border-bottom:1px solid #ddd}
      input,textarea{background:white;color:#111;border:1px solid #ddd}
      table{background:white;border:1px solid #ddd}
      thead th{background:#f5f5f5;border-bottom:1px solid #ddd;color:#333}
      tbody td{border-bottom:1px solid #eee;color:#111}
      .chip,.pill,.kpi{background:white;border:1px solid #ddd;color:#333}
    }
  </style>
</head>

<body>
<div class="wrap">
  <header>
    <div>
      <div class="h-title">업적/능력 평가 시트</div>
      <div class="h-sub">
        문항당 <b>10점 만점(1~10점)</b> · 업적(100) + 능력(100) = <b>총 200점 만점</b><br>
        임시저장/제출(잠금), 자동 합계·평균, CSV 내보내기, 인쇄(PDF)
      </div>
    </div>
    <div class="actions">
      <button id="btnLoad">불러오기</button>
      <button id="btnSave" class="good">임시저장</button>
      <button id="btnSubmit" class="warn">제출</button>
      <button id="btnUnlock" class="danger">제출 잠금 해제</button>
      <button id="btnExport">CSV 내보내기</button>
      <button id="btnPrint">인쇄/PDF</button>
      <button id="btnReset">새 평가(초기화)</button>
    </div>
  </header>

  <div class="grid">
    <!-- LEFT: BASIC INFO -->
    <section class="card">
      <div class="cardHead">
        <h3>기본 정보</h3>
        <div class="pill">
          <span id="statusDot" class="dot draft"></span>
          <span id="statusText">DRAFT (작성중)</span>
        </div>
      </div>
      <div class="cardBody">
        <div class="row"><label for="period">평가기간</label><input id="period" placeholder="예: 2026년 상반기" /></div>
        <div class="row"><label for="evaluator">평가자</label><input id="evaluator" placeholder="예: 홍길동" /></div>
        <div class="row"><label for="employee">피평가자</label><input id="employee" placeholder="예: 김OO" /></div>
        <div class="row"><label for="dept">부서</label><input id="dept" placeholder="예: 경영지원" /></div>
        <div class="row"><label for="pos">직급</label><input id="pos" placeholder="예: 책임/대리/과장" /></div>
        <div class="row" style="align-items:start">
          <label for="overall">총평</label>
          <textarea id="overall" placeholder="종합 코멘트(선택)"></textarea>
        </div>
        <div class="hint">
          - 점수는 <b>1~10</b>만 허용됩니다.<br>
          - <b>제출</b>하면 입력이 잠기며, 필요 시 <b>제출 잠금 해제</b>로 수정 가능합니다.<br>
          - 저장은 평가자 브라우저(localStorage)에만 됩니다(중앙 수집 기능은 별도).
        </div>
      </div>
    </section>

    <!-- RIGHT: SHEETS -->
    <section class="card">
      <div class="tabs">
        <div id="tabAch" class="tab active">업적평가(10)</div>
        <div id="tabCom" class="tab">능력평가(10)</div>
      </div>

      <div class="sheet">
        <div class="meta">
          <div style="display:flex;flex-wrap:wrap;gap:8px;align-items:center">
            <span class="chip">입력범위: 1~10</span>
            <span class="chip" id="lockChip">상태: 작성중</span>
            <span class="chip" id="validChip">입력상태: -</span>
          </div>
          <div style="display:flex;flex-wrap:wrap;gap:8px;align-items:center">
            <span class="chip">전체 평균(10점 만점): <b id="overallAvg">0.00</b></span>
            <span class="chip">전체 합계(200점 만점): <b id="overallTotal">0</b></span>
          </div>
        </div>

        <div id="sheetAch">
          <table>
            <thead>
              <tr>
                <th style="width:52px">No</th>
                <th>업적평가 항목 (설명)</th>
                <th class="scoreCell">점수</th>
                <th>코멘트(선택)</th>
              </tr>
            </thead>
            <tbody id="tbAch"></tbody>
          </table>

          <div class="kpis">
            <div class="kpi"><div><div class="lab">업적 합계</div><div class="hint">최대 100</div></div><div class="val"><span id="achTotal">0</span></div></div>
            <div class="kpi"><div><div class="lab">업적 평균</div><div class="hint">합계/10</div></div><div class="val"><span id="achAvg">0.00</span></div></div>
            <div class="kpi"><div><div class="lab">입력상태</div><div class="hint">누락/범위</div></div><div class="val"><span id="achValid">-</span></div></div>
          </div>
        </div>

        <div id="sheetCom" style="display:none">
          <table>
            <thead>
              <tr>
                <th style="width:52px">No</th>
                <th>능력평가 항목 (설명)</th>
                <th class="scoreCell">점수</th>
                <th>코멘트(선택)</th>
              </tr>
            </thead>
            <tbody id="tbCom"></tbody>
          </table>

          <div class="kpis">
            <div class="kpi"><div><div class="lab">능력 합계</div><div class="hint">최대 100</div></div><div class="val"><span id="comTotal">0</span></div></div>
            <div class="kpi"><div><div class="lab">능력 평균</div><div class="hint">합계/10</div></div><div class="val"><span id="comAvg">0.00</span></div></div>
            <div class="kpi"><div><div class="lab">입력상태</div><div class="hint">누락/범위</div></div><div class="val"><span id="comValid">-</span></div></div>
          </div>
        </div>

        <div class="foot">
          <div style="display:flex;gap:8px;flex-wrap:wrap">
            <button id="btnPrev">◀ 이전</button>
            <button id="btnNext">다음 ▶</button>
          </div>
          <div style="display:flex;gap:8px;flex-wrap:wrap">
            <button id="btnPreview" class="primary">미리보기(요약)</button>
          </div>
        </div>
      </div>
    </section>
  </div>
</div>

<div class="toast" id="toast">저장되었습니다.</div>

<script>
  // ===== 1) 문항 정의 (요청 그대로) =====
  const ACH_ITEMS = [
    { key:"A1", name:"조직목표 이해/실천", desc:"회사 및 소속부서의 목표를 이해하고 내부적인 방침과 제도 등에 긍정적 시각을 가지고 적극적으로 업무를 수행하는지 여부" },
    { key:"A2", name:"직무수행능력 향상", desc:"자기계발을 통해 직무와 관련된 능력 향상을 위해 노력하는지 여부" },
    { key:"A3", name:"도전성", desc:"업무의 위험성과 실패를 두려워하지 않으며 중도에 포기하지 않는 도전정신을 갖추고 있는지 여부" },
    { key:"A4", name:"업무처리 신뢰도", desc:"본연의 업무에 충실하며 책임있게 행동하는 등 상사로부터 신뢰를 받고 있는지 여부" },
    { key:"A5", name:"업무량(수행량)", desc:"지시 받은 일은 완벽하게 숙지하고 처리하는 등 기대 이상의 업무량을 처리하는지 여부" },
    { key:"A6", name:"업무개선도", desc:"담당업무 목표의 효과적/효율적인 달성을 위해 열정과 적극성으로 업무 개선 아이디어를 제시하고 현실화하는지 여부" },
    { key:"A7", name:"업무목표달성도", desc:"담당업무에서 요구하는 목표수준을 완벽하게 이해하고 요구하는 산출물을 달성하는지 여부" },
    { key:"A8", name:"업무효율성", desc:"담당업무를 계획적이고 일관성있게 처리하는 등 효율적인 시간 투입을 통해 원하는 목표를 달성하는지 여부" },
    { key:"A9", name:"업무이해도(프로세스)", desc:"담당업무의 핵심과업, 주요 업무내용 등 업무수행 프로세스를 완벽하게 이해하고 처리하는지 여부" },
    { key:"A10", name:"업무협조", desc:"소속부서는 물론 타부서의 업무협조 요청에 대해서도 애사심을 가지고 적극적으로 협조하여, 팀/파트 공동 목표는 물론 전사 목표에 기여하는지 여부" },
  ];

  const COM_ITEMS = [
    { key:"C1", name:"윤리경영", desc:"협력업체와 이해관계에 있어 '정직과 신뢰'를 바탕으로 직무를 윤리적·합법적으로 수행하며 공정한 거래질서 확립과 사회적 책임을 충실히 이행하는지 여부" },
    { key:"C2", name:"업무지식", desc:"본인의 일뿐만 아니라 연관된 부서의 일에 대해서도 폭넓은 지식을 보유하고 업무에 활용하는 능력이 있는지 여부" },
    { key:"C3", name:"이해판단력", desc:"상사의 지시를 바르게 이해하며 새롭고 특수한 사항에 대해서도 상황에 맞게 적절한 판단을 내릴 수 있는 능력이 있는지 여부" },
    { key:"C4", name:"개선창의력", desc:"자신의 업무에 대한 문제의식을 가지고 개선하기 위해 창의적인 아이디어를 제공하는 능력이 탁월하며 항상 자기발전을 위해 부단히 노력하는지 여부" },
    { key:"C5", name:"적극성", desc:"적극적 사고로 본인에게 주어진 일 뿐 아니라 업무 외 영역까지 폭넓게 처리하며 어떠한 장애에도 불구하고 올바로 처리하는 능력이 있는지 여부" },
    { key:"C6", name:"책임감", desc:"잘못된 일처리 결과에 대해 환경 여건이나 다른 사람을 탓하기보다는 솔직하고 책임 있는 행동으로 일을 끝까지 마무리 짓는 능력이 있는지 여부" },
    { key:"C7", name:"협조융화성", desc:"업무처리 시 관련 부서 직원의 협조를 유도하며 주어진 재량권 외의 업무는 상사와 반드시 상의하고 원활한 의사소통이 이루어 지도록 하는 능력이 있는지 여부" },
    { key:"C8", name:"신속정확성", desc:"회사의 영업정책 방향을 정확하게 숙지하고, 자신에게 부여된 업무를 신속하게 기한 내 마무리하는 능력이 있는지 여부" },
    { key:"C9", name:"문제해결능력", desc:"돌발적인 문제 발생 시 상황에 맞게 유연한 사고를 갖고 대안을 제시하여 업무를 진행하는 능력이 우수한지 여부" },
    { key:"C10", name:"추진력", desc:"자신의 의견을 소신 있게 상사에게 제언하고 추진력을 발휘해 신속히 업무를 추진하는 능력이 있는지 여부" },
  ];

  // ===== 2) 저장키/상태 =====
  const STORAGE_KEY = "EVAL_ACH_COM_200_V1";

  const state = {
    status: "draft", // draft | submitted
    period: "", evaluator: "", employee: "", dept: "", pos: "", overall: "",
    achievement: ACH_ITEMS.map(x => ({ key:x.key, score:"", comment:"" })),
    competency: COM_ITEMS.map(x => ({ key:x.key, score:"", comment:"" })),
    updatedAt: null, submittedAt: null
  };

  const $ = (id) => document.getElementById(id);

  function showToast(msg){
    const t = $("toast");
    t.textContent = msg;
    t.classList.add("show");
    clearTimeout(showToast._tm);
    showToast._tm = setTimeout(()=>t.classList.remove("show"), 1400);
  }

  function clampScore(v){
    if (v === "" || v === null || typeof v === "undefined") return "";
    const n = Number(v);
    if (!Number.isFinite(n)) return "";
    if (n < 1) return 1;
    if (n > 10) return 10;
    return Math.round(n);
  }

  function calc(list){
    let total = 0;
    for (const it of list){
      const n = Number(it.score);
      if (Number.isFinite(n)) total += n;
    }
    const avg = total / list.length;
    return { total, avg };
  }

  function validity(list){
    let missing = 0, bad = 0;
    for (const it of list){
      if (it.score === "" || it.score === null) missing++;
      else {
        const n = Number(it.score);
        if (!(n >= 1 && n <= 10)) bad++;
      }
    }
    return { ok: missing===0 && bad===0, missing, bad };
  }

  function persist(){
    state.updatedAt = new Date().toISOString();
    localStorage.setItem(STORAGE_KEY, JSON.stringify(state));
  }

  function loadSaved(){
    const raw = localStorage.getItem(STORAGE_KEY);
    if (!raw) return false;
    try{
      const p = JSON.parse(raw);
      Object.assign(state, p);
      // 방어코드
      if (!Array.isArray(state.achievement) || state.achievement.length !== 10){
        state.achievement = ACH_ITEMS.map(x => ({ key:x.key, score:"", comment:"" }));
      }
      if (!Array.isArray(state.competency) || state.competency.length !== 10){
        state.competency = COM_ITEMS.map(x => ({ key:x.key, score:"", comment:"" }));
      }
      return true;
    }catch(e){
      console.warn(e);
      return false;
    }
  }

  function setLocked(locked){
    const els = document.querySelectorAll("input, textarea");
    els.forEach(el => el.disabled = locked);

    $("btnSave").disabled = locked;
    $("btnSubmit").disabled = locked;
    $("btnUnlock").disabled = !locked;

    $("lockChip").textContent = locked ? "상태: 제출됨(잠금)" : "상태: 작성중";
    $("lockChip").style.borderColor = locked ? "rgba(82,209,183,.45)" : "rgba(255,204,102,.35)";
    $("lockChip").style.color = locked ? "rgba(238,243,255,.95)" : "rgba(166,179,200,.95)";
  }

  function updateStatusUI(){
    if (state.status === "draft"){
      $("statusDot").className = "dot draft";
      $("statusText").textContent = "DRAFT (작성중)";
      setLocked(false);
    } else {
      $("statusDot").className = "dot submitted";
      $("statusText").textContent = "SUBMITTED (제출됨)";
      setLocked(true);
    }
  }

  function updateKPIs(){
    const a = calc(state.achievement);
    const c = calc(state.competency);

    $("achTotal").textContent = a.total;
    $("achAvg").textContent = a.avg.toFixed(2);
    $("comTotal").textContent = c.total;
    $("comAvg").textContent = c.avg.toFixed(2);

    const overallTotal = a.total + c.total;          // 200점 만점
    const overallAvg = (a.avg + c.avg) / 2;          // 10점 만점 평균(업적/능력 평균의 평균)
    $("overallTotal").textContent = overallTotal;
    $("overallAvg").textContent = overallAvg.toFixed(2);

    const va = validity(state.achievement);
    const vc = validity(state.competency);
    $("achValid").textContent = va.ok ? "OK" : `누락 ${va.missing}, 오류 ${va.bad}`;
    $("comValid").textContent = vc.ok ? "OK" : `누락 ${vc.missing}, 오류 ${vc.bad}`;

    // 상단 입력상태(현재 탭 기준으로 표시)
    const active = document.querySelector("#tabAch").classList.contains("active") ? va : vc;
    $("validChip").textContent = active.ok ? "입력상태: OK" : `입력상태: 누락 ${active.missing}, 오류 ${active.bad}`;
    $("validChip").style.color = active.ok ? "var(--good)" : "var(--warn)";
  }

  function bindHeader(){
    $("period").value = state.period || "";
    $("evaluator").value = state.evaluator || "";
    $("employee").value = state.employee || "";
    $("dept").value = state.dept || "";
    $("pos").value = state.pos || "";
    $("overall").value = state.overall || "";

    const sync = () => {
      state.period = $("period").value.trim();
      state.evaluator = $("evaluator").value.trim();
      state.employee = $("employee").value.trim();
      state.dept = $("dept").value.trim();
      state.pos = $("pos").value.trim();
      state.overall = $("overall").value.trim();
      persist();
    };

    ["period","evaluator","employee","dept","pos","overall"].forEach(id=>{
      $(id).addEventListener("input", ()=>{ sync(); updateKPIs(); });
    });
  }

  function renderTable(tbodyId, items, list){
    const tb = $(tbodyId);
    tb.innerHTML = "";
    items.forEach((it, idx)=>{
      const tr = document.createElement("tr");

      const tdNo = document.createElement("td");
      tdNo.textContent = String(idx+1);
      tdNo.style.color = "rgba(166,179,200,.95)";
      tdNo.style.fontFamily = "var(--mono)";
      tr.appendChild(tdNo);

      const tdItem = document.createElement("td");
      tdItem.innerHTML =
        `<div style="display:flex;flex-direction:column;gap:6px">
           <div><b style="font-family:var(--mono)">${it.key}</b> <span style="font-weight:900;margin-left:6px">${it.name}</span></div>
           <div style="color:rgba(166,179,200,.95);font-size:12px;line-height:1.35">${it.desc}</div>
         </div>`;
      tr.appendChild(tdItem);

      const tdScore = document.createElement("td");
      tdScore.className = "scoreCell";
      const inp = document.createElement("input");
      inp.className = "score";
      inp.type = "number"; inp.min = "1"; inp.max = "10"; inp.step = "1";
      inp.placeholder = "1~10";
      inp.value = list[idx].score;
      inp.addEventListener("input", ()=>{
        const v = inp.value==="" ? "" : clampScore(inp.value);
        list[idx].score = v==="" ? "" : String(v);
        inp.value = list[idx].score;
        persist();
        updateKPIs();
      });
      tdScore.appendChild(inp);
      tr.appendChild(tdScore);

      const tdC = document.createElement("td");
      const ta = document.createElement("textarea");
      ta.className = "cmt";
      ta.placeholder = "필요 시 간단 코멘트";
      ta.value = list[idx].comment || "";
      ta.addEventListener("input", ()=>{
        list[idx].comment = ta.value;
        persist();
      });
      tdC.appendChild(ta);
      tr.appendChild(tdC);

      tb.appendChild(tr);
    });
  }

  function setTab(which){
    const isAch = which === "ach";
    $("tabAch").classList.toggle("active", isAch);
    $("tabCom").classList.toggle("active", !isAch);
    $("sheetAch").style.display = isAch ? "" : "none";
    $("sheetCom").style.display = isAch ? "none" : "";
    updateKPIs();
  }

  function validateBeforeSubmit(){
    const required = [
      ["period","평가기간"],
      ["evaluator","평가자"],
      ["employee","피평가자"],
    ];
    const miss = [];
    for (const [id, name] of required){
      if (!$(id).value.trim()) miss.push(name);
    }
    if (miss.length){
      alert("제출 전에 기본 정보를 입력해 주세요:\n- " + miss.join("\n- "));
      return false;
    }

    const va = validity(state.achievement);
    const vc = validity(state.competency);
    if (!va.ok || !vc.ok){
      alert(
        "제출할 수 없습니다.\n" +
        `업적평가: 누락 ${va.missing}, 오류 ${va.bad}\n` +
        `능력평가: 누락 ${vc.missing}, 오류 ${vc.bad}\n\n` +
        "모든 항목을 1~10점으로 입력해 주세요."
      );
      return false;
    }
    return true;
  }

  function doSubmit(){
    if (!validateBeforeSubmit()) return;
    if (!confirm("제출하면 입력이 잠깁니다. 제출하시겠습니까?")) return;
    state.status = "submitted";
    state.submittedAt = new Date().toISOString();
    persist();
    updateStatusUI();
    showToast("제출 완료(잠금)");
  }

  function doUnlock(){
    if (state.status !== "submitted"){ showToast("제출 상태가 아닙니다"); return; }
    if (!confirm("제출 잠금을 해제하면 수정이 가능해집니다. 해제하시겠습니까?")) return;
    state.status = "draft";
    state.submittedAt = null;
    persist();
    updateStatusUI();
    showToast("잠금 해제됨");
  }

  function doReset(){
    if (!confirm("새 평가로 초기화할까요? (현재 브라우저 저장 데이터는 덮어씌워집니다)")) return;
    state.status = "draft";
    state.period=""; state.evaluator=""; state.employee=""; state.dept=""; state.pos=""; state.overall="";
    state.achievement = ACH_ITEMS.map(x => ({ key:x.key, score:"", comment:"" }));
    state.competency = COM_ITEMS.map(x => ({ key:x.key, score:"", comment:"" }));
    state.updatedAt = new Date().toISOString();
    state.submittedAt = null;
    persist();
    bindHeader();
    renderTable("tbAch", ACH_ITEMS, state.achievement);
    renderTable("tbCom", COM_ITEMS, state.competency);
    updateStatusUI();
    updateKPIs();
    showToast("초기화 완료");
  }

  function doSave(){
    persist();
    showToast("임시저장 완료");
  }

  function doLoad(){
    const ok = loadSaved();
    if (!ok){ showToast("저장된 평가가 없습니다"); return; }
    bindHeader();
    renderTable("tbAch", ACH_ITEMS, state.achievement);
    renderTable("tbCom", COM_ITEMS, state.competency);
    updateStatusUI();
    updateKPIs();
    showToast("불러오기 완료");
  }

  function doPreview(){
    const a = calc(state.achievement);
    const c = calc(state.competency);
    const total = a.total + c.total;
    const avg = (a.avg + c.avg) / 2;
    const lines = [];
    lines.push(`평가기간: ${state.period || "-"}`);
    lines.push(`평가자: ${state.evaluator || "-"}`);
    lines.push(`피평가자: ${state.employee || "-"} (${state.dept || "-"} / ${state.pos || "-"})`);
    lines.push(`상태: ${state.status.toUpperCase()}`);
    lines.push("");
    lines.push(`[업적] 합계 ${a.total}/100, 평균 ${a.avg.toFixed(2)}/10`);
    lines.push(`[능력] 합계 ${c.total}/100, 평균 ${c.avg.toFixed(2)}/10`);
    lines.push("");
    lines.push(`[전체] 합계 ${total}/200, 평균 ${avg.toFixed(2)}/10`);
    if (state.overall) { lines.push(""); lines.push(`[총평] ${state.overall}`); }
    alert(lines.join("\n"));
  }

  function doExportCSV(){
    const a = calc(state.achievement);
    const c = calc(state.competency);
    const total = a.total + c.total;
    const avg = (a.avg + c.avg) / 2;

    const header = [
      "period","evaluator","employee","dept","position","status",
      "sheet","itemKey","itemName","itemDesc","score","itemComment",
      "sheetTotal","sheetAvg",
      "overallTotal(200)","overallAvg(10)",
      "overallComment",
      "updatedAt","submittedAt"
    ];

    const rows = [header];

    ACH_ITEMS.forEach((it, i)=>{
      rows.push([
        state.period, state.evaluator, state.employee, state.dept, state.pos, state.status,
        "achievement", it.key, it.name, it.desc,
        state.achievement[i].score,
        (state.achievement[i].comment||"").replaceAll("\n"," "),
        a.total, a.avg.toFixed(2),
        total, avg.toFixed(2),
        (state.overall||"").replaceAll("\n"," "),
        state.updatedAt||"", state.submittedAt||""
      ]);
    });

    COM_ITEMS.forEach((it, i)=>{
      rows.push([
        state.period, state.evaluator, state.employee, state.dept, state.pos, state.status,
        "competency", it.key, it.name, it.desc,
        state.competency[i].score,
        (state.competency[i].comment||"").replaceAll("\n"," "),
        c.total, c.avg.toFixed(2),
        total, avg.toFixed(2),
        (state.overall||"").replaceAll("\n"," "),
        state.updatedAt||"", state.submittedAt||""
      ]);
    });

    const csv = rows.map(r => r.map(cell => {
      const s = String(cell ?? "");
      if (s.includes('"') || s.includes(",") || s.includes("\n")) return `"${s.replaceAll('"','""')}"`;
      return s;
    }).join(",")).join("\n");

    const blob = new Blob([csv], { type:"text/csv;charset=utf-8;" });
    const url = URL.createObjectURL(blob);

    const aTag = document.createElement("a");
    const safeEmp = (state.employee || "employee").replace(/[^\w가-힣-]/g,"_");
    const safePeriod = (state.period || "period").replace(/[^\w가-힣-]/g,"_");
    aTag.href = url;
    aTag.download = `evaluation_${safePeriod}_${safeEmp}.csv`;
    document.body.appendChild(aTag);
    aTag.click();
    document.body.removeChild(aTag);
    URL.revokeObjectURL(url);

    showToast("CSV 다운로드 시작");
  }

  // ===== 3) 초기화/이벤트 =====
  function init(){
    loadSaved(); // 있으면 로드
    bindHeader();
    renderTable("tbAch", ACH_ITEMS, state.achievement);
    renderTable("tbCom", COM_ITEMS, state.competency);
    updateStatusUI();
    updateKPIs();
    setTab("ach");

    $("tabAch").addEventListener("click", ()=>setTab("ach"));
    $("tabCom").addEventListener("click", ()=>setTab("com"));
    $("btnPrev").addEventListener("click", ()=>{
      const achActive = $("tabAch").classList.contains("active");
      setTab(achActive ? "com" : "ach");
    });
    $("btnNext").addEventListener("click", ()=>{
      const achActive = $("tabAch").classList.contains("active");
      setTab(achActive ? "com" : "ach");
    });

    $("btnSave").addEventListener("click", doSave);
    $("btnLoad").addEventListener("click", doLoad);
    $("btnSubmit").addEventListener("click", doSubmit);
    $("btnUnlock").addEventListener("click", doUnlock);
    $("btnReset").addEventListener("click", doReset);
    $("btnExport").addEventListener("click", doExportCSV);
    $("btnPrint").addEventListener("click", ()=>window.print());
    $("btnPreview").addEventListener("click", doPreview);
  }

  init();
</script>
</body>
</html>
