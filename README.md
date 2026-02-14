<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no, viewport-fit=cover">
    <title>Квиз: Профессии в строительстве</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
            -webkit-tap-highlight-color: transparent;
        }

        body {
            background: #e6eaf0;
            background-image: radial-gradient(circle at 10% 20%, rgba(210, 225, 240, 0.5) 0%, transparent 30%),
                              radial-gradient(circle at 90% 70%, rgba(180, 200, 220, 0.4) 0%, transparent 40%);
            display: flex;
            align-items: center;
            justify-content: center;
            min-height: 100vh;
            padding: 20px;
        }

        .container {
            width: 100%;
            max-width: 780px;
            background: white;
            border-radius: 40px;
            padding: 32px 28px;
            box-shadow: 0 20px 40px -10px rgba(0, 20, 40, 0.15);
            transition: none;
        }

        .title-main {
            font-size: 2rem;
            font-weight: 700;
            color: #1e3b5c;
            letter-spacing: -0.02em;
            margin-bottom: 8px;
            line-height: 1.2;
        }

        .title-accent {
            color: #6387a5;
            font-weight: 500;
            font-size: 1rem;
            text-transform: uppercase;
            letter-spacing: 2px;
            margin-bottom: 24px;
            border-bottom: 2px solid #e1ecf4;
            padding-bottom: 16px;
        }

        .badge-soft {
            display: inline-block;
            background: #f0f6fa;
            color: #2c4c6b;
            padding: 6px 16px;
            border-radius: 50px;
            font-size: 0.8rem;
            font-weight: 600;
            letter-spacing: 0.5px;
        }

        .card {
            background: #fafcff;
            border-radius: 28px;
            padding: 24px;
            margin-bottom: 24px;
            border: 1px solid rgba(200, 215, 230, 0.6);
            box-shadow: 0 8px 0 rgba(180, 200, 215, 0.2);
        }

        .input-wrapper {
            background: white;
            border-radius: 20px;
            border: 1.5px solid #dae2ed;
            padding: 4px 20px;
            display: flex;
            align-items: center;
            transition: all 0.2s;
            box-shadow: 0 2px 0 #dae2ed;
        }

        .input-wrapper:focus-within {
            border-color: #5c9ead;
            box-shadow: 0 4px 0 #b8d4de;
        }

        .input-wrapper i {
            color: #7f9eb5;
            font-size: 1.1rem;
        }

        .input-field {
            width: 100%;
            padding: 16px 12px;
            border: none;
            font-size: 1rem;
            background: transparent;
            font-weight: 500;
        }

        .input-field:focus {
            outline: none;
        }

        .btn {
            width: 100%;
            padding: 18px 24px;
            border: none;
            border-radius: 40px;
            font-size: 1rem;
            font-weight: 700;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 12px;
            cursor: pointer;
            transition: all 0.15s ease;
            background: white;
            border: 1.5px solid #cbd7e3;
            color: #2c4c6b;
            box-shadow: 0 6px 0 #cbd7e3;
        }

        .btn:active {
            transform: translateY(4px);
            box-shadow: 0 2px 0 #cbd7e3;
        }

        .btn-primary {
            background: #2c4c6b;
            border-color: #1d364a;
            color: white;
            box-shadow: 0 6px 0 #1d364a;
        }

        .btn-primary i {
            color: white;
        }

        .rule-chip {
            display: flex;
            align-items: center;
            gap: 16px;
            padding: 16px 0;
            border-bottom: 1px dashed #d7e0e9;
        }

        .rule-chip:last-child {
            border-bottom: none;
        }

        .rule-chip i {
            width: 32px;
            height: 32px;
            background: #e9f0f5;
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: #2c4c6b;
        }

        .stats-bar {
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: #f0f6fa;
            border-radius: 60px;
            padding: 8px 8px 8px 20px;
            margin-bottom: 24px;
        }

        .question-pill {
            background: white;
            padding: 8px 20px;
            border-radius: 40px;
            font-weight: 700;
            color: #1e3b5c;
            box-shadow: 0 2px 0 #d0dfe9;
        }

        .timer-pill {
            background: #ffe6cc;
            padding: 8px 20px;
            border-radius: 40px;
            display: flex;
            align-items: center;
            gap: 8px;
            font-weight: 700;
            color: #b35e1a;
            box-shadow: 0 2px 0 #e6c9b0;
        }

        .timer-pill i {
            color: #cc7f3a;
        }

        .progress-track {
            height: 8px;
            background: #e5ecf1;
            border-radius: 20px;
            margin-bottom: 24px;
        }

        .progress-fill {
            height: 100%;
            width: 0%;
            background: #5c9ead;
            border-radius: 20px;
            transition: width 0.2s;
        }

        .question-box {
            background: #f4f9ff;
            border-radius: 28px;
            padding: 28px;
            margin-bottom: 28px;
            border: 1px solid #e2ecf5;
            font-size: 1.18rem;
            font-weight: 600;
            line-height: 1.5;
            color: #1a3344;
            box-shadow: inset 0 -2px 0 #d4e2ed;
        }

        .answers-grid {
            display: flex;
            flex-direction: column;
            gap: 12px;
            margin-bottom: 28px;
        }

        @media (min-width: 680px) {
            .answers-grid {
                display: grid;
                grid-template-columns: 1fr 1fr;
                gap: 14px;
            }
        }

        .answer-item {
            background: white;
            border: 1.5px solid #dbe3ec;
            border-radius: 20px;
            padding: 16px 20px;
            display: flex;
            align-items: center;
            gap: 16px;
            cursor: pointer;
            transition: all 0.12s;
            box-shadow: 0 4px 0 #dbe3ec;
        }

        .answer-item:active {
            transform: translateY(2px);
            box-shadow: 0 2px 0 #dbe3ec;
        }

        .answer-item.selected {
            background: #e8f2fc;
            border-color: #5c9ead;
            box-shadow: 0 4px 0 #5c9ead;
        }

        .answer-item.correct {
            background: #e2f3e4;
            border-color: #4a8b6e;
            box-shadow: 0 4px 0 #4a8b6e;
        }

        .answer-item.incorrect {
            background: #ffe9e9;
            border-color: #d18a8a;
            box-shadow: 0 4px 0 #d18a8a;
        }

        .answer-letter {
            width: 44px;
            height: 44px;
            background: #eef4f8;
            border-radius: 16px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 800;
            font-size: 1.2rem;
            color: #1e3b5c;
            flex-shrink: 0;
            border: 1px solid #d0dde8;
        }

        .answer-item.selected .answer-letter {
            background: #5c9ead;
            color: white;
            border-color: #5c9ead;
        }

        .result-block {
            text-align: center;
            background: #f4f9ff;
            border-radius: 48px;
            padding: 32px 24px;
            margin-bottom: 24px;
        }

        .result-number {
            font-size: 5rem;
            font-weight: 800;
            color: #2c4c6b;
            line-height: 1;
            margin: 16px 0;
        }

        .stat-panel {
            background: white;
            border-radius: 28px;
            padding: 24px;
            border: 1px solid #e3ecf3;
            margin: 24px 0;
        }

        .stat-line {
            display: flex;
            justify-content: space-between;
            padding: 14px 0;
            border-bottom: 1px solid #ecf2f7;
        }

        .stat-line:last-child {
            border-bottom: none;
        }

        .modal-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(30, 50, 70, 0.7);
            backdrop-filter: blur(4px);
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 1000;
            opacity: 0;
            visibility: hidden;
            transition: 0.15s;
        }

        .modal-overlay.active {
            opacity: 1;
            visibility: visible;
        }

        .modal-card {
            background: white;
            border-radius: 48px;
            width: 90%;
            max-width: 400px;
            padding: 32px 28px;
            box-shadow: 0 30px 50px rgba(0,0,0,0.2);
            transform: scale(0.95);
            transition: 0.2s;
        }

        .modal-overlay.active .modal-card {
            transform: scale(1);
        }

        .modal-buttons {
            display: flex;
            gap: 14px;
            margin-top: 28px;
        }

        .modal-btn {
            flex: 1;
            padding: 16px;
            border: none;
            border-radius: 30px;
            font-weight: 700;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
            cursor: pointer;
            background: #f0f4f9;
            border: 1px solid #cddae5;
            box-shadow: 0 4px 0 #cddae5;
            transition: 0.05s;
        }

        .modal-btn:active {
            transform: translateY(3px);
            box-shadow: 0 1px 0 #cddae5;
        }

        .modal-btn.yes {
            background: #2c4c6b;
            color: white;
            border-color: #1d364a;
            box-shadow: 0 4px 0 #1d364a;
        }

        .timeout-box {
            background: #fff3e6;
            border-radius: 20px;
            padding: 14px;
            margin-bottom: 20px;
            color: #b85c1a;
            font-weight: 600;
            display: none;
        }

        .timeout-box.show {
            display: block;
        }

        .player-chip {
            background: white;
            border-radius: 40px;
            padding: 10px 20px;
            display: inline-flex;
            align-items: center;
            gap: 10px;
            border: 1px solid #c8d8e5;
            font-weight: 600;
            color: #2c4c6b;
            margin-bottom: 20px;
        }

        .telegram-section {
            background: white;
            border-radius: 28px;
            padding: 24px;
            border: 1px solid #dae2ed;
            margin-top: 24px;
        }

        .telegram-btn {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 12px;
            background: #54a9eb;
            color: white;
            padding: 16px;
            border-radius: 40px;
            text-decoration: none;
            font-weight: 700;
            border: none;
            box-shadow: 0 6px 0 #2e7eb0;
            transition: 0.05s;
        }

        .telegram-btn:active {
            transform: translateY(4px);
            box-shadow: 0 2px 0 #2e7eb0;
        }

        .mobile-hint {
            text-align: center;
            color: #7f9eb5;
            font-size: 0.8rem;
            letter-spacing: 1px;
            margin-bottom: 12px;
        }

        .screen {
            display: none;
        }

        .screen.active {
            display: block;
            animation: fade 0.25s;
        }

        @keyframes fade {
            from { opacity: 0.5; transform: translateY(5px); }
            to { opacity: 1; transform: translateY(0); }
        }
    </style>
