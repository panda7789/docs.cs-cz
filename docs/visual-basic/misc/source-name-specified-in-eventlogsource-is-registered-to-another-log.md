---
title: Zadaný v EventLogSource název zdroje je registrován protokolu stanovené v EventLogName
ms.date: 07/20/2015
ms.assetid: 7317e100-098b-408d-86e5-7c74cf8558c7
ms.openlocfilehash: dc4c8f212de61a304f04c81d81d2e75c490450ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="source-name-specified-in-eventlogsource-is-registered-to-a-log-other-than-that-specified-in-eventlogname"></a>Zadaný v EventLogSource název zdroje je registrován protokolu stanovené v EventLogName
`EventLog` Se pokouší o odkazovat na zdroj, který je zaregistrován jiný protokol. Pokud píšete položky do protokolu událostí, je nutné zadat <xref:System.Diagnostics.EventLog.Source%2A> vlastnost. <xref:System.Diagnostics.EventLog.Source%2A> Vlastnost zaregistruje příslušné součásti se v protokolu událostí jako platný zdroj položek. Jednoho zdroje může být přidružen k (a tedy zapisovat položky k) jenom jeden protokol událostí v čase.  
  
 Ve výchozím nastavení, pokud se pokusíte zapsat záznam bez nejprve nutnosti zaregistrovat příslušné součásti jako platný zdroj, systém automaticky registruje zdroj protokolu událostí, pomocí hodnoty <xref:System.Diagnostics.EventLog.Source%2A> vlastnost jako zdrojový řetězec.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Zkontrolujte, zda že zdroj je zaregistrován v správné protokolu. Chcete-li to provést, použijte <xref:System.Diagnostics.EventLog.CreateEventSource%2A> metoda nebo jednoho z jeho přetížení pro zadejte řetězec, který jednoznačně identifikuje příslušné součásti do protokolu událostí.  
  
## <a name="see-also"></a>Viz také  
 [Správa protokolů událostí](http://msdn.microsoft.com/library/35f53238-bdd2-417b-acd8-2fd9f7397f18)  
 [Odkazy v protokolu událostí](http://msdn.microsoft.com/library/4af0661c-6c96-49f4-961d-b26ed9bc3e87)  
 [Postupy: Přidání aplikace jako zdroj položek protokolu událostí](http://msdn.microsoft.com/library/948ff920-a739-4e66-a191-ee951512d42c)  
 [Postupy: odebrání zdroje událostí](http://msdn.microsoft.com/library/bc66c900-4b8a-426a-b8e2-17031a20167e)
