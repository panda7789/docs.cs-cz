---
title: Události Trasování událostí pro Windows fondu vláken
ms.date: 03/30/2017
helpviewer_keywords:
- thread pool events [.NET Framework]
- ETW, thread pool events (CLR)
ms.assetid: f2a21e3a-3b6c-4433-97f3-47ff16855ecc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: caacee591c4df8389cea241916618f50da56b22b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949159"
---
# <a name="thread-pool-etw-events"></a>Události Trasování událostí pro Windows fondu vláken
<a name="top"></a> Tyto události shromažďovat informace o pracovních procesů a vláken vstupně-výstupních operací.  
  
 Existují dvě skupiny události fondu vláken:  
  
- [Události fondu vláken pracovního procesu](#worker), které poskytují informace o tom, jak aplikace používá fondu vláken a dopad úloh na řízení souběžnosti.  
  
- [Události fondu vláken vstupně-výstupních operací](#io), které poskytují informace o vstupně-výstupních operací podprocesů, které jsou vytvořeny, vyřazení, unretired nebo ukončen ve fondu vláken.  
  
<a name="worker"></a>   
## <a name="worker-thread-pool-events"></a>Události fondu vláken pracovního procesu  
 Tyto události se vztahují k fondu vláken pro pracovníka modul runtime a poskytují oznámení pro vlákno události (například když vlákno je vytvořen nebo zastavená). Vlákno fond pracovních procesů používá adaptivní algoritmus pro kontrolu souběžnosti, ve kterém se počítá počet vláken podle naměřená propustnost. Události fondu vláken pracovního procesu slouží k pochopení, jak aplikace používá fond vláken a některé úlohy mohou mít na řízení souběžnosti vliv.  
  
### <a name="threadpoolworkerthreadstart-and-threadpoolworkerthreadstop"></a>ThreadPoolWorkerThreadStart a ThreadPoolWorkerThreadStop  
 V následující tabulce jsou uvedeny klíčové slovo a úroveň pro tyto události. (Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Klíčové slovo pro vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá se, když|  
|-|-|-|  
|`ThreadPoolWorkerThreadStart`|50|Vytvoření pracovního vlákna.|  
|`ThreadPoolWorkerThreadStop`|51|Pracovní vlákno je zastavené.|  
|`ThreadPoolWorkerThreadRetirementStart`|52|Pracovní podproces co vyřadí.|  
|`ThreadPoolWorkerThreadRetirementStop`|53|Vyřazené pracovní podproces opět aktivní.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|ActiveWorkerThreadCount|win:UInt32|Počet pracovních vláken, které jsou k dispozici pro zpracování práci, včetně těch, které jsou již práce potřebné ke zpracování.|  
|RetiredWorkerThreadCount|win:UInt32|Počet pracovních vláken, které nejsou k dispozici pro zpracování prací, ale, která se ukládají do rezervy v případě, že je budete později potřebovat více vláken.|  
|ClrInstanceID|Windows: UInt16|Jedinečné ID instance CLR nebo CoreCLR.|  
  
### <a name="threadpoolworkerthreadadjustment"></a>ThreadPoolWorkerThreadAdjustment  
 Tyto události fondu vláken poskytují informace pro pochopení a ladění chování algoritmu vlákno vkládání (řízení souběžnosti). Informace se používá interně ve fondu pracovních vláken.  
  
#### <a name="threadpoolworkerthreadadjustmentsample"></a>ThreadPoolWorkerThreadAdjustmentSample  
 V následující tabulce jsou uvedeny klíčové slovo a úroveň.  
  
|Klíčové slovo pro vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Popis|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentSample`|54|Odkazuje na shromažďování informací pro jeden vzorek; To znamená měření propustnosti se určité souběžností úrovni, v okamžik v čase.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|Propustnost|win:Double|Počet dokončování na jednotku času.|  
|ClrInstanceID|Windows: UInt16|Jedinečné ID instance CLR nebo CoreCLR.|  
  
#### <a name="threadpoolworkerthreadadjustmentadjustment"></a>ThreadPoolWorkerThreadAdjustmentAdjustment  
 V následující tabulce jsou uvedeny klíčové slovo a úroveň.  
  
|Klíčové slovo pro vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Popis|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentAdjustment`|55|Zaznamenává změny v ovládacím prvku, pokud algoritmus vlákno vkládání (hill průběžné) určuje, že změna úroveň souběžnosti je na místě.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|AverageThroughput|win:Double|Průměrná propustnost ukázkové měření.|  
|NewWorkerThreadCount|win:UInt32|Nový počet aktivních pracovních vláken.|  
|Důvod|win:UInt32|Důvod pro úpravu.<br /><br /> 0x00 – zahřívání.<br /><br /> 0x01 - inicializace.<br /><br /> 0x02 – náhodné přesunout.<br /><br /> 0x03 - vzájemnému najetí přesunout.<br /><br /> 0x04 - Změna bodu.<br /><br /> 0x05 - stabilizace.<br /><br /> 0x06 - vyčerpání.<br /><br /> 0x07 - vlákno vypršel časový limit.|  
|ClrInstanceID|Windows: UInt16|Jedinečné ID instance CLR nebo CoreCLR.|  
  
#### <a name="threadpoolworkerthreadadjustmentstats"></a>ThreadPoolWorkerThreadAdjustmentStats  
 V následující tabulce jsou uvedeny klíčové slovo a úroveň.  
  
|Klíčové slovo pro vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Popis|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentStats`|56|Shromažďuje data ve fondu vláken.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|Doba trvání|win:Double|Množství času v sekundách, během kterých byly tyto statistické údaje shromážděny.|  
|Propustnost|win:Double|Průměrný počet dokončování za sekundu během tohoto intervalu.|  
|ThreadWave|win:Double|Vyhrazeno pro interní použití.|  
|ThroughputWave|win:Double|Vyhrazeno pro interní použití.|  
|ThroughputErrorEstimate|win:Double|Vyhrazeno pro interní použití.|  
|AverageThroughputErrorEstimate|win:Double|Vyhrazeno pro interní použití.|  
|ThroughputRatio|win:Double|Relativní zvýšení propustnosti způsobené kolísání počet aktivních pracovních vláken během tohoto intervalu.|  
|Spolehlivost|win:Double|Rozměr pole ThroughputRatio platnost.|  
|NewcontrolSetting|win:Double|Počet aktivních pracovních vláken, které bude sloužit jako základ pro budoucí kolísání počet aktivních vláken.|  
|NewThreadWaveMagnitude|Windows: UInt16|Velikost budoucí kolísání počet aktivních vláken.|  
|ClrInstanceID|Windows: UInt16|Jedinečné ID instance CLR nebo CoreCLR.|  
  
 [Zpět na začátek](#top)  
  
<a name="io"></a>   
## <a name="io-thread-events"></a>Události vláken vstupně-výstupních operací  
 Tyto události fondu vláken vztahuje vláken ve fondu vláken vstupně-výstupních operací (dokončení portů), což je asynchronní.  
  
### <a name="iothreadcreatev1"></a>IOThreadCreate_V1  
 V následující tabulce jsou uvedeny klíčové slovo a úroveň.  
  
|Klíčové slovo pro vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá se, když|  
|-|-|-|  
|`IOThreadCreate_V1`|44|Zřetězení vstupně-výstupní operace se vytvoří ve fondu vláken.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|Count|win:UInt64|Počet vláken vstupně-výstupních operací, včetně nově vytvořeného vlákna.|  
|NumRetired|win:UInt64|Počet vyřazených pracovních vláken.|  
|ClrInstanceID|Windows: UInt16|Jedinečné ID instance CLR nebo CoreCLR.|  
  
### <a name="iothreadretirev1"></a>IOThreadRetire_V1  
 V následující tabulce jsou uvedeny klíčové slovo a úroveň.  
  
|Klíčové slovo pro vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`IOThreadRetire_V1`|46|Zřetězení vstupně-výstupní operace se stane kandidát vyřazení z provozu.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|Count|win:UInt64|Počet vláken vstupně-výstupních operací zbývající ve fondu vláken.|  
|NumRetired|win:UInt64|Počet vyřazených vláken vstupně-výstupních operací.|  
|ClrInstanceID|Windows: UInt16|Jedinečné ID instance CLR nebo CoreCLR.|  
  
### <a name="iothreadunretirev1"></a>IOThreadUnretire_V1  
 V následující tabulce jsou uvedeny klíčové slovo a úroveň.  
  
|Klíčové slovo pro vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`IOThreadUnretire_V1`|47|Zřetězení vstupně-výstupních operací je unretired kvůli vstupně-výstupní operace, která dorazí do čekací doba, po vlákno stane kandidát vyřazení z provozu.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|Count|win:UInt64|Počet vstupně-výstupní operace vláken ve fondu vláken, včetně ten.|  
|NumRetired|win:UInt64|Počet vyřazených vláken vstupně-výstupních operací.|  
|ClrInstanceID|Windows: UInt16|Jedinečné ID instance CLR nebo CoreCLR.|  
  
### <a name="iothreadterminate"></a>IOThreadTerminate  
 V následující tabulce jsou uvedeny klíčové slovo a úroveň.  
  
|Klíčové slovo pro vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`IOThreadTerminate`|45|Zřetězení vstupně-výstupní operace se vytvoří ve fondu vláken.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|Count|win:UInt64|Počet vláken vstupně-výstupních operací zbývající ve fondu vláken.|  
|NumRetired|win:UInt64|Počet vyřazených vláken vstupně-výstupních operací.|  
|ClrInstanceID|Windows: UInt16|Jedinečné ID instance CLR nebo CoreCLR.|  
  
## <a name="see-also"></a>Viz také:

- [Události Trasování událostí pro Windows v CLR](../../../docs/framework/performance/clr-etw-events.md)
