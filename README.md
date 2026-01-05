<!doctype html>
<html lang="ko">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>업적/능력 평가 시트 (GitHub Pages)</title>
  <style>
    :root{
      --bg:#0b1220; --muted:#9aa7bd; --text:#eaf0ff; --line:rgba(255,255,255,.12);
      --good:#52d1b7; --warn:#ffcc66; --bad:#ff6b6b; --btn:#1b2b54; --btn2:#233562;
      --shadow: 0 20px 50px rgba(0,0,0,.35);
      --radius:16px; --mono: ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, "Liberation Mono","Courier New", monospace;
      --sans: ui-sans-serif, system-ui, -apple-system, Segoe UI, Roboto, "Noto Sans KR","Apple SD Gothic Neo","Malgun Gothic", Arial,"Helvetica Neue", Helvetica, sans-serif;
    }
    *{box-sizing:border-box}
    body{
      margin:0; font-family:var(--sans); color:var(--text); min-height:100vh;
      background:
        radial-gradient(1100px 600px at 30% -10%, rgba(122,167,255,.25), transparent 60%),
        radial-gradient(900px 500px at 110% 20%, rgba(82,209,183,.18), transparent 55%),
        linear-gradient(180deg, #070c17, var(--bg));
    }
    .wrap{max-width:1120px;margin:0 auto;padding:28px 18px 60px}
    header{display:flex;flex-wrap:wrap;gap:14px;align-items:flex-end;justify-content:space-between;margin-bottom:18px}
    .brand{display:flex;flex-direction:column;gap:6px}
    .title{font-size:22px;font-weight:800;letter-spacing:-.2px}
    .subtitle{color:var(--muted);font-size:13px;line-height:1.4}
    .topActions{display:flex;flex-wrap:wrap;gap:8px;align-items:center}
    button{
      border:1px solid var(--line);
      background:linear-gradient(180deg, var(--btn), var(--btn2));
      color:var(--text); padding:10px 12px; border-radius:12px;
      font-weight:700; cursor:pointer; box-shadow: 0 10px 24px rgba(0,0,0,.25);
      transition: transform .06s ease, filter .2s ease; white-space:nowrap;
    }
    button:hover{filter:brightness(1.07)} button:active{transform:translateY(1px)}
    button.secondary{background:transparent;box-shadow:none}
    button.danger{background:linear-gradient(180deg, rgba(255,107,107,.22), rgba(255,107,107,.10));border-color: rgba(255,107,107,.35)}
    button.good{background:linear-gradient(180deg, rgba(82,209,183,.22), rgba(82,209,183,.10));border-color: rgba(82,209,183,.35)}
    button.warn{background:linear-gradient(180deg, rgba(255,204,102,.22), rgba(255,204,102,.10));border-color: rgba(255,204,102,.35)}
    .grid{display:grid;grid-template-columns: 360px 1fr;gap:14px;align-items:start}
    @media (max-width: 980px){.grid{grid-template-columns:1fr}}
    .card{
      background:linear-gradient(180deg, rgba(255,255,255,.06), rgba(255,255,255,.03));
      border:1px solid var(--line); border-radius:var(--radius); box-shadow: var(--shadow); overflow:hidden;
    }
    .cardHead{padding:14px 14px 10px;border-bottom:1px solid var(--line);display:flex;gap:10px;align-items:center;justify-content:space-between}
    .cardHead h3{margin:0;font-size:14px;letter-spacing:-.2px}
    .cardBody{padding:14px}
    .fieldRow{display:grid;grid-template-columns: 120px 1fr;gap:10px;align-items:center;margin-bottom:10px}
    .fieldRow label{font-size:12px;color:var(--muted)}
    input, textarea{
      width:100%; padding:10px 10px; border-radius:12px; border:1px solid var(--line);
      background: rgba(0,0,0,.18); color:var(--text); outline:none;
    }
    textarea{min-height:80px;resize:vertical}
    input::placeholder, textarea::placeholder{color:rgba(154,167,189,.65)}
    .hint{color:var(--muted);font-size:12px;line-height:1.45}
    .statusPill{display:flex;align-items:center;gap:8px;padding:8px 10px;border-radius:999px;border:1px solid var(--line);background: rgba(0,0,0,.12);font-size:12px;color:var(--muted)}
    .dot{width:8px;height:8px;border-radius:50%} .dot.draft{background:var(--warn)} .dot.submitted{background:var(--good)}
    .tabs{display:flex;gap:8px;padding:10px 10px 0;border-bottom:1px solid var(--line);background: rgba(0,0,0,.06)}
    .tab{padding:10px 12px;border-radius:12px 12px 0 0;border:1px solid transparent;color:var(--muted);font-weight:800;cursor:pointer;user-select:none}
    .tab.active{color:var(--text);border-color: var(--line);border-bottom-color: transparent;background: rgba(0,0,0,.12)}
    .sheetWrap{padding:14px}
    .sheetHead{display:flex;flex-wrap:wrap;gap:10px;align-items:center;justify-content:space-between;margin-bottom:10px}
    .sheetHead .meta{display:flex;flex-wrap:wrap;gap:8px;align-items:center;color:var(--muted);font-size:12px}
    .chip{display:inline-flex;align-items:center;gap:6px;padding:6px 10px;border-radius:999px;background: rgba(0,0,0,.18);border:1px solid var(--line);color:var(--muted)}
    table{width:100%;border-collapse:separate;border-spacing:0;border:1px solid var(--line);border-radius:14px;background: rgba(0,0,0,.10);overflow:hidden}
    thead th{text-align:left;padding:10px 10px;font-size:12px;color:var(--muted);border-bottom:1px solid var(--line);background: rgba(0,0,0,.12)}
    tbody td{padding:10px 10px;border-bottom:1px solid rgba(255,255,255,.08);vertical-align:top;font-size:13px}
    tbody tr:last-child td{border-bottom:none}
    .scoreCell{width:120px}
    .scoreInput{width:90px;text-align:center;font-family:var(--mono);font-weight:900;letter-spacing:.2px}
    .miniComment{min-height:42px;font-size:12px;padding:8px 10px}
    .summaryBar{display:grid;grid-template-columns: repeat(3, 1fr);gap:10px;margin-top:12px}
    @media (max-width: 700px){.summaryBar{grid-template-columns:1fr}}
    .kpi{border:1px solid var(--line);border-radius:14px;padding:12px;background: rgba(0,0,0,.12);display:flex;align-items:flex-end;justify-content:space-between;gap:10px}
    .kpi .label{color:var(--muted);font-size:12px;font-weight:700}
    .kpi .val{font-size:18px;font-weight:900;font-family:var(--mono)}
    .kpi .unit{color:var(--muted);font-size:12px;margin-left:6px}
    .footerActions{display:flex;flex-wrap:wrap;gap:8px;margin-top:12px;align-items:center;justify-content:space-between}
    .leftBtns, .rightBtns{display:flex;flex-wrap:wrap;gap:8px;align-items:center}
    .toast{position:fixed;left:50%;bottom:18px;transform:translateX(-50%);padding:10px 12px;border-radius:999px;border:1px solid var(--line);background: rgba(0,0,0,.55);color:var(--text);font-size:12px;opacity:0;pointer-events:none;transition:opacity .25s ease, transform .25s ease;box-shadow: 0 18px 40px rgba(0,0,0,.35)}
    .toast.show{opacity:1;transform:translateX(-50%) translateY(-6px)}
    @media print{
      body{background:white;color:#111}
      .wrap{max-width:none;padding:0}
      header, .topActions, .tabs, .footerActions, .hint, .toast{display:none !important}
      .card{box-shadow:none;border:1px solid #ddd;background:white}
      .cardHead{border-bottom:1px solid #ddd}
      input, textarea{border:1px solid #ddd;background:white;color:#111}
      table{border:1px solid #ddd;background:white}
      thead th{background:#f5f5f5;border-bottom:1px solid #ddd;color:#333}
      tbody td{border-bottom:1px solid #eee;color:#111}
      .chip,.statusPill,.kpi{border:1px solid #ddd;background:white;color:#333}
    }
  </style>
</head>
<body>
  <div class="wrap">
    <header>
      <div class="brand">
        <div class="title">업적/능력 평가 시트 (GitHub Pages)</div>
        <div class="subtitle">
          문항당 <b>10점 만점(1~10 입력)</b>. 업적(100) + 능력(100) = <b>총 200점 만점</b>.<br>
          임시저장/제출(잠금), 자동 합계·평균, CSV 내보내기, 인쇄(PDF) 지원.<br>
          ※ 저장은 평가자 브라우저(localStorage)에만 됩니다(관리자 자동 취합은 별도 기능 필요).
        </div>
      </div>
      <div class="topActions">
        <button class="secondary" id="btnNew">새 평가(초기화)</button>
        <button class="secondary" id="btnLoad">불러오기</button>
        <button class="secondary" id="btnExport">CSV 내보내기</button>
        <button class="secondary" id="btnPrint">인쇄/PDF</button>
      </div>
    </header>

    <div class="grid">
      <section class="card" aria-label="기본정보">
        <div class="cardHead">
          <h3>기본 정보</h3>
          <div class="statusPill">
            <span class="dot draft" id="statusDot"></span>
            <span id="statusText">DRAFT (작성중)</span>
          </div>
        </div>
        <div class="cardBody">
          <div class="fieldRow">
            <label for="period">평가기간</label>
            <input id="period" placeholder="예: 2026-H1, 2026년 상반기" />
          </div>
          <div class="fieldRow">
            <label for="evaluator">평가자</label>
            <input id="evaluator" placeholder="예: 홍길동" />
          </div>
          <div class="fieldRow">
            <label for="employeeName">피평가자</label>
            <input id="employeeName" placeholder="예: 김OO" />
          </div>
          <div class="fieldRow">
            <label for="dept">부서</label>
            <input id="dept" placeholder="예: 경영지원" />
          </div>
          <div class="fieldRow">
            <label for="position">직급</label>
            <input id="position" placeholder="예: 책임/대리/과장" />
          </div>

          <div class="fieldRow" style="align-items:start">
            <label for="overallComment">총평</label>
            <textarea id="overallComment" placeholder="종합 코멘트(선택)"></textarea>
          </div>

          <div class="hint">
            <b>제출</b>하면 점수 입력이 잠깁니다. (필요 시 ‘제출 잠금 해제’로 수정 가능)<br/>
            점수는 <b>1~10</b>만 허용합니다. 제출 시 누락이 있으면 제출되지 않습니다.
          </div>

          <div style="height:12px"></div>

          <div class="footerActions">
            <div class="leftBtns">
              <button class="good" id="btnSave">임시저장</button>
              <button class="warn" id="btnSubmit">제출</button>
            </div>
            <div class="rightBtns">
              <button class="danger" id="btnUnlock">제출 잠금 해제</button>
            </div>
          </div>
        </div>
      </section>

      <section class="card" aria-label="평가시트">
        <div class="tabs">
          <div class="tab active" id="tabAch">업적평가(10)</div>
          <div class="tab" id="tabCom">능력평가(10)</div>
        </div>

        <div class="sheetWrap">
          <div class="sheetHead">
            <div class="meta">
              <span class="chip">입력범위: 1~10</span>
              <span class="chip" id="lockChip">상태: 작성중</span>
              <span class="chip">자동합계/평균</span>
            </div>
            <div class="meta">
              <span class="chip">전체 평균(10점 만점): <b id="overallAvg">0.00</b></span>
              <span class="chip">전체 합계(200점 만점): <b id="overallTotal">0</b></span>
            </div>
          </div>

          <div id="sheetAchievement">
            <table>
              <thead>
                <tr>
                  <th style="width:52px">No</th>
                  <th>업적평가 항목 (설명 포함)</th>
                  <th class="scoreCell">점수(1~10)</th>
                  <th>항목 코멘트(선택)</th>
                </tr>
              </thead>
              <tbody id="tbodyAch"></tbody>
            </table>

            <div class="summaryBar">
              <div class="kpi">
                <div>
                  <div class="label">업적 합계</div>
                  <div class="hint">10개 항목 합산(최대 100)</div>
                </div>
                <div class="val"><span id="achTotal">0</span><span class="unit">점</span></div>
              </div>
              <div class="kpi">
                <div>
                  <div class="label">업적 평균</div>
                  <div class="hint">합계 / 10</div>
                </div>
                <div class="val"><span id="achAvg">0.00</span><span class="unit">점</span></div>
              </div>
              <div class="kpi">
                <div>
                  <div class="label">입력 상태</div>
                  <div class="hint">누락/범위 체크</div>
                </div>
                <div class="val"><span id="achValid">OK</span></div>
              </div>
            </div>
          </div>

          <div id="sheetCompetency" style="display:none">
            <table>
              <thead>
                <tr>
                  <th style="width:52px">No</th>
                  <th>능력평가 항목 (설명 포함)</th>
                  <th class="scoreCell">점수(1~10)</th>
                  <th>항목 코멘트(선택)</th>
                </tr>
              </thead>
              <tbody id="tbodyCom"></tbody>
            </table>

            <div class="summaryBar">
              <div class="kpi">
                <div>
                  <div class="label">능력 합계</div>
                  <div class="hint">10개 항목 합산(최대 100)</div>
                </div>
                <div class="val"><span id="comTotal">0</span><span class="unit">점</span></div>
              </div>
              <div class="kpi">
                <div>
                  <div class="label">능력 평균</div>
                  <div class="hint">합계 / 10</div>
                </div>
                <div class="val"><span id="comAvg">0.00</span><span class="unit">점</span></div>
              </div>
              <div class="kpi">
                <div>
                  <div class="label">입력 상태</div>
                  <div class="hint">누락/범위 체크</div>
                </div>
                <div class="val"><span id="comValid">OK</span></div>
              </div>
            </div>
          </div>

          <div class="footerActions">
            <div class="leftBtns">
              <button class="secondary" id="btnPrev">◀ 이전 탭</button>
              <button class="secondary" id="btnNext">다음 탭 ▶</button>
            </div>
            <div class="rightBtns">
              <button class="secondary" id="btnPreview">미리보기(요약)</button>
            </div>
          </div>
        </div>
      </section>
    </div>
  </div>

  <div class="toast" id="toast">저장되었습니다.</div>

  <script>
    // ====== 평가 항목(요청 반영) ======
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

    // GitHub Pages에서 동일하게 동작(평가자별로 각자 브라우저에 저장)
    const STORAGE_KEY = "EVAL_SHEET_GHPAGES_V1";

    const state = {
      status: "draft", // draft | submitted
      period: "",
      evaluator: "",
      employeeName: "",
      dept: "",
      position: "",
      overallComment: "",
      achievement: ACH_ITEMS.map(it => ({ key: it.key, score: "", comment: "" })),
      competency: COM_ITEMS.map(it => ({ key: it.key, score: "", comment: "" })),
      updatedAt: null,
      submittedAt: null,
    };

    const $ = (id) => document.getElementById(id);

    function toast(msg){
      const t = $("toast");
      t.textContent = msg;
      t.classList.add("show");
      clearTimeout(toast._tm);
      toast._tm = setTimeout(()=>t.classList.remove("show"), 1400);
    }

    function clampScore(v){
      if (v === "" || v === null || typeof v === "undefined") return "";
      const n = Number(v);
      if (!Number.isFinite(n)) return "";
      if (n < 1) return 1;
      if (n > 10) return 10;
      return Math.round(n);
    }

    function scoreStatus(list){
      let missing = 0, outOfRange = 0;
      for (const it of list){
        if (it.score === "" || it.score === null) missing++;
        else {
          const n = Number(it.score);
          if (!(n >= 1 && n <= 10)) outOfRange++;
        }
      }
      return { ok: missing === 0 && outOfRange === 0, missing, outOfRange };
    }

    function calcTotals(list){
      let total = 0;
      let filled = 0;
      for (const it of list){
        const n = Number(it.score);
        if (Number.isFinite(n)){
          total += n;
          filled++;
        }
      }
      const avg = filled > 0 ? total / list.length : 0;
      return { total, avg };
    }

    function setLockedUI(locked){
      document.querySelectorAll("input.scoreInput, textarea.miniComment, input#period, input#evaluator, input#employeeName, input#dept, input#position, textarea#overallComment")
        .forEach(el => el.disabled = locked);

      $("btnSave").disabled = locked;
      $("btnSubmit").disabled = locked;
      $("btnUnlock").disabled = !locked;

      $("lockChip").textContent = locked ? "상태: 제출됨(잠금)" : "상태: 작성중";
      $("lockChip").style.borderColor = locked ? "rgba(82,209,183,.45)" : "rgba(255,204,102,.35)";
      $("lockChip").style.color = locked ? "rgba(234,240,255,.95)" : "rgba(154,167,189,.95)";
    }

    function updateStatusUI(){
      const dot = $("statusDot");
      const text = $("statusText");
      if (state.status === "draft"){
        dot.className = "dot draft";
        text.textContent = "DRAFT (작성중)";
        setLockedUI(false);
      } else {
        dot.className = "dot submitted";
        text.textContent = "SUBMITTED (제출됨)";
        setLockedUI(true);
      }
    }

    function updateKPIs(){
      const ach = calcTotals(state.achievement);
      const com = calcTotals(state.competency);

      $("achTotal").textContent = ach.total;
      $("achAvg").textContent = ach.avg.toFixed(2);
      $("comTotal").textContent = com.total;
      $("comAvg").textContent = com.avg.toFixed(2);

      const overallTotal = ach.total + com.total; // 200점 만점
      const overallAvg = (ach.avg + com.avg) / 2; // 10점 만점 평균
      $("overallTotal").textContent = overallTotal;
      $("overallAvg").textContent = overallAvg.toFixed(2);

      const vA = scoreStatus(state.achievement);
      const vC = scoreStatus(state.competency);

      $("achValid").textContent = vA.ok ? "OK" : `누락 ${vA.missing}, 범위오류 ${vA.outOfRange}`;
      $("achValid").style.color = vA.ok ? "var(--good)" : "var(--warn)";
      $("comValid").textContent = vC.ok ? "OK" : `누락 ${vC.missing}, 범위오류 ${vC.outOfRange}`;
      $("comValid").style.color = vC.ok ? "var(--good)" : "var(--warn)";
    }

    function persist(){
      state.updatedAt = new Date().toISOString();
      localStorage.setItem(STORAGE_KEY, JSON.stringify(state));
    }

    function bindHeaderFields(){
      $("period").value = state.period;
      $("evaluator").value = state.evaluator;
      $("employeeName").value = state.employeeName;
      $("dept").value = state.dept;
      $("position").value = state.position;
      $("overallComment").value = state.overallComment;

      const sync = () => {
        state.period = $("period").value.trim();
        state.evaluator = $("evaluator").value.trim();
        state.employeeName = $("employeeName").value.trim();
        state.dept = $("dept").value.trim();
        state.position = $("position").value.trim();
        state.overallComment = $("overallComment").value.trim();
        persist();
        updateKPIs();
      };

      ["period","evaluator","employeeName","dept","position","overallComment"].forEach(id=>{
        $(id).addEventListener("input", sync);
      });
    }

    function renderTable(tbodyId, items, stateList){
      const tb = $(tbodyId);
      tb.innerHTML = "";
      items.forEach((it, idx)=>{
        const tr = document.createElement("tr");

        const tdNo = document.createElement("td");
        tdNo.textContent = (idx+1);
        tdNo.style.color = "rgba(154,167,189,.9)";
        tdNo.style.fontFamily = "var(--mono)";
        tr.appendChild(tdNo);

        const tdName = document.createElement("td");
        tdName.innerHTML =
          `<div style="display:flex;flex-direction:column;gap:6px">
             <div>
               <b style="font-family:var(--mono); color:rgba(234,240,255,.95)">${it.key}</b>
               <span style="margin-left:6px;font-weight:900">${it.name}</span>
             </div>
             <div style="color:rgba(154,167,189,.95);font-size:12px;line-height:1.35">${it.desc}</div>
           </div>`;
        tr.appendChild(tdName);

        const tdScore = document.createElement("td");
        tdScore.className = "scoreCell";
        const inp = document.createElement("input");
        inp.className = "scoreInput";
        inp.type = "number"; inp.min = "1"; inp.max = "10"; inp.step = "1";
        inp.placeholder = "1~10";
        inp.value = stateList[idx].score;
        inp.addEventListener("input", () => {
          const v = inp.value === "" ? "" : clampScore(inp.value);
          stateList[idx].score = v === "" ? "" : String(v);
          inp.value = stateList[idx].score;
          persist();
          updateKPIs();
        });
        tdScore.appendChild(inp);
        tr.appendChild(tdScore);

        const tdC = document.createElement("td");
        const ta = document.createElement("textarea");
        ta.className = "miniComment";
        ta.placeholder = "필요 시 간단 코멘트";
        ta.value = stateList[idx].comment || "";
        ta.addEventListener("input", ()=>{
          stateList[idx].comment = ta.value;
          persist();
        });
        tdC.appendChild(ta);
        tr.appendChild(tdC);

        tb.appendChild(tr);
      });
    }

    function renderAll(){
      renderTable("tbodyAch", ACH_ITEMS, state.achievement);
      renderTable("tbodyCom", COM_ITEMS, state.competency);
      updateStatusUI();
      updateKPIs();
    }

    function save(){
      persist();
      toast("임시저장 완료");
    }

    function load(){
      const raw = localStorage.getItem(STORAGE_KEY);
      if (!raw){ toast("저장된 평가가 없습니다"); return; }
      try{
        const parsed = JSON.parse(raw);
        Object.assign(state, parsed);

        if (!Array.isArray(state.achievement) || state.achievement.length !== 10){
          state.achievement = ACH_ITEMS.map(it => ({ key: it.key, score: "", comment: "" }));
        }
        if (!Array.isArray(state.competency) || state.competency.length !== 10){
          state.competency = COM_ITEMS.map(it => ({ key: it.key, score: "", comment: "" }));
        }

        bindHeaderFields();
        renderAll();
        toast("불러오기 완료");
      }catch(e){
        console.error(e);
        toast("불러오기 실패(데이터 손상)");
      }
    }

    function resetAll(){
      if (!confirm("새 평가로 초기화할까요? (현재 브라우저 저장 데이터는 덮어씌워집니다)")) return;

      state.status = "draft";
      state.period = ""; state.evaluator = ""; state.employeeName = ""; state.dept = ""; state.position = "";
      state.overallComment = "";
      state.achievement = ACH_ITEMS.map(it => ({ key: it.key, score: "", comment: "" }));
      state.competency = COM_ITEMS.map(it => ({ key: it.key, score: "", comment: "" }));
      state.updatedAt = new Date().toISOString();
      state.submittedAt = null;

      persist();
      bindHeaderFields();
      renderAll();
      toast("초기화 완료");
    }

    function validateBeforeSubmit(){
      const vA = scoreStatus(state.achievement);
      const vC = scoreStatus(state.competency);

      const requiredHeader = [
        { id:"period", name:"평가기간" },
        { id:"evaluator", name:"평가자" },
        { id:"employeeName", name:"피평가자" },
      ];
      const missingHeader = [];
      requiredHeader.forEach(f=>{ if (!$(f.id).value.trim()) missingHeader.push(f.name); });

      if (missingHeader.length){
        alert(`제출 전에 기본 정보를 입력해 주세요:\n- ${missingHeader.join("\n- ")}`);
        return false;
      }

      if (!vA.ok || !vC.ok){
        alert(
          `제출할 수 없습니다.\n`+
          `업적평가: 누락 ${vA.missing}, 범위오류 ${vA.outOfRange}\n`+
          `능력평가: 누락 ${vC.missing}, 범위오류 ${vC.outOfRange}\n\n`+
          `모든 항목을 1~10점으로 입력해 주세요.`
        );
        return false;
      }
      return true;
    }

    function submit(){
      if (!validateBeforeSubmit()) return;
      if (!confirm("제출하면 점수 입력이 잠깁니다. 제출하시겠습니까?")) return;

      state.status = "submitted";
      state.submittedAt = new Date().toISOString();
      persist();
      updateStatusUI();
      toast("제출 완료(잠금)");
    }

    function unlock(){
      if (state.status !== "submitted"){ toast("현재 제출 상태가 아닙니다"); return; }
      if (!confirm("제출 잠금을 해제하면 수정이 가능해집니다. 해제하시겠습니까?")) return;

      state.status = "draft";
      st
