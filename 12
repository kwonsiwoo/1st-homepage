import { useState } from "react";

// ── 아이콘 ──────────────────────────────────────────────────────────────────
const Zap = () => (
  <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2.5" strokeLinecap="round" strokeLinejoin="round" className="w-4 h-4">
    <polygon points="13 2 3 14 12 14 11 22 21 10 12 10 13 2"/>
  </svg>
);
const ArrowRight = () => (
  <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round" className="w-4 h-4">
    <line x1="5" y1="12" x2="19" y2="12"/><polyline points="12 5 19 12 12 19"/>
  </svg>
);
const Check = ({ small }) => (
  <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2.5" strokeLinecap="round" strokeLinejoin="round" className={small ? "w-3 h-3" : "w-4 h-4"}>
    <polyline points="20 6 9 18 4 13"/>
  </svg>
);
const Menu = () => (
  <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round" className="w-5 h-5">
    <line x1="3" y1="6" x2="21" y2="6"/><line x1="3" y1="12" x2="21" y2="12"/><line x1="3" y1="18" x2="21" y2="18"/>
  </svg>
);
const X = () => (
  <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round" className="w-5 h-5">
    <line x1="18" y1="6" x2="6" y2="18"/><line x1="6" y1="6" x2="18" y2="18"/>
  </svg>
);
const Sparkles = () => (
  <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round" className="w-3.5 h-3.5">
    <path d="M12 3l1.5 4.5L18 9l-4.5 1.5L12 15l-1.5-4.5L6 9l4.5-1.5z"/><path d="M5 3l.75 2.25L8 6l-2.25.75L5 9l-.75-2.25L2 6l2.25-.75z"/><path d="M19 15l.75 2.25L22 18l-2.25.75L19 21l-.75-2.25L16 18l2.25-.75z"/>
  </svg>
);

// ── 데이터 ──────────────────────────────────────────────────────────────────
const SITE_TYPES = [
  { id: "landing",   label: "랜딩페이지",          emoji: "🚀", basePrice: 290000, description: "단일 페이지 · 제품/서비스 소개 · CTA 중심" },
  { id: "business",  label: "비즈니스 홈페이지",    emoji: "🏢", basePrice: 590000, description: "3~5 페이지 · 회사소개 · 서비스 · 문의" },
  { id: "portfolio", label: "포트폴리오/개인 브랜딩", emoji: "🎨", basePrice: 390000, description: "작업물 전시 · 이력 소개 · 블로그 연동" },
  { id: "shop",      label: "쇼핑몰/이커머스",       emoji: "🛍️", basePrice: 990000, description: "상품 관리 · 결제 연동 · 주문 관리" },
];
const FEATURES = [
  { id: "reservation", label: "예약 시스템",           price: 150000, description: "캘린더 기반 예약 및 알림 기능" },
  { id: "board",       label: "게시판/블로그",          price: 100000, description: "공지사항, 뉴스, 블로그 글 관리" },
  { id: "multilang",   label: "다국어 지원",            price: 120000, description: "한국어 + 영어 (또는 추가 언어)" },
  { id: "analytics",   label: "방문자 분석 대시보드",   price:  80000, description: "Google Analytics 연동" },
  { id: "chatbot",     label: "AI 챗봇 상담",           price: 200000, description: "24시간 자동 응대 AI 챗봇 연동" },
  { id: "seo",         label: "SEO 최적화 패키지",      price:  90000, description: "메타태그, 사이트맵, 구조화 데이터" },
  { id: "admin",       label: "관리자 CMS",             price: 180000, description: "콘텐츠 직접 수정 가능한 관리자 패널" },
  { id: "kakao",       label: "카카오 채널 연동",        price:  50000, description: "카카오톡 상담 버튼 및 알림톡 연동" },
];
const MAINTENANCE = [
  { id: "none", label: "없음",   months: 0,  pricePerMonth: 0 },
  { id: "3m",   label: "3개월", months: 3,  pricePerMonth: 50000 },
  { id: "6m",   label: "6개월", months: 6,  pricePerMonth: 45000 },
  { id: "12m",  label: "12개월",months: 12, pricePerMonth: 40000 },
];
const PORTFOLIO = [
  { id:1, title:"강남 프리미엄 헤어샵",    category:"뷰티/미용",  period:"2024.11", emoji:"✂️", bg:"linear-gradient(135deg,#667eea,#764ba2)", desc:"예약 시스템과 스타일리스트 소개 페이지 포함" },
  { id:2, title:"수제버거 브랜드 사이트",  category:"식음료",     period:"2024.10", emoji:"🍔", bg:"linear-gradient(135deg,#f093fb,#f5576c)", desc:"메뉴 소개, 매장 위치, 온라인 주문 연동" },
  { id:3, title:"IT 스타트업 랜딩페이지", category:"스타트업",   period:"2024.09", emoji:"🚀", bg:"linear-gradient(135deg,#4facfe,#00f2fe)", desc:"투자자 대상 제품 소개, 데모 신청 폼 포함" },
  { id:4, title:"개인 PT 트레이너",       category:"헬스",       period:"2024.08", emoji:"💪", bg:"linear-gradient(135deg,#43e97b,#38f9d7)", desc:"자격증, 후기, 프로그램 소개 페이지" },
  { id:5, title:"법률 사무소 사이트",     category:"법률/전문직", period:"2024.07", emoji:"⚖️", bg:"linear-gradient(135deg,#30cfd0,#330867)", desc:"변호사 소개, 전문 분야, 상담 예약 기능" },
  { id:6, title:"온라인 쇼핑몰 랜딩",     category:"이커머스",   period:"2024.06", emoji:"🛍️", bg:"linear-gradient(135deg,#fa709a,#fee140)", desc:"신상품 런칭 바이럴 랜딩, 사전 예약 기능" },
];
const STRENGTHS = [
  { icon:"⚡", title:"압도적인 속도", highlight:"평균 납기 3일", desc:"AI 바이브 코딩으로 기획부터 완성까지 평균 3일 이내. 경쟁사 대비 5배 빠른 납기로 비즈니스를 즉시 온라인에 올립니다." },
  { icon:"💰", title:"합리적인 가격", highlight:"기존 대비 70% 절감", desc:"에이전시 비용의 1/3 수준. AI가 반복 작업을 처리하기 때문에 절감된 비용을 그대로 고객에게 돌려드립니다." },
  { icon:"🤝", title:"밀착 케어",     highlight:"3개월 무상 유지보수", desc:"제작 후에도 끝이 아닙니다. 수정 요청, 콘텐츠 업데이트, 기술 지원까지 전담 매니저가 지속적으로 함께합니다." },
];

