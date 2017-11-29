---
title: "Souhrn typů trasování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d8e82f153e996ffebc2aba614f42c5cfa949e7ec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
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
