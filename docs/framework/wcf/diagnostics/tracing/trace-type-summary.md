---
title: Souhrn typů trasování
ms.date: 03/30/2017
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
ms.openlocfilehash: 8f54f71ef63338708a29fac5557c7c7e8f257f58
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856010"
---
# <a name="trace-type-summary"></a>Souhrn typů trasování
[Zdrojové úrovně](https://go.microsoft.com/fwlink/?LinkID=94943) definují různé úrovně trasování: Kritická, chyba, upozornění, informace a podrobné a také poskytuje popis `ActivityTracing` příznaku, který přepíná výstup událostí pro trasování a přenos aktivity.  
  
 Můžete také zkontrolovat [TraceEventType](https://go.microsoft.com/fwlink/?LinkId=95169) pro typy trasování, ze <xref:System.Diagnostics>kterých lze generovat.  
  
 V následující tabulce jsou uvedeny nejdůležitější ty.  
  
|Typ trasování|Popis|  
|----------------|-----------------|  
|Kritická|Závažná chyba nebo selhání aplikace|  
|Chyba|Obnovitelná chyba.|  
|Upozornění|Informační zpráva.|  
|Informace o|Nekritický problém.|  
|Podrobnosti|Trasování ladění.|  
|Spustit|Spuštění logické jednotky zpracování.|  
|Pozastavit|Pozastavení logické jednotky zpracování.|  
|Resume|Obnovení logické jednotky zpracování.|  
|Zastavit|Zastavuje se logická jednotka zpracování.|  
|Přenos|Změna identity korelace.|  
  
 Aktivita je definována jako kombinace typů trasování výše.  
  
 Následuje regulární výraz, který definuje ideální aktivitu v oboru místního (zdroje trasování),  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 To znamená, že aktivita musí splňovat následující podmínky.  
  
- Musí začínat a zastavovat trasování spuštění a zastavení.  
  
- Musí mít trasování přenosu hned před přerušením nebo obnovením trasování.  
  
- Nesmí obsahovat žádné trasování mezi trasováním pozastavení a obnovení, pokud taková trasování existují.  
  
- Může mít libovolné a tolik kritických/chyb/upozornění/informací/podrobných trasování/přenosů, pokud jsou splněny předchozí podmínky.  
  
 Následuje regulární výraz, který definuje ideální aktivitu v globálním oboru.  
  
`R+`  
  
 v jazyce R je regulární výraz aktivity v místním oboru. To se týká,  
  
`[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+`
