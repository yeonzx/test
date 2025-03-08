<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>유튜브 혁명: 4주 매출 시스템</title>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/tailwindcss/2.2.19/tailwind.min.css" rel="stylesheet">
    <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+KR:wght@400;500;700;900&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Noto Sans KR', sans-serif;
            background-color: #000;
            color: #fff;
            line-height: 1.5;
        }
        
        .gradient-bg {
            background: linear-gradient(135deg, #FF0080, #7928CA);
        }
        
        .gradient-text {
            background: linear-gradient(135deg, #FF0080, #7928CA);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        
        .highlighted-text {
            color: #FF0080;
            font-weight: bold;
        }
        
        .section {
            padding: 2rem 1.5rem;
            position: relative;
        }
        
        .section:not(:last-child)::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 1.5rem;
            right: 1.5rem;
            height: 1px;
            background: rgba(255, 255, 255, 0.1);
        }
        
        .card {
            background-color: #111;
            border-radius: 1rem;
            padding: 1.5rem;
            margin-bottom: 1rem;
            position: relative;
            overflow: hidden;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        .card-highlight {
            border: 1px solid #FF0080;
            box-shadow: 0 4px 20px rgba(255, 0, 128, 0.2);
        }
        
        .card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 4px;
            height: 100%;
            background: linear-gradient(135deg, #FF0080, #7928CA);
        }
        
        .card-highlight::before {
            width: 100%;
            height: 4px;
        }
        
        .pulse {
            animation: pulse 2s infinite;
        }
        
        @keyframes pulse {
            0% {
                transform: scale(1);
            }
            50% {
                transform: scale(1.05);
            }
            100% {
                transform: scale(1);
            }
        }
        
        .btn {
            padding: 1rem 2rem;
            border-radius: 0.5rem;
            font-weight: bold;
            font-size: 1.125rem;
            text-align: center;
            display: block;
            width: 100%;
            position: relative;
            overflow: hidden;
            z-index: 1;
            transition: all 0.3s ease;
        }
        
        .btn-primary {
            background: linear-gradient(135deg, #FF0080, #7928CA);
            color: white;
            box-shadow: 0 4px 20px rgba(255, 0, 128, 0.3);
        }
        
        .btn-primary:hover {
            box-shadow: 0 4px 25px rgba(255, 0, 128, 0.5);
        }
        
        .btn::after {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            width: 120%;
            height: 0;
            padding-bottom: 120%;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 50%;
            transform: translate(-50%, -50%) scale(0);
            opacity: 0;
            z-index: -1;
            transition: transform 0.5s ease, opacity 0.5s ease;
        }
        
        .btn:active::after {
            transform: translate(-50%, -50%) scale(1);
            opacity: 1;
            transition: 0s;
        }
        
        .case-badge {
            display: inline-block;
            padding: 0.25rem 0.75rem;
            border-radius: 1rem;
            font-size: 0.75rem;
            font-weight: bold;
            margin-right: 0.5rem;
            background: rgba(255, 255, 255, 0.1);
        }
        
        .case-badge-success {
            background: rgba(0, 255, 128, 0.15);
            color: #00FF80;
        }
        
        .week-tabs {
            display: flex;
            overflow-x: auto;
            scrollbar-width: none;
            margin: 0 -1.5rem 1.5rem;
            padding: 0 1.5rem;
        }
        
        .week-tabs::-webkit-scrollbar {
            display: none;
        }
        
        .week-tab {
            flex: 0 0 auto;
            padding: 0.75rem 1.5rem;
            margin-right: 0.5rem;
            border-radius: 0.5rem;
            background: #111;
            color: #fff;
            font-weight: bold;
            white-space: nowrap;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        .week-tab.active {
            background: linear-gradient(135deg, #FF0080, #7928CA);
            color: white;
            border-color: transparent;
        }
        
        .week-content {
            display: none;
        }
        
        .week-content.active {
            display: block;
        }
        
        .checkmark-list li {
            position: relative;
            padding-left: 2rem;
            margin-bottom: 0.75rem;
        }
        
        .checkmark-list li::before {
            content: '✓';
            position: absolute;
            left: 0;
            color: #FF0080;
            font-weight: bold;
        }
        
        .problem-list li {
            position: relative;
            padding-left: 2rem;
            margin-bottom: 0.75rem;
        }
        
        .problem-list li::before {
            content: '✗';
            position: absolute;
            left: 0;
            color: #FF0080;
            font-weight: bold;
        }
        
        .fixed-cta {
            position: fixed;
            bottom: 0;
            left: 0;
            right: 0;
            background: rgba(0, 0, 0, 0.9);
            backdrop-filter: blur(10px);
            padding: 1rem 1.5rem;
            z-index: 100;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        .stat-card {
            padding: 1rem;
            border-radius: 0.75rem;
            background: #111;
            text-align: center;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        .limited-spots {
            background: rgba(255, 0, 128, 0.1);
            border: 1px solid #FF0080;
            border-radius: 0.5rem;
            padding: 0.5rem 1rem;
            text-align: center;
            margin-bottom: 1rem;
        }
        
        .arrow-down {
            width: 0;
            height: 0;
            border-left: 10px solid transparent;
            border-right: 10px solid transparent;
            border-top: 10px solid #FF0080;
            margin: 1rem auto;
        }
        
        .price-strike {
            text-decoration: line-through;
            color: rgba(255, 255, 255, 0.5);
        }
        
        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
        
        .fade-in-up {
            animation: fadeInUp 0.6s ease forwards;
        }
        
        .delay-100 { animation-delay: 0.1s; }
        .delay-200 { animation-delay: 0.2s; }
        .delay-300 { animation-delay: 0.3s; }
        .delay-400 { animation-delay: 0.4s; }
        .delay-500 { animation-delay: 0.5s; }
    </style>
</head>
<body>
    <!-- 헤더 섹션 -->
    <section class="section">
        <div class="text-sm text-gray-400">4주 완성 프로그램</div>
        <h1 class="text-3xl font-black mt-2 mb-4">
            <span class="gradient-text">월 500만원 대행사가 숨기는</span><br>
            유튜브 돈 벌기의 비밀
        </h1>
        <p class="text-gray-300 mb-6">
            3개의 영상만으로 구독자 3만+와 <br>
            <span class="highlighted-text">실제 매출 폭발</span>을 만드는 4주 시스템
        </p>
        
        <div class="video-placeholder mb-6">
            <div class="relative rounded-xl overflow-hidden">
                <img src="/api/placeholder/600/350" alt="프로그램 소개 영상" class="w-full rounded-xl">
                <div class="absolute inset-0 flex items-center justify-center">
                    <div class="w-16 h-16 rounded-full bg-white bg-opacity-20 flex items-center justify-center backdrop-filter backdrop-blur-sm">
                        <div class="w-0 h-0 border-t-8 border-b-8 border-l-14 border-transparent border-l-white ml-1"></div>
                    </div>
                </div>
            </div>
        </div>
        
        <div class="limited-spots pulse">
            <p class="text-sm font-bold text-white">마지막 <span class="text-xl gradient-text">8자리</span> | 다음 기수 가격 인상 예정</p>
        </div>
        
        <button class="btn btn-primary mb-4">지금 바로 신청하기</button>
        <p class="text-center text-xs text-gray-400">* 심사 후 적합한 분들만 선발됩니다</p>
    </section>
    
    <!-- 성과 지표 -->
    <section class="section">
        <h2 class="text-2xl font-bold mb-4">단 <span class="gradient-text">3개의 영상</span>으로</h2>
        
        <div class="grid grid-cols-3 gap-3 mb-6">
            <div class="stat-card">
                <div class="text-sm text-gray-400">최소 영상</div>
                <div class="text-2xl font-bold gradient-text">3개</div>
            </div>
            <div class="stat-card">
                <div class="text-sm text-gray-400">구축 기간</div>
                <div class="text-2xl font-bold gradient-text">4주</div>
            </div>
            <div class="stat-card">
                <div class="text-sm text-gray-400">평균 성장</div>
                <div class="text-2xl font-bold gradient-text">300%</div>
            </div>
        </div>
        
        <div class="card card-highlight">
            <h3 class="font-bold mb-2">유튜브는 레드오션이 아닙니다</h3>
            <p class="text-sm text-gray-300">
                지금도 매일 새로운 채널이 성공하고 있습니다. 중요한 것은 <span class="highlighted-text">올바른 전략</span>과 <span class="highlighted-text">시스템</span>입니다.
            </p>
        </div>
    </section>
    
    <!-- 성공 사례 -->
    <section class="section">
        <h2 class="text-2xl font-bold mb-4">입증된 성공 사례</h2>
        
        <div class="card fade-in-up">
            <div class="flex justify-between items-start mb-3">
                <h3 class="font-bold">교육 채널 B</h3>
                <div class="case-badge case-badge-success">영상 1개</div>
            </div>
            <p class="text-sm text-gray-300 mb-2">
                단 1개의 영상으로 설명회 전석 만석을 달성했습니다.
            </p>
            <div class="text-right">
                <span class="case-badge case-badge-success">원생 100명 확보</span>
            </div>
        </div>
        
        <div class="card fade-in-up delay-100">
            <div class="flex justify-between items-start mb-3">
                <h3 class="font-bold">변호사 A</h3>
                <div class="case-badge case-badge-success">영상 1개</div>
            </div>
            <p class="text-sm text-gray-300 mb-2">
                단 하나의 영상으로 2천만원 사건을 수임했습니다.
            </p>
            <div class="text-right">
                <span class="case-badge case-badge-success">2천만원 매출</span>
            </div>
        </div>
        
        <div class="card fade-in-up delay-200">
            <div class="flex justify-between items-start mb-3">
                <h3 class="font-bold">치과 원장</h3>
                <div class="case-badge case-badge-success">영상 7개</div>
            </div>
            <p class="text-sm text-gray-300 mb-2">
                영상 7개 업로드 후 신환이 대폭 증가했습니다.
            </p>
            <div class="text-right">
                <span class="case-badge case-badge-success">신환 300% 증가</span>
            </div>
        </div>
        
        <div class="arrow-down"></div>
        
        <div class="card card-highlight fade-in-up delay-300">
            <h3 class="font-bold mb-2">교육 채널 D의 폭발적 성장</h3>
            <p class="text-sm text-gray-300 mb-3">
                APCP 이론 접목 후 <span class="highlighted-text">구독자 1만 → 10만</span> 달성
            </p>
            <ul class="text-sm text-gray-300">
                <li class="mb-1">✓ 정부지원사업 3.5억 획득</li>
                <li class="mb-1">✓ 월 광고제안 300만원 단가</li>
                <li>✓ 유튜브 라이브 1회로 <span class="highlighted-text">5천만원 매출</span></li>
            </ul>
        </div>
    </section>
    
    <!-- 문제점 -->
    <section class="section">
        <h2 class="text-2xl font-bold mb-4">유튜브 컨설팅의 <span class="gradient-text">불편한 진실</span></h2>
        
        <ul class="problem-list text-gray-300 mb-6">
            <li class="fade-in-up">월 <span class="highlighted-text">500만원</span>을 대행사에 쏟아부어도 채널 소유권은 당신에게 없습니다.</li>
            <li class="fade-in-up delay-100">대행이 중단되면 채널도 함께 <span class="highlighted-text">죽습니다</span>.</li>
            <li class="fade-in-up delay-200">프로덕션의 고퀄리티 영상이 유튜브 알고리즘과 <span class="highlighted-text">충돌</span>합니다.</li>
            <li class="fade-in-up delay-300">대행사들은 클라이언트 만족을 위해 <span class="highlighted-text">가짜 조회수와 구독자</span>를 구매합니다.</li>
            <li class="fade-in-up delay-400">이론만 가득한 강의로는 <span class="highlighted-text">실전에서 아무것도 할 수 없습니다</span>.</li>
        </ul>
        
        <div class="card gradient-bg">
            <h3 class="font-bold mb-2">더 이상 속지 마세요</h3>
            <p class="text-sm">
                조회수만 높고 매출은 없는 채널은 의미가 없습니다. <span class="font-bold">진짜 중요한 것은 트래픽을 매출로 전환하는 것입니다.</span>
            </p>
        </div>
    </section>
    
    <!-- 4주 프로그램 -->
    <section class="section">
        <h2 class="text-2xl font-bold mb-4">
            <span class="gradient-text">4주 완성</span> 매출 시스템
        </h2>
        
        <p class="text-gray-300 mb-4">
            말이 좋아 '강의'지, 사실상 손발 딱 붙들고 밀어주는 <span class="highlighted-text">"밀착 과외"</span>입니다.
        </p>
        
        <div class="week-tabs">
            <div class="week-tab active" data-week="1">1주차</div>
            <div class="week-tab" data-week="2">2주차</div>
            <div class="week-tab" data-week="3">3주차</div>
            <div class="week-tab" data-week="4">4주차</div>
        </div>
        
        <div class="week-content active" id="week-1">
            <div class="card">
                <h3 class="font-bold gradient-text mb-3">채널 DNA 구축</h3>
                <ul class="checkmark-list text-sm text-gray-300 mb-4">
                    <li>당신만의 고유한 포지셔닝 전략 수립</li>
                    <li>시청자가 공감하는 브랜드 스토리 설계</li>
                    <li>자의식을 내려놓고 매력적인 캐릭터 구축</li>
                    <li>비즈니스 목표와 연결된 콘텐츠 전략 수립</li>
                </ul>
                <div class="bg-black bg-opacity-50 p-3 rounded-lg">
                    <p class="text-sm highlighted-text font-bold mb-1">우리는 짜치는 채널을 만들지 않습니다</p>
                    <p class="text-xs text-gray-400">
                        진정한 가치가 있는 콘텐츠만 추구합니다. 당신만의 매력을 최대한 끌어올려 진정성 있는 브랜딩을 구축합니다.
                    </p>
                </div>
            </div>
        </div>
        
        <div class="week-content" id="week-2">
            <div class="card">
                <h3 class="font-bold gradient-text mb-3">알고리즘 최적화 마스터링</h3>
                <ul class="checkmark-list text-sm text-gray-300 mb-4">
                    <li>유튜브 트래픽 시스템의 핵심 원리 분석</li>
                    <li>클릭률을 높이는 썸네일과 제목 설계법</li>
                    <li>시청 유지율을 극대화하는 영상 구성 전략</li>
                    <li>APCP 알고리즘을 활용한 채널 성장 가속화</li>
                </ul>
                <div class="bg-black bg-opacity-50 p-3 rounded-lg">
                    <p class="text-sm highlighted-text font-bold mb-1">무조건 터지는 알고리즘 비밀 전수</p>
                    <p class="text-xs text-gray-400">
                        유튜브 알고리즘을 이해하고 활용하여 최소한의 노력으로 최대한의 노출을 이끌어내는 전략을 학습합니다.
                    </p>
                </div>
            </div>
        </div>
        
        <div class="week-content" id="week-3">
            <div class="card">
                <h3 class="font-bold gradient-text mb-3">제작 시스템 자동화</h3>
                <ul class="checkmark-list text-sm text-gray-300 mb-4">
                    <li>최소한의 장비로 최대 효과를 내는 세팅 완성</li>
                    <li>버튼 하나로 촬영 가능한 환경 구축</li>
                    <li>외주와 프리랜서를 최적으로 활용하는 방법</li>
                    <li>편집 시간을 90% 줄이는 템플릿 시스템</li>
                </ul>
                <div class="bg-black bg-opacity-50 p-3 rounded-lg">
                    <p class="text-sm highlighted-text font-bold mb-1">반자동화된 유튜브 제작 시스템</p>
                    <p class="text-xs text-gray-400">
                        촬영부터 편집까지 모든 과정을 최적화하여 시간과 비용을 절약하는 방법을 배웁니다.
                    </p>
                </div>
            </div>
        </div>
        
        <div class="week-content" id="week-4">
            <div class="card">
                <h3 class="font-bold gradient-text mb-3">매출 전환 시스템 확립</h3>
                <ul class="checkmark-list text-sm text-gray-300 mb-4">
                    <li>조회수를 실제 매출로 바꾸는 전환 프로세스</li>
                    <li>고객 신뢰를 높이는 전문가 포지셔닝 전략</li>
                    <li>오프라인 비즈니스와 유튜브의 시너지 창출</li>
                    <li>지속 가능한 수익 모델 구축</li>
                </ul>
                <div class="bg-black bg-opacity-50 p-3 rounded-lg">
                    <p class="text-sm highlighted-text font-bold mb-1">실제 매출로 이어지는 유튜브 채널</p>
                    <p class="text-xs text-gray-400">
                        단순 조회수가 아닌 실제 비즈니스 성과로 이어지는 유튜브 전략을 구축합니다.
                    </p>
                </div>
            </div>
        </div>
    </section>
    
    <!-- 차별점 -->
    <section class="section">
        <h2 class="text-2xl font-bold mb-4">
            우리가 <span class="gradient-text">다른 이유</span>
        </h2>
        
        <div class="card mb-4 fade-in-up">
            <h3 class="font-bold mb-2">완전 밀착 지원</h3>
            <p class="text-sm text-gray-300">
                이론만 알려주고 끝나는 것이 아닌 실제 구현까지 함께합니다. 진짜 실행력이 생기는 프로그램입니다.
            </p>
        </div>
        
        <div class="card mb-4 fade-in-up delay-100">
            <h3 class="font-bold mb-2">비즈니스 연계</h3>
            <p class="text-sm text-gray-300">
                단순한 구독자 증가가 아닌 실제 매출 증가에 초점을 맞춥니다. 유튜브가 실질적인 비즈니스 성과로 이어지도록 설계합니다.
            </p>
        </div>
        
        <div class="card mb-4 fade-in-up delay-200">
            <h3 class="font-bold mb-2">검증된 방법론</h3>
            <p class="text-sm text-gray-300">
                다양한 분야에서 성공한 사례를 기반으로 한 전략을 제시합니다. 이미 1500만원 이상의 프리미엄 컨설팅에서 제공하던 내용을 체계화했습니다.
            </p>
        </div>
        
        <div class="card fade-in-up delay-300">
            <h3 class="font-bold mb-2">지속 가능성</h3>
            <p class="text-sm text-gray-300">
                외부 의존 없이 스스로 운영 가능한 자립형 시스템을 구축합니다. 더 이상 대행사에 매달 500만원을 쏟아붓지 않아도 됩니다.
            </p>
        </div>
    </section>
    
    <!-- 신청 안내 -->
    <section class="section">
        <div class="card card-highlight">
            <h2 class="text-xl font-bold mb-3">이 기회는 누구에게나 열려있지 않습니다</h2>
            <p class="text-sm text-gray-300 mb-4">
                우리는 정말 성공할 가능성이 있는 분들만 선별적으로 모십니다. 그렇기에 간단한 심사 과정이 있습니다.
            </p>
            <p class="text-sm font-bold">
                더 이상 시행착오로 귀중한 시간과 자원을 낭비하지 마세요. 
                <span class="highlighted-text">당신의 시간은 돈입니다.</span>
            </p>
        </div>
        
        <div class="limited-spots mt-6 pulse">
            <p class="text-sm font-bold text-white mb-1">마지막 <span class="text-xl gradient-text">8자리</span></p>
            <p class="text-xs text-gray-400">다음 기수는 가격이 인상될 예정입니다</p>
        </div>
        
        <button class="btn btn-primary mt-4 mb-20">지금 바로 신청하기</button>
    </section>
    
    <!-- 하단 고정 CTA -->
    <div class="fixed-cta">
        <div class="flex justify-between items-center mb-2">
            <div>
                <p class="text-sm price-strike">1,500만원</p>
                <p class="text-base font-bold gradient-text">특별 조기 신청가</p>
            </div>
            <div>
                <span class="case-badge pulse">
                    마지막 8자리
                </span>
            </div>
        </div>
        <button class="btn btn-primary">지금 바로 신청하기</button>
    </div>
    
    <script>
        // 주차별 탭 기능
        document.addEventListener('DOMContentLoaded', function() {
            const weekTabs = document.querySelectorAll('.week-tab');
            const weekContents = document.querySelectorAll('.week-content');
            
            weekTabs.forEach(tab => {
                tab.addEventListener('click', function() {
                    // 모든 탭 비활성화
                    weekTabs.forEach(t => t.classList.remove('active'));
                    weekContents.forEach(c => c.classList.remove('active'));
                    
                    // 클릭한 탭 활성화
                    this.classList.add('active');
                    const weekNumber = this.getAttribute('data-week');
                    document.getElementById('week-' + weekNumber).classList.add('active');
                });
            });
        });
    </script>
</body>
</html>
