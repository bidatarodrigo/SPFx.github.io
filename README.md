<div style="max-width: 320px; margin: 0 auto;">
  <div style="
    border: 1px solid #e5e6ea;
    border-radius: 16px;
    box-shadow: 0 10px 24px rgba(0,0,0,.10);
    overflow: hidden;
    background: white;
  ">
    <!-- Cabeçalho -->
    <div id="calendar-header" style="
      background: #8bd1ff;
      color: white;
      text-align: center;
      padding: 18px 14px 24px;
    ">
      <div id="weekday" style="font-size: .8rem; letter-spacing: .06em;">
        SEGUNDA-FEIRA
      </div>
      <div id="day-big" style="font-size: 4.2rem; line-height: 1; font-weight: 700; margin-top: 8px;">
        17
      </div>
    </div>
    
    <!-- Corpo -->
    <div style="padding: 12px 14px 16px;">
      <div style="display: flex; justify-content: center; align-items: center; gap: 8px; margin-bottom: 8px;">
        <button onclick="prevMonth()" style="border: 1px solid #e5e6ea; background: #f0f2f5; border-radius: 10px; padding: 6px 9px; cursor: pointer;">
          ‹
        </button>
        <div id="month-name" style="font-weight: 600;">
          Março 2025
        </div>
        <button onclick="nextMonth()" style="border: 1px solid #e5e6ea; background: #f0f2f5; border-radius: 10px; padding: 6px 9px; cursor: pointer;">
          ›
        </button>
      </div>
      
      <!-- Dias da semana -->
      <div style="display: grid; grid-template-columns: repeat(7, 1fr); gap: 6px; margin-bottom: 8px;">
        <div style="text-align: center; font-size: .72rem; color: #7a7a7a;">D</div>
        <div style="text-align: center; font-size: .72rem; color: #7a7a7a;">S</div>
        <div style="text-align: center; font-size: .72rem; color: #7a7a7a;">T</div>
        <div style="text-align: center; font-size: .72rem; color: #7a7a7a;">Q</div>
        <div style="text-align: center; font-size: .72rem; color: #7a7a7a;">Q</div>
        <div style="text-align: center; font-size: .72rem; color: #7a7a7a;">S</div>
        <div style="text-align: center; font-size: .72rem; color: #7a7a7a;">S</div>
      </div>
      
      <!-- Grade de dias -->
      <div id="calendar-grid" style="display: grid; grid-template-columns: repeat(7, 1fr); gap: 6px;">
        <!-- JavaScript preencherá aqui -->
      </div>
      
      <div style="margin-top: 10px; text-align: center;">
        <button onclick="goToday()" style="
          background: #0078D4;
          color: white;
          border: none;
          border-radius: 10px;
          padding: 8px 16px;
          cursor: pointer;
        ">
          Hoje
        </button>
      </div>
    </div>
  </div>
</div>

<script>
  // JavaScript simplificado
  let currentDate = new Date();
  
  function renderCalendar() {
    const monthNames = ["Janeiro", "Fevereiro", "Março", "Abril", "Maio", "Junho",
      "Julho", "Agosto", "Setembro", "Outubro", "Novembro", "Dezembro"];
    
    const weekdays = ["DOMINGO", "SEGUNDA-FEIRA", "TERÇA-FEIRA", "QUARTA-FEIRA", 
      "QUINTA-FEIRA", "SEXTA-FEIRA", "SÁBADO"];
    
    // Atualizar cabeçalho
    document.getElementById('weekday').textContent = weekdays[currentDate.getDay()];
    document.getElementById('day-big').textContent = currentDate.getDate();
    document.getElementById('month-name').textContent = 
      `${monthNames[currentDate.getMonth()]} ${currentDate.getFullYear()}`;
    
    // Renderizar grade (simplificado)
    const grid = document.getElementById('calendar-grid');
    grid.innerHTML = '';
    
    // Exemplo: apenas mostrar 1-31
    for (let i = 1; i <= 31; i++) {
      const day = document.createElement('div');
      day.style.textAlign = 'center';
      day.style.padding = '8px 0';
      day.style.borderRadius = '10px';
      day.textContent = i;
      
      if (i === currentDate.getDate()) {
        day.style.background = 'rgba(0,120,212,.12)';
        day.style.border = '2px solid #0078D4';
      }
      
      grid.appendChild(day);
    }
  }
  
  function prevMonth() {
    currentDate.setMonth(currentDate.getMonth() - 1);
    renderCalendar();
  }
  
  function nextMonth() {
    currentDate.setMonth(currentDate.getMonth() + 1);
    renderCalendar();
  }
  
  function goToday() {
    currentDate = new Date();
    renderCalendar();
  }
  
  // Inicializar
  renderCalendar();
</script>
