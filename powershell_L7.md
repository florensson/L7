# PowerShell-lektion: Livekodning och Praktik för IT-tekniker

## Tidsram: 2,5–3 timmar (inkl. raster)

## Syfte
- Visa praktisk PowerShell-användning för IT-tekniker
- Koda live och låt eleverna följa och testa
- Ge exempel på processhantering, nätverk, tjänster, miljövariabler och filhantering

---

## Del 1 – Livekodning: Exempel att visa och testa

### 1. Lista och analysera processer (CPU)
```powershell
Get-Process | Sort-Object CPU -Descending | Select-Object -First 10 | Format-Table
```

### 2. Filtrera tjänster som körs
```powershell
Get-Service | Where-Object {$_.Status -eq 'Running'} | Format-Table
```

### 3. Spara tjänster till fil
```powershell
Get-Service | Where-Object {$_.Status -eq 'Running'} | Out-File running_services.txt
```

### 4. Testa nätverksanslutning (ping)
```powershell
Test-Connection -ComputerName 8.8.8.8 -Count 4
```

### 5. Sök efter stora filer i C:\
```powershell
Get-ChildItem C:\ -Recurse | Where-Object {$_.Length -gt 100MB} | Sort-Object Length -Descending
```

### 6. Läsa alla miljövariabler
```powershell
Get-Item env:
```

### 7. Skapa/ändra miljövariabel
```powershell
[System.Environment]::SetEnvironmentVariable("TestVar", "Hello World")
```

---

## Del 2 – Praktisk övning i par (ca 45 min)
- Välj en eller flera av ovanstående exempel och skapa egna variationer
- Kombinera dem till ett större skript (t.ex. ping + loggning, processanalys + rapport)
- Lägg till `try/catch`-block för att hantera fel

---

## Del 3 – Livekodning: Kombinera idéer
- Skapa ett skript som:
  - Hittar topp 5 CPU-processer
  - Sparar resultaten till en fil
  - Läser in och visar filen
```powershell
$topProcesses = Get-Process | Sort-Object CPU -Descending | Select-Object -First 5
$topProcesses | Out-File top_processes.txt
Get-Content top_processes.txt
```

---

## Del 4 – Reflektion och avslutning
- Vad lärde ni er idag?
- Vilka kommandon var mest användbara?
- Hur kan detta användas i praktiken?