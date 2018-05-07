---
title: Události Trasování událostí pro Windows fondu vláken
ms.date: 03/30/2017
helpviewer_keywords:
- thread pool events [.NET Framework]
- ETW, thread pool events (CLR)
ms.assetid: f2a21e3a-3b6c-4433-97f3-47ff16855ecc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 41a37fa34b9d75eb8cfc1bdcb55b237faf137cad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="thread-pool-etw-events"></a>Události Trasování událostí pro Windows fondu vláken
<a name="top"></a> Tyto události shromažďovat informace o vstupně-výstupních operací vláken a pracovního procesu.  
  
 Existují dvě skupiny události fondu vláken:  
  
-   [Události fondu vláken pracovní](#worker), které obsahují informace o tom, jak aplikace používá fondu vláken a účinek zatížení na Kontrola souběžnosti.  
  
-   [Události fondu vláken vstupně-výstupních operací](#io), které obsahují informace o vstupně-výstupních operací vláken, která jsou vytvořena, vyřazen z provozu, unretired, nebo byl ukončen ve fondu vláken.  
  
<a name="worker"></a>   
## <a name="worker-thread-pool-events"></a>Události fondu vláken pracovního procesu  
 Tyto události se týkají fondu vláken modulu runtime pracovního procesu a poskytnout oznámení pro přístup z více vláken události (například při vytvoření nebo zastavena vlákno). Fond pracovních vláken používá adaptivní algoritmus pro concurrency řízení, kde se počítá počet vláken, na základě měřená propustnost. Události fondu vláken pracovní slouží k pochopení, jak aplikace používá fond vláken a o tom, že některé úlohy mohou mít na Kontrola souběžnosti.  
  
### <a name="threadpoolworkerthreadstart-and-threadpoolworkerthreadstop"></a>ThreadPoolWorkerThreadStart a ThreadPoolWorkerThreadStop  
 V následující tabulce jsou uvedeny – klíčové slovo a úroveň pro tyto události. (Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|– Klíčové slovo za vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá, když|  
|-|-|-|  
|`ThreadPoolWorkerThreadStart`|50|Je-li vytvořit pracovní vlákno.|  
|`ThreadPoolWorkerThreadStop`|51|Pracovní podproces je zastavena.|  
|`ThreadPoolWorkerThreadRetirementStart`|52|Pracovní podproces IT vyřadí.|  
|`ThreadPoolWorkerThreadRetirementStop`|53|Vyřazeno pracovní vlákno zase aktivní.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|ActiveWorkerThreadCount|Win: UInt32|Počet pracovních vláken, které jsou k dispozici pro zpracování práce, včetně těch, které jsou již zpracování pracovní.|  
|RetiredWorkerThreadCount|Win: UInt32|Počet pracovních vláken, které nejsou k dispozici pro zpracování pracovní, ale které jsou právě uložené v rezervy v případě, že je budete později potřebovat více vláken.|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
### <a name="threadpoolworkerthreadadjustment"></a>ThreadPoolWorkerThreadAdjustment  
 Tyto události fondu vláken poskytují informace pro pochopení a ladění chování algoritmus vlákno vkládání (concurrency řízení). Informace se používá interně ve fondu pracovních vláken.  
  
#### <a name="threadpoolworkerthreadadjustmentsample"></a>ThreadPoolWorkerThreadAdjustmentSample  
 V následující tabulce jsou uvedeny – klíčové slovo a úroveň.  
  
|– Klíčové slovo za vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Popis|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentSample`|54|Odkazuje na kolekci informace pro jeden ukázku; měření propustnosti s určitým souběžných úrovně tedy prakticky okamžitě času.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|Propustnost|Win: Double|Počet dokončených na jednotku intervalu.|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
#### <a name="threadpoolworkerthreadadjustmentadjustment"></a>ThreadPoolWorkerThreadAdjustmentAdjustment  
 V následující tabulce jsou uvedeny – klíčové slovo a úroveň.  
  
|– Klíčové slovo za vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Popis|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentAdjustment`|55|Zaznamenává změnu v ovládacím prvku, pokud algoritmus vlákno vkládání (vrchol stoupající) zjistí, že ke změně v concurrency úroveň na místě.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|AverageThroughput|Win: Double|Průměrná propustnost ukázkové měření.|  
|NewWorkerThreadCount|Win: UInt32|Nový počet active pracovních vláken.|  
|Důvod|Win: UInt32|Důvod pro úpravu.<br /><br /> 0x00 - zahřívání.<br /><br /> 0x01 - inicializace.<br /><br /> 0x02 – náhodné move.<br /><br /> 0x03 - týkajícími se horolezectví move.<br /><br /> 0x04 - změnit bod.<br /><br /> 0x05 - stabilizaci.<br /><br /> 0x06 - nedostatku prostředků.<br /><br /> 0x07 - vlákno vypršel časový limit.|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
#### <a name="threadpoolworkerthreadadjustmentstats"></a>ThreadPoolWorkerThreadAdjustmentStats  
 V následující tabulce jsou uvedeny – klíčové slovo a úroveň.  
  
|– Klíčové slovo za vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Popis|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentStats`|56|Shromáždí data ve fondu vláken.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|Doba trvání|Win: Double|Množství času v sekundách, během které byly shromážděny ve statistikách.|  
|Propustnost|Win: Double|Průměrný počet dokončených za sekundu během tohoto intervalu.|  
|ThreadWave|Win: Double|Vyhrazeno pro interní použití.|  
|ThroughputWave|Win: Double|Vyhrazeno pro interní použití.|  
|ThroughputErrorEstimate|Win: Double|Vyhrazeno pro interní použití.|  
|AverageThroughputErrorEstimate|Win: Double|Vyhrazeno pro interní použití.|  
|ThroughputRatio|Win: Double|Relativní zlepšování propustnost způsobené rozdíly v počet vláken active pracovní během tohoto intervalu.|  
|Spolehlivosti|Win: Double|Míra platnosti ThroughputRatio pole.|  
|NewcontrolSetting|Win: Double|Počet aktivních pracovních vláken, která bude sloužit jako základ pro budoucí rozdíly v počet aktivních vláken.|  
|NewThreadWaveMagnitude|Win: UInt16|Odhad budoucích rozdíly v počet aktivních vláken.|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
 [Zpět na začátek](#top)  
  
<a name="io"></a>   
## <a name="io-thread-events"></a>Události vstupně-výstupních operací přístup z více vláken  
 Tyto události fondu vláken dojít pro vláken ve fondu vláken vstupně-výstupní operace (dokončení porty), která je asynchronní.  
  
### <a name="iothreadcreatev1"></a>IOThreadCreate_V1  
 V následující tabulce jsou uvedeny – klíčové slovo a úroveň.  
  
|– Klíčové slovo za vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá, když|  
|-|-|-|  
|`IOThreadCreate_V1`|44|Zřetězení vstupně-výstupních operací je vytvořená ve fondu vláken.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|Počet|Win: UInt64|Počet vláken vstupně-výstupní operace, včetně nově vytvořený vlákno.|  
|NumRetired|Win: UInt64|Počet vyřazeno pracovních vláken.|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
### <a name="iothreadretirev1"></a>IOThreadRetire_V1  
 V následující tabulce jsou uvedeny – klíčové slovo a úroveň.  
  
|– Klíčové slovo za vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá, když|  
|-----------|--------------|-----------------|  
|`IOThreadRetire_V1`|46|Zřetězení vstupně-výstupních operací se stane kandidátem vyřazení.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|Počet|Win: UInt64|Počet vstupně-výstupních operací vláken zbývající ve fondu vláken.|  
|NumRetired|Win: UInt64|Počet vláken vyřazeno vstupně-výstupní operace.|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
### <a name="iothreadunretirev1"></a>IOThreadUnretire_V1  
 V následující tabulce jsou uvedeny – klíčové slovo a úroveň.  
  
|– Klíčové slovo za vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá, když|  
|-----------|--------------|-----------------|  
|`IOThreadUnretire_V1`|47|Zřetězení vstupně-výstupních operací je unretired kvůli vstupně-výstupní operace doručena během čekací doby, po vyřazení kandidátem se změní na vlákno.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|Počet|Win: UInt64|Počet vstupně-výstupních operací vláken ve fondu vláken, včetně tato.|  
|NumRetired|Win: UInt64|Počet vláken vyřazeno vstupně-výstupní operace.|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
### <a name="iothreadterminate"></a>IOThreadTerminate  
 V následující tabulce jsou uvedeny – klíčové slovo a úroveň.  
  
|– Klíčové slovo za vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`ThreadingKeyword` (0x10000)|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá, když|  
|-----------|--------------|-----------------|  
|`IOThreadTerminate`|45|Zřetězení vstupně-výstupních operací je vytvořená ve fondu vláken.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|Počet|Win: UInt64|Počet vstupně-výstupních operací vláken zbývající ve fondu vláken.|  
|NumRetired|Win: UInt64|Počet vláken vyřazeno vstupně-výstupní operace.|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
## <a name="see-also"></a>Viz také  
 [Události Trasování událostí pro Windows v CLR](../../../docs/framework/performance/clr-etw-events.md)