const fmt = (n) => n.toLocaleString("ko-KR") + "원";

// ── 메인 컴포넌트 ────────────────────────────────────────────────────────────
export default function App() {
  const [page, setPage] = useState("home"); // home | estimate | contact
  const [menuOpen, setMenuOpen] = useState(false);

  const nav = (p) => { setPage(p); setMenuOpen(false); window.scrollTo?.(0,0); };

  return (
    <div style={{ fontFamily: "'Inter', sans-serif" }} className="min-h-screen bg-white text-gray-900">
      {/* ── HEADER ── */}
      <header className="sticky top-0 z-50 bg-white/80 backdrop-blur border-b border-gray-100">
        <div className="max-w-6xl mx-auto px-4 h-16 flex items-center justify-between">
          <button onClick={() => nav("home")} className="flex items-center gap-2 font-bold text-lg">
            <div className="w-8 h-8 rounded-lg bg-indigo-600 flex items-center justify-center text-white"><Zap/></div>
            바로페이지
          </button>
          <nav className="hidden md:flex items-center gap-6 text-sm text-gray-500">
            {["home","estimate","contact"].map(p => (
              <button key={p} onClick={() => nav(p)} className={`hover:text-gray-900 transition-colors ${page===p?"text-gray-900 font-medium":""}`}>
                {p==="home"?"서비스 소개":p==="estimate"?"견적 계산기":"문의하기"}
              </button>
            ))}
          </nav>
          <button onClick={() => nav("contact")} className="hidden md:block bg-indigo-600 text-white text-sm font-medium px-4 py-2 rounded-lg hover:bg-indigo-700 transition-colors">
            무료 상담 신청
          </button>
          <button className="md:hidden" onClick={() => setMenuOpen(o => !o)}>
            {menuOpen ? <X/> : <Menu/>}
          </button>
        </div>
        {menuOpen && (
          <div className="md:hidden border-t border-gray-100 bg-white px-4 py-4 flex flex-col gap-3">
            {["home","estimate","contact"].map(p => (
              <button key={p} onClick={() => nav(p)} className="text-sm text-gray-600 text-left hover:text-gray-900">
                {p==="home"?"서비스 소개":p==="estimate"?"견적 계산기":"문의하기"}
              </button>
            ))}
            <button onClick={() => nav("contact")} className="bg-indigo-600 text-white text-sm font-medium px-4 py-2 rounded-lg">
              무료 상담 신청
            </button>
          </div>
        )}
      </header>

      {/* ── PAGES ── */}
      {page === "home"     && <HomePage     nav={nav}/>}
      {page === "estimate" && <EstimatePage nav={nav}/>}
      {page === "contact"  && <ContactPage/>}

      {/* ── FOOTER ── */}
      <footer className="border-t border-gray-100 bg-gray-50 py-8">
        <div className="max-w-6xl mx-auto px-4 flex flex-col md:flex-row items-center justify-between gap-4 text-sm text-gray-400">
          <div className="flex items-center gap-2 font-semibold text-gray-700">
            <div className="w-7 h-7 rounded-lg bg-indigo-600 flex items-center justify-center text-white"><Zap/></div>
            바로페이지
          </div>
          <div className="flex gap-6">
            {["estimate","contact"].map(p => (
              <button key={p} onClick={() => nav(p)} className="hover:text-gray-600 transition-colors">
                {p==="estimate"?"견적 계산기":"문의하기"}
              </button>
            ))}
          </div>
          <p>© 2025 바로페이지. All rights reserved.</p>
        </div>
      </footer>
    </div>
  );
}

