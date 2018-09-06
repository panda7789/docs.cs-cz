---
title: Zadaný v EventLogSource název zdroje je zaregistrovaný do protokolu, než je zadaná v EventLogName
ms.date: 07/20/2015
ms.assetid: 7317e100-098b-408d-86e5-7c74cf8558c7
ms.openlocfilehash: 03fcc41b0fbb84233aa037d7af17d168050a98b6
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43731959"
---
# <a name="source-name-specified-in-eventlogsource-is-registered-to-a-log-other-than-that-specified-in-eventlogname"></a>Zadaný v EventLogSource název zdroje je zaregistrovaný do protokolu, než je zadaná v EventLogName
`EventLog` Se pokouší odkazovat na zdroj, který je registrovaný pro jiný protokol. Pokud vytváříte položky do protokolu událostí, je nutné zadat <xref:System.Diagnostics.EventLog.Source%2A> vlastnost. <xref:System.Diagnostics.EventLog.Source%2A> Vlastnost zaregistruje vaše komponenta se do protokolu událostí jako platný zdroj položky. Jeden zdroj může být spojen s (a proto zapisovat položky do) jenom jeden protokol událostí současně.  
  
 Ve výchozím nastavení, pokud se pokusíte pro zápis záznamu, aniž nejprve registraci komponenty jako platný zdroj, systém automaticky registruje zdroj protokolu událostí, použití hodnoty <xref:System.Diagnostics.EventLog.Source%2A> vlastnost jako zdrojový řetězec.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Zajistěte, aby že zdroj je registrován do správné protokolu. Chcete-li to provést, použijte <xref:System.Diagnostics.EventLog.CreateEventSource%2A> metody nebo jeden z jejich přetížení zadat řetězec, který jednoznačně identifikuje vaše komponenta do protokolu událostí.  
  
## <a name="see-also"></a>Viz také  
 [Správa protokolů událostí](https://msdn.microsoft.com/library/35f53238-bdd2-417b-acd8-2fd9f7397f18)  
 [Odkazy protokolu událostí](https://msdn.microsoft.com/library/4af0661c-6c96-49f4-961d-b26ed9bc3e87)  
 [Postupy: Přidání aplikace jako zdroj položky protokolu událostí](https://msdn.microsoft.com/library/948ff920-a739-4e66-a191-ee951512d42c)  
 [Postupy: odebrání zdroje událostí](https://msdn.microsoft.com/library/bc66c900-4b8a-426a-b8e2-17031a20167e)
