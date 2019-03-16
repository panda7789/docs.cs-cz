---
title: Zadaný v EventLogSource název zdroje je zaregistrovaný do protokolu, než je zadaná v EventLogName
ms.date: 07/20/2015
ms.assetid: 7317e100-098b-408d-86e5-7c74cf8558c7
ms.openlocfilehash: 22129ab0c4f7fe0a78300907a949d9368028c9fa
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2019
ms.locfileid: "58022303"
---
# <a name="source-name-specified-in-eventlogsource-is-registered-to-a-log-other-than-that-specified-in-eventlogname"></a>Zadaný v EventLogSource název zdroje je zaregistrovaný do protokolu, než je zadaná v EventLogName
`EventLog` Se pokouší odkazovat na zdroj, který je registrovaný pro jiný protokol. Pokud vytváříte položky do protokolu událostí, je nutné zadat <xref:System.Diagnostics.EventLog.Source%2A> vlastnost. <xref:System.Diagnostics.EventLog.Source%2A> Vlastnost zaregistruje vaše komponenta se do protokolu událostí jako platný zdroj položky. Jeden zdroj může být spojen s (a proto zapisovat položky do) jenom jeden protokol událostí současně.  
  
 Ve výchozím nastavení, pokud se pokusíte pro zápis záznamu, aniž nejprve registraci komponenty jako platný zdroj, systém automaticky registruje zdroj protokolu událostí, použití hodnoty <xref:System.Diagnostics.EventLog.Source%2A> vlastnost jako zdrojový řetězec.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Zajistěte, aby že zdroj je registrován do správné protokolu. Chcete-li to provést, použijte <xref:System.Diagnostics.EventLog.CreateEventSource%2A> metody nebo jeden z jejich přetížení zadat řetězec, který jednoznačně identifikuje vaše komponenta do protokolu událostí.  
  
## <a name="see-also"></a>Viz také:

- [Správa protokolů událostí](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/4f69axw4(v=vs.90))
- [Odkazy protokolu událostí](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/k43k9z2a(v=vs.90))
- [Postupy: Přidejte svoji aplikaci jako zdroj položky protokolu událostí](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/xz73e171(v=vs.90))
- [Postupy: Odebrat zdroje událostí](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/k57466fc(v=vs.90))