// ── HOME PAGE ────────────────────────────────────────────────────────────────
function HomePage({ nav }) {
  return (
    <>
      {/* Hero */}
      <section className="relative overflow-hidden py-24 md:py-36 text-center px-4">
        <div className="absolute inset-0 -z-10 flex items-start justify-center">
          <div style={{ width:900, height:600, borderRadius:"50%", background:"radial-gradient(ellipse,rgba(99,102,241,0.08) 0%,transparent 70%)" }}/>
        </div>
        <div className="max-w-4xl mx-auto">
          <span className="inline-flex items-center gap-1.5 border border-indigo-200 bg-indigo-50 text-indigo-700 text-xs font-semibold px-3 py-1.5 rounded-full mb-6">
            <Sparkles/> AI 바이브 코딩으로 제작하는 맞춤형 홈페이지
          </span>
          <h1 className="text-4xl md:text-6xl font-extrabold tracking-tight leading-tight">
            당신의 비즈니스를 <span className="text-indigo-600">온라인</span>으로,<br/>
            <span className="text-indigo-600">빠르고 저렴하게</span>
          </h1>
          <p className="mt-6 text-lg text-gray-500 max-w-2xl mx-auto leading-relaxed">
            복잡한 견적 없이, 바로페이지와 함께하면 <strong className="text-gray-700">3일 이내</strong>에 전문적인 홈페이지를 완성할 수 있습니다. 소상공인부터 스타트업까지 — AI가 만드는 퀄리티, 사람이 케어하는 서비스.
          </p>
          <div className="mt-10 flex flex-col sm:flex-row items-center justify-center gap-4">
            <button onClick={() => nav("estimate")} className="flex items-center gap-2 bg-indigo-600 text-white font-semibold px-8 py-3.5 rounded-xl hover:bg-indigo-700 transition-colors text-base">
              무료 견적 계산해보기 <ArrowRight/>
            </button>
            <button className="flex items-center gap-2 border border-gray-200 text-gray-700 font-semibold px-8 py-3.5 rounded-xl hover:border-gray-300 transition-colors text-base">
              포트폴리오 보기
            </button>
          </div>
          <p className="mt-10 text-sm text-gray-400">
            ⭐ 누적 제작 <strong className="text-gray-600">50+</strong>개 &nbsp;·&nbsp; 고객 만족도 <strong className="text-gray-600">98%</strong> &nbsp;·&nbsp; 평균 납기 <strong className="text-gray-600">3일</strong>
          </p>
        </div>
      </section>

      {/* Strengths */}
      <section className="bg-gray-50 py-20 px-4">
        <div className="max-w-6xl mx-auto">
          <div className="text-center mb-12">
            <p className="text-xs font-bold uppercase tracking-widest text-indigo-600 mb-3">Why BaroPage</p>
            <h2 className="text-3xl font-bold">바로페이지를 선택해야 하는 이유</h2>
            <p className="mt-3 text-gray-500 max-w-xl mx-auto">퀄리티, 속도, 가격 세 가지를 모두 잡았습니다.</p>
          </div>
          <div className="grid md:grid-cols-3 gap-6">
            {STRENGTHS.map(s => (
              <div key={s.title} className="bg-white rounded-2xl border border-gray-100 shadow-sm p-6 hover:shadow-md transition-shadow">
                <div className="w-11 h-11 rounded-xl bg-indigo-50 flex items-center justify-center text-2xl mb-4">{s.icon}</div>
                <p className="text-xs font-bold text-indigo-600 uppercase tracking-wide mb-1">{s.highlight}</p>
                <h3 className="text-xl font-bold mb-2">{s.title}</h3>
                <p className="text-sm text-gray-500 leading-relaxed">{s.desc}</p>
              </div>
            ))}
          </div>
        </div>
      </section>

      {/* Portfolio */}
      <section className="py-20 px-4">
        <div className="max-w-6xl mx-auto">
          <div className="text-center mb-12">
            <p className="text-xs font-bold uppercase tracking-widest text-indigo-600 mb-3">Portfolio</p>
            <h2 className="text-3xl font-bold">바로페이지가 만든 홈페이지</h2>
            <p className="mt-3 text-gray-500">다양한 업종과 규모의 고객사 프로젝트를 확인해보세요.</p>
          </div>
          <div className="grid sm:grid-cols-2 lg:grid-cols-3 gap-6">
            {PORTFOLIO.map(p => (
              <div key={p.id} className="group rounded-2xl border border-gray-100 overflow-hidden shadow-sm hover:shadow-lg hover:-translate-y-1 transition-all">
                <div className="h-44 flex items-center justify-center text-5xl" style={{ background: p.bg }}>
                  {p.emoji}
                </div>
                <div className="p-5 bg-white">
                  <div className="flex items-center justify-between mb-2">
                    <span className="text-xs font-semibold bg-gray-100 text-gray-600 px-2.5 py-1 rounded-full">{p.category}</span>
                    <span className="text-xs text-gray-400">{p.period}</span>
                  </div>
                  <h3 className="font-bold mb-1">{p.title}</h3>
                  <p className="text-sm text-gray-500">{p.desc}</p>
                </div>
              </div>
            ))}
          </div>
          <div className="text-center mt-12">
            <p className="text-gray-500 mb-4">내 비즈니스에 맞는 홈페이지가 궁금하신가요?</p>
            <button onClick={() => nav("contact")} className="bg-indigo-600 text-white font-semibold px-8 py-3.5 rounded-xl hover:bg-indigo-700 transition-colors">
              무료 상담 신청하기
            </button>
          </div>
        </div>
      </section>
    </>
  );
}

