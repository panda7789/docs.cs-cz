---
title: Souhrn typů trasování
ms.date: 03/30/2017
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
ms.openlocfilehash: 8ed6dceb19caa52f928f285064c60337e3f15a87
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674843"
---
# <a name="trace-type-summary"></a>Souhrn typů trasování
[Úrovně zdrojového přenosu](xref:System.Diagnostics.SourceLevels) definuje různé úrovně trasování: Kritická, Chyba, Upozornění, Informace `ActivityTracing` a Verbose, stejně jako poskytuje popis příznaku, který přepíná výstup hranice trasování a události přenosu aktivity.  
  
 Můžete také <xref:System.Diagnostics.TraceEventType> zkontrolovat typy trasování, které mohou <xref:System.Diagnostics>být emitovány z .  
  
 V následující tabulce jsou uvedeny nejdůležitější.  
  
|Typ trasování|Popis|  
|----------------|-----------------|  
|Kritická|Závažná chyba nebo selhání aplikace.|  
|Chyba|Obnovitelná chyba.|  
|Upozornění|Informační zpráva.|  
|Informace|Nekritický problém.|  
|Verbose|Ladění trasování.|  
|Start|Spuštění logické jednotky zpracování.|  
|Suspend|Pozastavení logické jednotky zpracování.|  
|Obnovit|Obnovení logické jednotky zpracování.|  
|Zastavit|Zastavení logické jednotky zpracování.|  
|Přenos|Změna korelační identity.|  
  
 Aktivita je definována jako kombinace výše uvedených typů trasování.  
  
 Následuje regulární výraz, který definuje ideální aktivitu v místním oboru (zdroj trasování),  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 To znamená, že činnost musí splňovat následující podmínky.  
  
- Musí se spustit a zastavit, respektive stopami Start a Stop  
  
- Musí mít trasování přenosu bezprostředně předcházející sledování pozastavit nebo pokračovat.  
  
- Nesmí mít žádné stopy mezi Stopy spánku a Pokračovat, pokud takové stopy existují  
  
- To může mít všechny a tolik kritických / Chyba / Varování / Informace / Verbose / Transfer stopy tak dlouho, dokud jsou dodrženy předchozí podmínky  
  
 Následuje regulární výraz, který definuje ideální aktivitu v globálním rozsahu,  
  
`R+`  
  
 r je regulární výraz pro aktivitu v místním oboru. To se promítá do,  
  
`[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+`
