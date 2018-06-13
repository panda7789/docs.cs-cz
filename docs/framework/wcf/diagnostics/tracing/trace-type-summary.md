---
title: Souhrn typů trasování
ms.date: 03/30/2017
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
ms.openlocfilehash: e3bc66753dd44e1dc4c7417caf593820300f69a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486039"
---
# <a name="trace-type-summary"></a>Souhrn typů trasování
[Zdroj úrovně](http://go.microsoft.com/fwlink/?LinkID=94943) definuje různé úrovně trasování: kritická, chyba, upozornění, informace a podrobné, stejně jako obsahuje popis `ActivityTracing` příznak, které přepíná výstup trasování událostí pro přenos hranice a aktivity.  
  
 Můžete také zkontrolovat [typ TraceEventType](http://go.microsoft.com/fwlink/?LinkId=95169) pro typy trasování, které můžou být vygenerované z <xref:System.Diagnostics>.  
  
 Následující tabulka uvádí nejdůležitější ty.  
  
|Typ trasování|Popis|  
|----------------|-----------------|  
|Kritická|Závažná chyba nebo aplikaci k chybě.|  
|Chyba|Nezotavitelnou chybu.|  
|Upozornění|Informační zpráva.|  
|Informace o|Nekritická problém.|  
|Verbose|Ladění trasování.|  
|Spustit|Spouštění logické jednotky zpracování.|  
|Pozastavit|Pozastavení logické jednotky zpracování.|  
|Resume|Obnovení logické jednotky zpracování.|  
|Zastavit|Zastavování logické jednotky zpracování.|  
|Přenos|Změna identity korelace.|  
  
 Aktivita je definován jako kombinace výše uvedených typů trasování.  
  
 Toto je regulární výraz, který definuje ideální aktivitu v oboru místní (Zdroj trasování)  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 To znamená, že aktivita musí splňovat následující podmínky.  
  
-   Musí začínat a zastavte v uvedeném pořadí spouštění a zastavování trasování  
  
-   Musí mít přenos trasování bezprostředně předcházející pozastavit nebo obnovit trasování  
  
-   Nesmí obsahovat žádné trasování mezi pozastavení a obnovení trasování, pokud existují takové trasování  
  
-   Také je možné vysledovat předchozích podmínek může mít všechny a libovolný počet trasování kritické/chyby nebo upozornění nebo informace nebo Verbose/přenos  
  
 Toto je regulární výraz, který definuje ideální aktivitu v globálním oboru  
  
```  
R+   
```  
  
 s R se regulární výraz pro aktivitu v místní rozsah. To znamená, že  
  
```  
[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+  
```
