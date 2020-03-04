---
title: Události Trasování událostí pro Windows fondu vláken
ms.date: 03/30/2017
helpviewer_keywords:
- thread pool events [.NET Framework]
- ETW, thread pool events (CLR)
ms.assetid: f2a21e3a-3b6c-4433-97f3-47ff16855ecc
ms.openlocfilehash: 249d0607ddd280bcb4e9cf3ef34b28ff8ada3b04
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240490"
---
# <a name="thread-pool-etw-events"></a>Události Trasování událostí pro Windows fondu vláken
Tyto události shromažďují informace o vláknech Worker a I/O.  
  
 Existují dvě skupiny událostí fondu vláken:  
  
- [Události fondu pracovních vláken](#worker-thread-pool-events), které poskytují informace o tom, jak aplikace používá fond vláken, a vliv úloh na řízení souběžnosti.  
  
- [Události fondu vláken v/v](#io-thread-events), které poskytují informace o vláknech v/v, které jsou vytvářeny, vyřazeny, vyřazeny nebo ukončeny ve fondu vláken.  

## <a name="worker-thread-pool-events"></a>Události fondu pracovních vláken
 Tyto události se týkají fondu pracovních vláken modulu runtime a poskytují oznámení pro události vlákna (například při vytvoření nebo zastavení vlákna). Fond pracovních vláken používá adaptivní algoritmus pro řízení souběžnosti, kde se počet vláken počítá na základě měřené propustnosti. Události fondu pracovních vláken lze použít k pochopení, jak aplikace používá fond vláken, a vliv na to, kdy některé úlohy mohou mít kontrolu souběžnosti.  
  
### <a name="threadpoolworkerthreadstart-and-threadpoolworkerthreadstop"></a>ThreadPoolWorkerThreadStart a ThreadPoolWorkerThreadStop  
 Následující tabulka ukazuje klíčové slovo a úroveň pro tyto události. (Další informace najdete v tématu [klíčová slova a úrovně CLR ETW](clr-etw-keywords-and-levels.md).)  
  
|Klíčové slovo pro vyvolání události|Úroveň|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Informační (4)|  
  
 V následující tabulce jsou uvedeny informace o událostech.  
  
|Událost|ID události|Vyvolá se, když|  
|-|-|-|  
|`ThreadPoolWorkerThreadStart`|50|Pracovní vlákno je vytvořeno.|  
|`ThreadPoolWorkerThreadStop`|51|Pracovní vlákno je zastavené.|  
|`ThreadPoolWorkerThreadRetirementStart`|52|Recyklování pracovního vlákna.|  
|`ThreadPoolWorkerThreadRetirementStop`|53|Vyřazené pracovní vlákno se znovu aktivuje.|  
  
 V následující tabulce jsou uvedena data události.  
  
|Název pole|Typ dat|Popis|  
|----------------|---------------|-----------------|  
|ActiveWorkerThreadCount|Win: UInt32|Počet pracovních vláken, která jsou k dispozici pro zpracování práce, včetně těch, které již zpracovávají práci.|  
|RetiredWorkerThreadCount|Win: UInt32|Počet pracovních vláken, která nejsou k dispozici pro zpracování práce, ale jsou držena v rezervě v případě, že jsou později potřeba další vlákna.|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
### <a name="threadpoolworkerthreadadjustment"></a>ThreadPoolWorkerThreadAdjustment  
 Tyto události fondu vláken poskytují informace pro porozumění a ladění chování algoritmu vložení vlákna (řízení souběžnosti). Tyto informace se používají interně fondem pracovních vláken.  
  
#### <a name="threadpoolworkerthreadadjustmentsample"></a>ThreadPoolWorkerThreadAdjustmentSample  
 Klíčové slovo a úroveň jsou uvedeny v následující tabulce.  
  
|Klíčové slovo pro vyvolání události|Úroveň|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Informační (4)|  
  
 V následující tabulce jsou uvedeny informace o událostech.  
  
|Událost|ID události|Popis|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentSample`|54|Odkazuje na shromažďování informací pro jednu ukázku; To znamená, že v čase je měření propustnosti s určitou úrovní souběžnosti.|  
  
 V následující tabulce jsou uvedena data události.  
  
|Název pole|Typ dat|Popis|  
|----------------|---------------|-----------------|  
|Propustnost|Win: Double|Počet dokončení na jednotku času.|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
#### <a name="threadpoolworkerthreadadjustmentadjustment"></a>ThreadPoolWorkerThreadAdjustmentAdjustment  
 Klíčové slovo a úroveň jsou uvedeny v následující tabulce.  
  
|Klíčové slovo pro vyvolání události|Úroveň|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Informační (4)|  
  
 V následující tabulce jsou uvedeny informace o událostech.  
  
|Událost|ID události|Popis|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentAdjustment`|55|Zaznamenává změnu v ovládacím prvku, když algoritmus pro vložení vlákna (stoupání) určuje, že změna v úrovni souběžnosti je na místě.|  
  
 V následující tabulce jsou uvedena data události.  
  
|Název pole|Typ dat|Popis|  
|----------------|---------------|-----------------|  
|AverageThroughput|Win: Double|Průměrná propustnost vzorku měření.|  
|NewWorkerThreadCount|Win: UInt32|Nový počet aktivních pracovních vláken.|  
|Důvod|Win: UInt32|Důvod pro úpravu<br /><br /> 0x00-zahřívání.<br /><br /> 0x01 – inicializuje se.<br /><br /> 0x02 – náhodný přesun.<br /><br /> 0x03-stoupání Move.<br /><br /> 0x04 – bod změny.<br /><br /> 0x05 – stabilizace.<br /><br /> 0x06-vyčerpání.<br /><br /> 0x07 – vypršel časový limit vlákna.|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
#### <a name="threadpoolworkerthreadadjustmentstats"></a>ThreadPoolWorkerThreadAdjustmentStats  
 Klíčové slovo a úroveň jsou uvedeny v následující tabulce.  
  
|Klíčové slovo pro vyvolání události|Úroveň|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Informační (4)|  
  
 V následující tabulce jsou uvedeny informace o událostech.  
  
|Událost|ID události|Popis|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentStats`|56|Shromažďuje data ve fondu vláken.|  
  
 V následující tabulce jsou uvedena data události.  
  
|Název pole|Typ dat|Popis|  
|----------------|---------------|-----------------|  
|Doba trvání|Win: Double|Množství času v sekundách, během kterého byly tyto statistiky shromažďovány.|  
|Propustnost|Win: Double|Průměrný počet dokončení za sekundu v průběhu tohoto intervalu.|  
|ThreadWave|Win: Double|Vyhrazeno pro interní použití.|  
|ThroughputWave|Win: Double|Vyhrazeno pro interní použití.|  
|ThroughputErrorEstimate|Win: Double|Vyhrazeno pro interní použití.|  
|AverageThroughputErrorEstimate|Win: Double|Vyhrazeno pro interní použití.|  
|ThroughputRatio|Win: Double|Relativní zvýšení propustnosti způsobené kolísáním počtu aktivních pracovních vláken v průběhu tohoto intervalu.|  
|Confidence|Win: Double|Míra platnosti pole ThroughputRatio.|  
|NewcontrolSetting|Win: Double|Počet aktivních pracovních vláken, která budou sloužit jako základ pro budoucí variace počtu aktivních vláken.|  
|NewThreadWaveMagnitude|Win: UInt16|Velikost budoucích variant počtu aktivních vláken.|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  

## <a name="io-thread-events"></a>Události v/v vlákna  
 Tyto události fondu vláken se vyskytují pro vlákna ve fondu vláken v/v (porty dokončení), což je asynchronní.  
  
### <a name="iothreadcreate_v1"></a>IOThreadCreate_V1  
 Klíčové slovo a úroveň jsou uvedeny v následující tabulce.  
  
|Klíčové slovo pro vyvolání události|Úroveň|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Informační (4)|  
  
 V následující tabulce jsou uvedeny informace o událostech.  
  
|Událost|ID události|Vyvolá se, když|  
|-|-|-|  
|`IOThreadCreate_V1`|44|Ve fondu vláken se vytvoří vstupně-výstupní vlákno.|  
  
 V následující tabulce jsou uvedena data události.  
  
|Název pole|Typ dat|Popis|  
|----------------|---------------|-----------------|  
|Počet|win:UInt64|Počet vstupně-výstupních vláken, včetně nově vytvořeného vlákna.|  
|NumRetired|win:UInt64|Počet vyřazených pracovních vláken.|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
### <a name="iothreadretire_v1"></a>IOThreadRetire_V1  
 Klíčové slovo a úroveň jsou uvedeny v následující tabulce.  
  
|Klíčové slovo pro vyvolání události|Úroveň|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Informační (4)|  
  
 V následující tabulce jsou uvedeny informace o událostech.  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`IOThreadRetire_V1`|46|Vstupně-výstupní vlákno se staly kandidátem na vyřazení.|  
  
 V následující tabulce jsou uvedena data události.  
  
|Název pole|Typ dat|Popis|  
|----------------|---------------|-----------------|  
|Počet|win:UInt64|Počet zbývajících vstupně-výstupních vláken ve fondu vláken.|  
|NumRetired|win:UInt64|Počet vyřazených vstupně-výstupních vláken.|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
### <a name="iothreadunretire_v1"></a>IOThreadUnretire_V1  
 Klíčové slovo a úroveň jsou uvedeny v následující tabulce.  
  
|Klíčové slovo pro vyvolání události|Úroveň|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Informační (4)|  
  
 V následující tabulce jsou uvedeny informace o událostech.  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`IOThreadUnretire_V1`|47|Vstupně-výstupní vlákno není vyřazeno z důvodu vstupu/výstupu, který dorazí do čekací doby poté, co se vlákno dostane kandidátem na vyřazení.|  
  
 V následující tabulce jsou uvedena data události.  
  
|Název pole|Typ dat|Popis|  
|----------------|---------------|-----------------|  
|Počet|win:UInt64|Počet vstupně-výstupních vláken ve fondu vláken, včetně tohoto typu.|  
|NumRetired|win:UInt64|Počet vyřazených vstupně-výstupních vláken.|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
### <a name="iothreadterminate"></a>IOThreadTerminate  
 Klíčové slovo a úroveň jsou uvedeny v následující tabulce.  
  
|Klíčové slovo pro vyvolání události|Úroveň|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Informační (4)|  
  
 V následující tabulce jsou uvedeny informace o událostech.  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`IOThreadTerminate`|45|Vstupně-výstupní vlákno je ukončeno ve fondu vláken.|  
  
 V následující tabulce jsou uvedena data události.  
  
|Název pole|Typ dat|Popis|  
|----------------|---------------|-----------------|  
|Počet|win:UInt64|Počet zbývajících vstupně-výstupních vláken ve fondu vláken.|  
|NumRetired|win:UInt64|Počet vyřazených vstupně-výstupních vláken.|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
## <a name="see-also"></a>Viz také

- [Události Trasování událostí pro Windows v CLR](clr-etw-events.md)