// ── ESTIMATE PAGE ─────────────────────────────────────────────────────────────
function EstimatePage({ nav }) {
  const [site, setSite]     = useState(null);
  const [feats, setFeats]   = useState([]);
  const [maint, setMaint]   = useState("none");

  const toggleFeat = id => setFeats(p => p.includes(id) ? p.filter(f=>f!==id) : [...p, id]);
  const m = MAINTENANCE.find(o => o.id === maint);
  const featTotal = FEATURES.filter(f => feats.includes(f.id)).reduce((s,f)=>s+f.price, 0);
  const maintTotal = m.months * m.pricePerMonth;
  const total = (site?.basePrice ?? 0) + featTotal + maintTotal;

  return (
    <div className="max-w-5xl mx-auto px-4 py-16">
      <div className="text-center mb-12">
        <p className="text-xs font-bold uppercase tracking-widest text-indigo-600 mb-3">Estimate</p>
        <h1 className="text-3xl font-bold">예상 견적 계산기</h1>
        <p className="mt-3 text-gray-500 max-w-xl mx-auto">원하는 사이트 유형과 기능을 선택하면 예상 비용을 실시간으로 확인할 수 있습니다.</p>
      </div>

      <div className="grid lg:grid-cols-3 gap-8">
        <div className="lg:col-span-2 space-y-10">

          {/* Step 1 */}
          <div>
            <h2 className="font-bold text-lg mb-4 flex items-center gap-2">
              <span className="w-6 h-6 rounded-full bg-indigo-600 text-white text-xs flex items-center justify-center font-bold">1</span>
              사이트 유형 선택
            </h2>
            <div className="grid sm:grid-cols-2 gap-3">
              {SITE_TYPES.map(s => (
                <button key={s.id} onClick={() => setSite(s)}
                  className={`text-left p-4 rounded-xl border-2 transition-all ${site?.id===s.id?"border-indigo-600 bg-indigo-50":"border-gray-100 hover:border-indigo-200 bg-white"}`}>
                  <div className="flex justify-between items-start">
                    <span className="text-2xl">{s.emoji}</span>
                    {site?.id===s.id && <span className="w-5 h-5 rounded-full bg-indigo-600 flex items-center justify-center text-white"><Check small/></span>}
                  </div>
                  <p className="mt-2 font-bold">{s.label}</p>
                  <p className="text-xs text-gray-500 mt-1">{s.description}</p>
                  <p className="mt-2 text-sm font-bold text-indigo-600">{fmt(s.basePrice)}~</p>
                </button>
              ))}
            </div>
          </div>

          {/* Step 2 */}
          <div>
            <h2 className="font-bold text-lg mb-4 flex items-center gap-2">
              <span className="w-6 h-6 rounded-full bg-indigo-600 text-white text-xs flex items-center justify-center font-bold">2</span>
              추가 기능 선택 <span className="text-sm font-normal text-gray-400">(복수 선택 가능)</span>
            </h2>
            <div className="grid sm:grid-cols-2 gap-3">
              {FEATURES.map(f => (
                <button key={f.id} onClick={() => toggleFeat(f.id)}
                  className={`text-left p-4 rounded-xl border-2 transition-all ${feats.includes(f.id)?"border-indigo-600 bg-indigo-50":"border-gray-100 hover:border-indigo-200 bg-white"}`}>
                  <div className="flex justify-between items-center">
                    <p className="font-medium text-sm">{f.label}</p>
                    {feats.includes(f.id) && <span className="w-5 h-5 rounded-full bg-indigo-600 flex items-center justify-center text-white flex-shrink-0"><Check small/></span>}
                  </div>
                  <p className="text-xs text-gray-400 mt-1">{f.description}</p>
                  <p className="mt-2 text-sm font-bold text-indigo-600">+{fmt(f.price)}</p>
                </button>
              ))}
            </div>
          </div>

          {/* Step 3 */}
          <div>
            <h2 className="font-bold text-lg mb-4 flex items-center gap-2">
              <span className="w-6 h-6 rounded-full bg-indigo-600 text-white text-xs flex items-center justify-center font-bold">3</span>
              유지보수 플랜
            </h2>
            <div className="grid grid-cols-4 gap-3">
              {MAINTENANCE.map(o => (
                <button key={o.id} onClick={() => setMaint(o.id)}
                  className={`p-4 rounded-xl border-2 text-center transition-all ${maint===o.id?"border-indigo-600 bg-indigo-50":"border-gray-100 hover:border-indigo-200 bg-white"}`}>
                  <p className="font-semibold text-sm">{o.label}</p>
                  {o.pricePerMonth > 0
                    ? <p className="text-xs text-indigo-600 font-bold mt-1">{fmt(o.pricePerMonth)}/월</p>
                    : <p className="text-xs text-gray-400 mt-1">해당 없음</p>}
                </button>
              ))}
            </div>
          </div>
        </div>

        {/* 견적 요약 */}
        <div className="lg:col-span-1">
          <div className="sticky top-24 bg-white rounded-2xl border border-gray-100 shadow-md p-6 space-y-4">
            <h3 className="font-bold text-lg">견적 요약</h3>
            <div className="space-y-2 text-sm">
              <div className="flex justify-between">
                <span className="text-gray-400">사이트 유형</span>
                <span className="font-medium">{site?.label ?? "미선택"}</span>
              </div>
              <div className="flex justify-between">
                <span className="text-gray-400">기본 금액</span>
                <span>{site ? fmt(site.basePrice) : "-"}</span>
              </div>
            </div>
            {feats.length > 0 && (
              <div className="border-t pt-3 space-y-2 text-sm">
                <p className="text-gray-400 font-medium">추가 기능</p>
                {FEATURES.filter(f=>feats.includes(f.id)).map(f => (
                  <div key={f.id} className="flex justify-between">
                    <span className="text-gray-500 flex items-center gap-1"><Check small/>{f.label}</span>
                    <span>+{fmt(f.price)}</span>
                  </div>
                ))}
              </div>
            )}
            {m.months > 0 && (
              <div className="border-t pt-3 text-sm">
                <div className="flex justify-between">
                  <span className="text-gray-400">유지보수 ({m.months}개월)</span>
                  <span>+{fmt(maintTotal)}</span>
                </div>
              </div>
            )}
            <div className="border-t pt-4">
              <div className="flex justify-between items-center">
                <span className="font-bold">예상 총 금액</span>
                <span className="text-2xl font-extrabold text-indigo-600">{total > 0 ? fmt(total) : "-"}</span>
              </div>
              <p className="text-xs text-gray-400 mt-1">* 실제 금액은 상담 후 확정됩니다</p>
            </div>
            {feats.length >= 3 && (
              <div className="bg-indigo-50 text-indigo-700 text-xs font-semibold text-center py-2 px-3 rounded-lg">
                🎉 기능 3개 이상 선택 시 10% 할인 가능
              </div>
            )}
            <button
              onClick={() => nav("contact")}
              disabled={!site}
              className={`w-full flex items-center justify-center gap-2 py-3 rounded-xl font-semibold transition-colors ${site?"bg-indigo-600 text-white hover:bg-indigo-700":"bg-gray-100 text-gray-300 cursor-not-allowed"}`}
            >
              이 견적으로 상담 신청 <ArrowRight/>
            </button>
          </div>
        </div>
      </div>
    </div>
  );
}