</head>
<body>
    <div class="container">
        <div id="start-screen" class="screen active">
            <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 24px;">
                <span class="badge-soft"><i class="fas fa-helmet-safety"></i> СТФ</span>
                <span class="badge-soft">КВИЗ</span>
            </div>

            <div class="title-main">
                Профессии<br>в строительстве
            </div>
            <div class="title-accent">
                29 заданий · 60 секунд
            </div>

            <div class="card" style="margin-top: 16px;">
                <div style="display: flex; align-items: center; gap: 12px; margin-bottom: 20px;">
                    <i class="fas fa-user-circle" style="font-size: 1.8rem; color: #5c9ead;"></i>
                    <span style="font-weight: 700; color: #1e3b5c;">Участник</span>
                </div>
                <div class="input-wrapper">
                    <i class="fas fa-pencil-alt"></i>
                    <input type="text" id="player-name" class="input-field" placeholder="Ваше имя" maxlength="25" autocomplete="off">
                </div>
            </div>

            <button id="start-btn" class="btn btn-primary">
                <i class="fas fa-play"></i> НАЧАТЬ
            </button>
        </div>

        <div id="rules-screen" class="screen">
            <div style="margin-bottom: 28px;">
                <span class="badge-soft"><i class="fas fa-info-circle"></i> ПРАВИЛА</span>
            </div>

            <div class="card">
                <div class="rule-chip">
                    <i class="fas fa-hourglass-half"></i>
                    <span style="font-weight: 600;">60 секунд на вопрос</span>
                </div>
                <div class="rule-chip">
                    <i class="fas fa-check-circle"></i>
                    <span style="font-weight: 600;">+1 балл за верный ответ</span>
                </div>
                <div class="rule-chip">
                    <i class="fas fa-briefcase"></i>
                    <span style="font-weight: 600;">29 вопросов о профессиях</span>
                </div>
                <div class="rule-chip">
                    <i class="fas fa-check-double"></i>
                    <span style="font-weight: 600;">Подтверждение ответа</span>
                </div>
            </div>

            <button id="rules-back-btn" class="btn" style="margin-bottom: 12px;">
                <i class="fas fa-arrow-left"></i> НАЗАД
            </button>
            <button id="start-game-btn" class="btn btn-primary">
                <i class="fas fa-play"></i> СТАРТ
            </button>
        </div>

        <div id="game-screen" class="screen">
            <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 16px;">
                <span class="player-chip" id="current-player">
                    <i class="fas fa-user"></i> ЗАГРУЗКА
                </span>
                <span class="badge-soft">ВОПРОС</span>
            </div>

            <div class="stats-bar">
                <span class="question-pill">
                    <span id="question-number">1</span>/29
                </span>
                <span class="timer-pill">
                    <i class="fas fa-stopwatch"></i> <span id="timer">60</span>с
                </span>
            </div>

            <div class="progress-track">
                <div class="progress-fill" id="progress-bar"></div>
            </div>

            <div class="timeout-box" id="timeout-message">
                <i class="fas fa-hourglass-end"></i> Время вышло — ответ не засчитан
            </div>

            <div class="question-box" id="question-text">
                Загрузка вопроса...
            </div>

            <div class="mobile-hint">
                <i class="fas fa-hand-pointer"></i> нажми на вариант → подтверди
            </div>

            <div class="answers-grid" id="options-container"></div>

            <button id="next-btn" class="btn" disabled>
                <i class="fas fa-arrow-right"></i> ДАЛЕЕ
            </button>
        </div>

        <div id="result-screen" class="screen">
            <div style="text-align: center; margin-bottom: 16px;">
                <span class="badge-soft"><i class="fas fa-flag-checkered"></i> ЗАВЕРШЕНО</span>
            </div>

            <div class="result-block">
                <div style="color: #7f9eb5; letter-spacing: 2px;">ВАШ РЕЗУЛЬТАТ</div>
                <div class="result-number" id="final-score">0</div>
                <div id="result-message" style="font-size: 1.4rem; font-weight: 700; color: #1e3b5c; margin-top: 8px;"></div>
            </div>

            <div class="stat-panel">
                <div class="stat-line">
                    <span>Игрок</span>
                    <strong id="result-player">—</strong>
                </div>
                <div class="stat-line">
                    <span>Верные ответы</span>
                    <strong id="correct-answers">0/29</strong>
                </div>
                <div class="stat-line">
                    <span>Время прохождения</span>
                    <strong id="total-time">0 с</strong>
                </div>
                <div class="stat-line">
                    <span>Дата</span>
                    <strong id="completion-date"></strong>
                </div>
            </div>

            <div class="telegram-section">
                <div style="display: flex; align-items: center; gap: 12px; margin-bottom: 16px;">
                    <i class="fab fa-telegram-plane" style="font-size: 1.5rem; color: #54a9eb;"></i>
                    <span style="font-weight: 700; color: #1e3b5c;">Отправить результат</span>
                </div>
                <a href="https://t.me/+QM7jnY2vZjozMjRi" class="telegram-btn" target="_blank">
                    <i class="fab fa-telegram"></i> TELEGRAM
                </a>
            </div>
        </div>
    </div>

    <div class="modal-overlay" id="confirmation-modal">
        <div class="modal-card">
            <div style="display: flex; justify-content: center; margin-bottom: 16px;">
                <div style="width: 56px; height: 56px; background: #eef4f8; border-radius: 20px; display: flex; align-items: center; justify-content: center;">
                    <i class="fas fa-question" style="font-size: 1.8rem; color: #5c9ead;"></i>
                </div>
            </div>
            <h3 style="text-align: center; margin-bottom: 20px; color: #1e3b5c;">Подтвердите выбор</h3>
            <div id="confirmation-text" style="background: #f7fbfe; padding: 18px; border-radius: 20px; font-size: 1rem; text-align: center;"></div>
            <div class="modal-buttons">
                <button class="modal-btn yes" id="confirm-yes">
                    <i class="fas fa-check"></i> ДА
                </button>
                <button class="modal-btn" id="confirm-no">
                    <i class="fas fa-times"></i> НЕТ
                </button>
            </div>
        </div>
    </div>

    <script>
        (function() {
            "use strict";

            const quizData = [
                { question: "Как называется специалист, который выполняет геодезические измерения, разбивку осей и контролирует точность геометрии здания на стройплощадке?", options: ["Маркшейдер", "Геодезист", "Проектировщик", "Технадзор"], correct: 1 },
                { question: "Кто отвечает за общее руководство строительством объекта, соблюдение сроков, сметы и координацию всех субподрядчиков?", options: ["Прораб", "Мастер участка", "Инженер ПТО", "Начальник строительного управления"], correct: 0 },
                { question: "Специалист, который разрабатывает раздел проекта, касающийся организации строительства и календарного графика работ — это:", options: ["Инженер-сметчик", "Инженер ПТО (производственно-технического отдела)", "Генподрядчик", "Координатор по оборудованию"], correct: 1 },
                { question: "Как называется профессия рабочего, который специализируется на сборке и разборке опалубки для монолитных бетонных работ?", options: ["Арматурщик", "Плотник-опалубщик", "Бетонщик", "Монтажник"], correct: 1 },
                { question: "Специалист, занимающийся монтажом, наладкой и обслуживанием систем вентиляции, кондиционирования и отопления — это:", options: ["Сантехник", "Кровельщик", "Монтажник МИК (монтажник внутренних инженерных систем)", "Вентиляционщик"], correct: 2 },
                { question: "Ответственность за пожарную безопасность здания на этапе проектирования и соответствие проектной документации нормам несет:", options: ["Инженер по охране труда", "Пожарный инспектор", "Инженер-проектировщик (специалист по ПБ)", "Руководитель строительства"], correct: 2 },
                { question: "Профессия рабочего, который специализируется на монтаже каркасов из легких стальных тонкостенных конструкций (ЛСТК), — это:", options: ["Монтажник стальных конструкций", "Вальцовщик", "Монтажник ЛСТК", "Арматурщик"], correct: 2 },
                { question: "Как называется специалист, который рассчитывает нагрузки на конструкции здания и проектирует его несущий каркас (колонны, балки, перекрытия)?", options: ["Архитектор", "Инженер-конструктор (расчетчик)", "Технолог", "Сметчик"], correct: 1 },
                { question: "Кто выполняет контроль качества поступающих на стройку материалов, проводит лабораторные испытания бетона, грунта?", options: ["Инженер ОТК", "Лаборант строительной лаборатории", "Инженер технического надзора заказчика", "Мастер участка"], correct: 1 },
                { question: "Как называется профессия рабочего, который укладывает асфальтобетонную смесь и работает с асфальтоукладчиком?", options: ["Дорожный рабочий", "Асфальтировщик", "Водитель катка", "Машинист асфальтоукладчика"], correct: 3 },
                { question: "Кто руководит работами на отдельном участке (например, этаже), непосредственно распределяет задания между бригадами?", options: ["Прораб", "Мастер строительных работ", "Начальник участка", "Бригадир"], correct: 1 },
                { question: "Кто отвечает за разработку и согласование документации, подтверждающей соответствие построенного объекта проекту (исполнительная документация)?", options: ["Инженер ПТО", "Геодезист", "Инженер по качеству", "Все перечисленные"], correct: 3 },
                { question: "Рабочий, который специализируется на монтаже и сварке трубопроводов высокого давления, технологических трубопроводов — это:", options: ["Сантехник", "Монтажник технологических трубопроводов", "Газосварщик", "Слесарь-монтажник"], correct: 1 },
                { question: "Специалист, занимающийся расчетом стоимости строительства, составлением локальных и объектных смет, — это:", options: ["Экономист", "Финансовый директор", "Инженер-сметчик", "Инженер ПТО"], correct: 2 },
                { question: "Профессия, связанная с монтажом и герметизацией светопрозрачных конструкций (окон, витражей, фасадного остекления), — это:", options: ["Стекольщик", "Монтажник окон", "Фасадчик", "Все перечисленные"], correct: 3 },
                { question: "Кто управляет такими машинами, как башенный кран, гусеничный или колесный экскаватор?", options: ["Водитель погрузчика", "Машинист строительной машины", "Механик", "Крановщик"], correct: 1 },
                { question: "Специалист, который проектирует и рассчитывает системы водоснабжения, канализации, водоотведения здания, — это:", options: ["Гидравлик", "Инженер-сантехник (проектировщик ВК)", "Инженер-эколог", "Слесарь-сантехник"], correct: 1 },
                { question: "Как называется профессия рабочего, занимающегося сложной высокоточной кирпичной или каменной кладкой, часто декоративной?", options: ["Каменщик", "Печник", "Облицовщик", "Архитектор-каменщик"], correct: 0 },
                { question: "Кто координирует действия всех специалистов на сложном объекте с точки зрения пространства и времени, чтобы избежать коллизий?", options: ["Главный инженер проекта", "BIM-менеджер", "Диспетчер", "Логист"], correct: 1 },
                { question: "Специалист, который занимается возведением и отделкой печей, каминов, барбекю, — это:", options: ["Каменщик", "Печник", "Огнеупорщик", "Арматурщик"], correct: 1 },
                { question: "Кто отвечает за составление и ведение графика производства работ (ГПР) с привязкой к датам и ресурсам?", options: ["Прораб", "Планировщик (инженер-планировщик)", "Начальник строительства", "Экономист"], correct: 1 },
                { question: "Рабочий, специализирующийся на устройстве покрытий из линолеума, ковролина, ламината, — это:", options: ["Паркетчик", "Отделочник", "Монтажник напольных покрытий", "Укладчик"], correct: 2 },
                { question: "Кто осуществляет авторский надзор за строительством, следя за соответствием реализации архитектурному проекту?", options: ["Технический заказчик", "Архитектор (автор проекта)", "Генеральный подрядчик", "Инженер ГАСН"], correct: 1 },
                { question: "Специалист, отвечающий за подбор, организацию доставки и складирования строительных материалов на объекте, — это:", options: ["Завхоз", "Кладовщик", "Логист (снабженец)", "Комплектовщик"], correct: 2 },
                { question: "Специалист с каким профилем подготовки факультета СТФ, скорее всего, будет работать над газификацией региона и проектированием систем отопления?", options: ["ПГС", "ИСЖС", "АД", "ПСК"], correct: 1 },
                { question: "Что является ключевым отличием BIM-менеджера от обычного инженера-проектировщика?", options: ["Работает только с чертежами в 2D", "Разрабатывает весь жизненный цикл объекта, используя информационное моделирование", "Не участвует в этапе строительства", "Отвечает исключительно за расчет сметной стоимости"], correct: 1 },
                { question: "Какое направление подготовки на факультете СТФ напрямую связано с объектами, которые уже эксплуатируются, и включает в себя задачи по их обследованию, ремонту и предотвращению аварий?", options: ["СУЗ", "ПГС", "АД", "Все перечисленные"], correct: 3 },
                { question: "Студент какого направления, скорее всего, будет проходить практику в независимой испытательной лаборатории Политеха, проверяя качество бетона или кирпича?", options: ["ПГС", "ИСЖС", "ПСК", "СУЗ"], correct: 2 },
                { question: "Какую стипендию будет получать студент, который является активистом факультета (участвует в организации мероприятий), но при этом сдал сессию только на «хорошо»?", options: ["Только базовую академическую", "Повышенную стипендию за достижения в общественной деятельности", "Социальную повышенную стипендию", "Он не будет получать стипендию, так как нет отличных оценок"], correct: 1 }
            ];

            const $ = document;
            const screens = {
                start: $.getElementById('start-screen'),
                rules: $.getElementById('rules-screen'),
                game: $.getElementById('game-screen'),
                result: $.getElementById('result-screen')
            };

            const playerNameInput = $.getElementById('player-name');
            const currentPlayerEl = $.getElementById('current-player');
            const resultPlayerEl = $.getElementById('result-player');
            const qNumberEl = $.getElementById('question-number');
            const qTextEl = $.getElementById('question-text');
            const optionsContainer = $.getElementById('options-container');
            const progressBar = $.getElementById('progress-bar');
            const timeoutMsg = $.getElementById('timeout-message');
            const timerEl = $.getElementById('timer');
            const nextBtn = $.getElementById('next-btn');
            const finalScoreEl = $.getElementById('final-score');
            const correctAnswersEl = $.getElementById('correct-answers');
            const totalTimeEl = $.getElementById('total-time');
            const completionDateEl = $.getElementById('completion-date');
            const resultMsgEl = $.getElementById('result-message');
            const startBtn = $.getElementById('start-btn');
            const rulesBackBtn = $.getElementById('rules-back-btn');
            const startGameBtn = $.getElementById('start-game-btn');
            const modal = $.getElementById('confirmation-modal');
            const modalText = $.getElementById('confirmation-text');
            const confirmYes = $.getElementById('confirm-yes');
            const confirmNo = $.getElementById('confirm-no');

            let state = {
                currentIdx: 0,
                score: 0,
                playerName: '',
                timeLeft: 60,
                timerId: null,
                startTime: 0,
                selectedOpt: null,
                answered: false,
                totalTime: 0,
                pendingEl: null,
                pendingIdx: null
            };

            function showScreen(name) {
                Object.values(screens).forEach(s => s.classList.remove('active'));
                screens[name].classList.add('active');
                if (name === 'game') state.startTime = Date.now();
            }

            function stopTimer() {
                if (state.timerId) clearInterval(state.timerId);
                state.timerId = null;
            }

            function startTimer() {
                stopTimer();
                state.timeLeft = 60;
                timerEl.textContent = state.timeLeft;
                
                state.timerId = setInterval(() => {
                    state.timeLeft--;
                    timerEl.textContent = state.timeLeft;
                    
                    if (state.timeLeft <= 0) {
                        stopTimer();
                        if (!state.answered) {
                            timeoutMsg.classList.add('show');
                            document.querySelectorAll('.answer-item').forEach(o => o.style.pointerEvents = 'none');
                            setTimeout(() => {
                                timeoutMsg.classList.remove('show');
                                nextQuestion();
                            }, 2000);
                        }
                    }
                }, 1000);
            }

            function loadQuestion() {
                const q = quizData[state.currentIdx];
                qNumberEl.textContent = state.currentIdx + 1;
                qTextEl.textContent = q.question;
                progressBar.style.width = `${((state.currentIdx + 1) / quizData.length) * 100}%`;
                
                optionsContainer.innerHTML = '';
                const letters = ['А', 'Б', 'В', 'Г'];
                
                q.options.forEach((opt, i) => {
                    const optEl = $.createElement('div');
                    optEl.className = 'answer-item';
                    optEl.dataset.index = i;
                    optEl.innerHTML = `<span class="answer-letter">${letters[i]}</span><span style="flex:1; font-weight: 500; color: #1e3b5c;">${opt}</span>`;
                    
                    optEl.addEventListener('click', (e) => {
                        e.preventDefault();
                        if (!state.answered) showModal(optEl, i);
                    });
                    
                    optionsContainer.appendChild(optEl);
                });
                
                nextBtn.disabled = true;
                state.selectedOpt = null;
                state.answered = false;
                state.pendingEl = null;
                state.pendingIdx = null;
                
                startTimer();
            }

            function showModal(el, idx) {
                if (state.answered) return;
                state.pendingEl = el;
                state.pendingIdx = idx;
                const letter = ['А', 'Б', 'В', 'Г'][idx];
                const text = el.querySelector('span:last-child').textContent;
                modalText.innerHTML = `<strong style="color:#5c9ead;">${letter}</strong> · ${text.substring(0, 35)}...`;
                modal.classList.add('active');
            }

            function hideModal() {
                modal.classList.remove('active');
            }

            function confirmAnswer() {
                if (state.pendingEl && state.pendingIdx !== null) {
                    document.querySelectorAll('.answer-item').forEach(o => o.classList.remove('selected'));
                    state.pendingEl.classList.add('selected');
                    state.selectedOpt = state.pendingIdx;
                    nextBtn.disabled = false;
                }
                hideModal();
            }

            function cancelSelection() {
                if (state.pendingEl) state.pendingEl.classList.remove('selected');
                state.pendingEl = null;
                state.pendingIdx = null;
                state.selectedOpt = null;
                hideModal();
            }

            function checkAnswer() {
                if (state.selectedOpt === null || state.answered) return;
                
                state.answered = true;
                stopTimer();
                
                const q = quizData[state.currentIdx];
                const options = document.querySelectorAll('.answer-item');
                
                options.forEach(opt => opt.style.pointerEvents = 'none');
                
                options.forEach((opt, i) => {
                    if (i === q.correct) {
                        opt.classList.add('correct');
                    } else if (i === state.selectedOpt && i !== q.correct) {
                        opt.classList.add('incorrect');
                    }
                });
                
                if (state.selectedOpt === q.correct) {
                    state.score++;
                }
            }

            function nextQuestion() {
                if (!state.answered && state.selectedOpt !== null) {
                    checkAnswer();
                    return;
                }
                
                state.currentIdx++;
                
                if (state.currentIdx < quizData.length) {
                    loadQuestion();
                } else {
                    finishGame();
                }
            }

            function finishGame() {
                stopTimer();
                
                state.totalTime = Math.floor((Date.now() - state.startTime) / 1000);
                const percent = Math.round((state.score / quizData.length) * 100);
                
                finalScoreEl.textContent = state.score;
                correctAnswersEl.textContent = `${state.score}/${quizData.length}`;
                totalTimeEl.textContent = `${state.totalTime} с`;
                resultPlayerEl.textContent = state.playerName || 'Участник';
                
                const now = new Date();
                completionDateEl.textContent = now.toLocaleDateString('ru-RU', { 
                    day: 'numeric', month: 'numeric', hour: '2-digit', minute: '2-digit' 
                });
                
                if (percent >= 90) resultMsgEl.textContent = 'Ведущий инженер';
                else if (percent >= 70) resultMsgEl.textContent = 'Прораб';
                else if (percent >= 50) resultMsgEl.textContent = 'Мастер';
                else resultMsgEl.textContent = 'Стажёр';
                
                showScreen('result');
            }

            function initGame() {
                state.currentIdx = 0;
                state.score = 0;
                state.selectedOpt = null;
                state.answered = false;
                state.totalTime = 0;
                state.pendingEl = null;
                state.pendingIdx = null;
                
                stopTimer();
                timeoutMsg.classList.remove('show');
                loadQuestion();
                currentPlayerEl.innerHTML = `<i class="fas fa-user"></i> ${state.playerName || 'Участник'}`;
            }

            startBtn.addEventListener('click', () => {
                state.playerName = playerNameInput.value.trim() || 'Участник';
                showScreen('rules');
            });
            
            rulesBackBtn.addEventListener('click', () => showScreen('start'));
            
            startGameBtn.addEventListener('click', () => {
                showScreen('game');
                initGame();
            });
            
            nextBtn.addEventListener('click', nextQuestion);
            
            confirmYes.addEventListener('click', confirmAnswer);
            confirmNo.addEventListener('click', cancelSelection);
            
            modal.addEventListener('click', (e) => {
                if (e.target === modal) cancelSelection();
            });
        })();
    </script>
</body>
</html>
