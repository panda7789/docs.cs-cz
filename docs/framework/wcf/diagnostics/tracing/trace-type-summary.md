---
title: Souhrn typů trasování
ms.date: 03/30/2017
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
ms.openlocfilehash: 73777df2b58b14947c416ce409bcb42d439499ec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61925148"
---
# <a name="trace-type-summary"></a>Souhrn typů trasování
[Zdrojové úrovně](https://go.microsoft.com/fwlink/?LinkID=94943) definuje různé úrovně trasování: Kritická chyba, upozornění, informace a Verbose, stejně jako obsahuje popis `ActivityTracing` příznak, které přepíná výstup trasování událostí pro přenos hranice a aktivity.  
  
 Můžete také zkontrolovat [parametrem TraceEventType](https://go.microsoft.com/fwlink/?LinkId=95169) pro typy trasování, které může být generována z <xref:System.Diagnostics>.  
  
 V následující tabulce jsou uvedeny nejdůležitější ty.  
  
|Typ sledování|Popis|  
|----------------|-----------------|  
|Kritická|Závažná chyba nebo aplikaci k chybě.|  
|Chyba|Došlo k opravitelné chybě.|  
|Upozornění|Informační zpráva.|  
|Informace o|Nekritická problém.|  
|Podrobnosti|Ladění trasování.|  
|Spustit|Spouští se zpracování logické jednotky.|  
|Pozastavit|Pozastavení logické jednotky zpracování.|  
|Resume|Obnovení logické jednotky zpracování.|  
|Zastavit|Zastavuje se logické jednotky zpracování.|  
|Přenos|Změna identity korelace.|  
  
 Aktivita je definován jako kombinace výše uvedených typů trasování.  
  
 Tady je regulární výraz, který definuje ideální aktivitu v oboru místní (Zdroj trasování)  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 To znamená, že aktivita musí splňovat následující podmínky.  
  
- Musí začínat a zastavte v uvedeném pořadí spouštění a zastavování trasování  
  
- Musí mít přenos trasování bezprostředně před pozastavení nebo obnovení činnosti trasování  
  
- Nesmí mít žádné trasování mezi pozastavit a obnovit trasování, pokud existují tato trasování  
  
- Tak dlouho, dokud jsou dodržovány předchozích podmínek může mít libovolný a libovolný počet kritických/Chyba/upozornění / / Verbose/přenosu informací trasování  
  
 Tady je regulární výraz, který definuje ideální aktivitu v globálním oboru  
  
```  
R+   
```  
  
 s R se regulární výraz pro aktivitu v místním oboru. Výsledkem je,  
  
```  
[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+  
```