// ── CONTACT PAGE ──────────────────────────────────────────────────────────────
function ContactPage() {
  const [form, setForm] = useState({ name:"", email:"", phone:"", company:"", site_type:"", budget:"", message:"" });
  const [sent, setSent] = useState(false);
  const set = (k, v) => setForm(p => ({ ...p, [k]: v }));

  const handleSubmit = () => {
    if (!form.name || !form.email || !form.phone || !form.site_type || !form.message) return;
    setSent(true);
  };

  if (sent) return (
    <div className="max-w-lg mx-auto px-4 py-32 text-center">
      <div className="text-6xl mb-6">✅</div>
      <h2 className="text-2xl font-bold mb-3">문의가 접수되었습니다!</h2>
      <p className="text-gray-500 mb-6">영업일 기준 24시간 내에 <strong>{form.email}</strong>로 연락드리겠습니다.</p>
      <button onClick={() => setSent(false)} className="border border-gray-200 px-6 py-2.5 rounded-xl text-sm hover:border-gray-300 transition-colors">
        추가 문의하기
      </button>
    </div>
  );

  return (
    <div className="max-w-5xl mx-auto px-4 py-16">
      <div className="text-center mb-12">
        <p className="text-xs font-bold uppercase tracking-widest text-indigo-600 mb-3">Contact</p>
        <h1 className="text-3xl font-bold">문의하기</h1>
        <p className="mt-3 text-gray-500 max-w-xl mx-auto">아래 폼을 작성해주세요. 영업일 기준 24시간 내 담당자가 연락드립니다.</p>
      </div>

      <div className="grid lg:grid-cols-3 gap-10">
        <aside className="space-y-5">
          <div className="rounded-2xl border border-gray-100 bg-gray-50 p-6 space-y-4">
            <h2 className="font-bold">연락처 정보</h2>
            {[{e:"📧",l:"이메일",v:"hello@baropage.kr"},{e:"📞",l:"전화",v:"010-0000-0000"},{e:"🕐",l:"운영시간",v:"평일 09:00–18:00"}].map(i => (
              <div key={i.l} className="flex items-center gap-3">
                <span className="text-xl">{i.e}</span>
                <div>
                  <p className="text-xs text-gray-400">{i.l}</p>
                  <p className="text-sm font-medium">{i.v}</p>
                </div>
              </div>
            ))}
          </div>
          <div className="rounded-2xl border border-gray-100 bg-gray-50 p-6">
            <h2 className="font-bold mb-3">💡 이런 분께 추천해요</h2>
            <ul className="text-sm text-gray-500 space-y-2">
              {["홈페이지가 없어 고객을 놓치는 소상공인","기존 사이트 리뉴얼이 필요한 분","빠른 온라인 채널이 필요한 분","저렴하게 전문 사이트를 원하는 분"].map(t => (
                <li key={t} className="flex gap-2"><span className="text-indigo-500">✓</span>{t}</li>
              ))}
            </ul>
          </div>
        </aside>

        <div className="lg:col-span-2 bg-white rounded-2xl border border-gray-100 shadow-sm p-6 md:p-8 space-y-5">
          <div className="grid sm:grid-cols-2 gap-4">
            {[{id:"name",label:"이름",ph:"홍길동",type:"text",req:true},{id:"phone",label:"연락처",ph:"010-0000-0000",type:"tel",req:true}].map(f => (
              <div key={f.id}>
                <label className="text-sm font-medium block mb-1.5">{f.label} {f.req && <span className="text-red-500">*</span>}</label>
                <input type={f.type} placeholder={f.ph} required={f.req} value={form[f.id]} onChange={e=>set(f.id,e.target.value)}
                  className="w-full border border-gray-200 rounded-xl px-4 py-2.5 text-sm focus:outline-none focus:ring-2 focus:ring-indigo-500 transition"/>
              </div>
            ))}
          </div>
          <div className="grid sm:grid-cols-2 gap-4">
            {[{id:"email",label:"이메일",ph:"hello@example.com",type:"email",req:true},{id:"company",label:"회사/상호명",ph:"바로페이지",type:"text",req:false}].map(f => (
              <div key={f.id}>
                <label className="text-sm font-medium block mb-1.5">{f.label} {!f.req && <span className="text-xs text-gray-400">(선택)</span>}</label>
                <input type={f.type} placeholder={f.ph} required={f.req} value={form[f.id]} onChange={e=>set(f.id,e.target.value)}
                  className="w-full border border-gray-200 rounded-xl px-4 py-2.5 text-sm focus:outline-none focus:ring-2 focus:ring-indigo-500 transition"/>
              </div>
            ))}
          </div>
          <div className="grid sm:grid-cols-2 gap-4">
            <div>
              <label className="text-sm font-medium block mb-1.5">사이트 유형 <span className="text-red-500">*</span></label>
              <select required value={form.site_type} onChange={e=>set("site_type",e.target.value)}
                className="w-full border border-gray-200 rounded-xl px-4 py-2.5 text-sm focus:outline-none focus:ring-2 focus:ring-indigo-500 bg-white transition">
                <option value="">유형을 선택해주세요</option>
                {SITE_TYPES.map(t => <option key={t.id} value={t.id}>{t.emoji} {t.label}</option>)}
                <option value="other">기타</option>
              </select>
            </div>
            <div>
              <label className="text-sm font-medium block mb-1.5">예산 범위 <span className="text-xs text-gray-400">(선택)</span></label>
              <select value={form.budget} onChange={e=>set("budget",e.target.value)}
                className="w-full border border-gray-200 rounded-xl px-4 py-2.5 text-sm focus:outline-none focus:ring-2 focus:ring-indigo-500 bg-white transition">
                <option value="">예산을 선택해주세요</option>
                {["30만원 미만","30–60만원","60–100만원","100–200만원","200만원 이상","미정"].map(b => <option key={b}>{b}</option>)}
              </select>
            </div>
          </div>
          <div>
            <label className="text-sm font-medium block mb-1.5">문의 내용 <span className="text-red-500">*</span></label>
            <textarea rows={5} required placeholder="원하시는 홈페이지 유형, 참고 사이트, 특별한 요구사항 등을 자유롭게 작성해주세요." value={form.message} onChange={e=>set("message",e.target.value)}
              className="w-full border border-gray-200 rounded-xl px-4 py-2.5 text-sm focus:outline-none focus:ring-2 focus:ring-indigo-500 transition resize-none"/>
          </div>
          <button onClick={handleSubmit} className="w-full bg-indigo-600 text-white font-semibold py-3.5 rounded-xl hover:bg-indigo-700 transition-colors flex items-center justify-center gap-2">
            문의 전송하기 <ArrowRight/>
          </button>
          <p className="text-center text-xs text-gray-400">제출하신 정보는 홈페이지 제작 상담 목적으로만 사용됩니다.</p>
        </div>
      </div>
    </div>
  );
}
