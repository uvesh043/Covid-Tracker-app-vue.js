 <div class="box">
    <div class="box-1">
      <h1>Cases</h1>
      <div class="box-11">
        <h2>New: </h2>
        <h2>{{ numberWithCommas(status.NewConfirmed) }}</h2>
      </div>
      <div class="box-12">
        <h2>Confirmed: </h2>
        <h2>{{ numberWithCommas(status.TotalConfirmed) }}</h2>
      </div>
    </div>

    <div class="box-2">
      <h2>Deaths:</h2>
      <h2>NewDeaths</h2>
      <h1>{{ numberWithCommas(status.NewDeaths) }}</h1>
      <h2>TotalDeaths</h2>
      <h1>{{ numberWithCommas(status.TotalDeaths) }}</h1>
    </div>
  </div>