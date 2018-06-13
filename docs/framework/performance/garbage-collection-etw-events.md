---
title: Události Trasování událostí pro Windows kolekci paměti
ms.date: 03/30/2017
helpviewer_keywords:
- GC events
- garbage collection events [.NET Framework]
- ETW, garbage collection events (CLR)
ms.assetid: f14b6fd7-0966-4d87-bc89-54ef3a44a94a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 13f7e935ab999ccc3cd3ea1e308e8d686bed4171
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33396932"
---
# <a name="garbage-collection-etw-events"></a>Události Trasování událostí pro Windows kolekci paměti
<a name="top"></a> Tyto události shromažďovat informace týkající se uvolňování paměti. Mohou pomoci v diagnostice a ladění, včetně určení, jak často uvolňování byla provedena, kolik paměti byl uvolněn při uvolňování paměti a tak dále.  
  
 Tato kategorie se skládá z následujících událostí:  
  
-   [GCStart_V1 událostí](#gcstart_v1_event)  
  
-   [GCEnd_V1 událostí](#gcend_v1_event)  
  
-   [GCHeapStats_V1 událostí](#gcheapstats_v1_event)  
  
-   [GCCreateSegment_V1 událostí](#gccreatesegment_v1_event)  
  
-   [GCFreeSegment_V1 událostí](#gcfreesegment_v1_event)  
  
-   [GCRestartEEBegin_V1 událostí](#gcrestarteebegin_v1_event)  
  
-   [GCRestartEEEnd_V1 událostí](#gcrestarteeend_v1_event)  
  
-   [GCSuspendEE_V1 událostí](#gcsuspendee_v1_event)  
  
-   [GCSuspendEEEnd_V1 událostí](#gcsuspendeeend_v1_event)  
  
-   [GCAllocationTick_V2 událostí](#gcallocationtick_v2_event)  
  
-   [GCFinalizersBegin_V1 událostí](#gcfinalizersbegin_v1_event)  
  
-   [GCFinalizersEnd_V1 událostí](#gcfinalizersend_v1_event)  
  
-   [GCCreateConcurrentThread_V1 událostí](#gccreateconcurrentthread_v1_event)  
  
-   [GCTerminateConcurrentThread_V1 událostí](#gcterminateconcurrentthread_v1_event)  
  
<a name="gcstart_v1_event"></a>   
## <a name="gcstartv1-event"></a>GCStart_V1 událostí  
 V následující tabulce jsou uvedeny – klíčové slovo a úroveň. (Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|– Klíčové slovo za vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá, když|  
|-----------|--------------|-----------------|  
|`GCStart_V1`|1|Kolekce paměti bylo zahájeno.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|Počet|Win: UInt32|*n*tý uvolňování paměti.|  
|Hloubka|Win: UInt32|Generování, jež jsou shromažďována.|  
|Důvod|Win: UInt32|Proč byla aktivována uvolnění paměti:<br /><br /> 0x0 - přidělení haldy malé objektu.<br /><br /> 0x1 - vyvolané.<br /><br /> 0x2 - nedostatek paměti.<br /><br /> 0x3 - prázdný.<br /><br /> 0x4 - přidělení haldy velkého objektu.<br /><br /> 0x5 – volné místo (pro malé objektu haldy).<br /><br /> 0x6 – volné místo (pro velkého objektu haldy).<br /><br /> 0x7 - vyvolané ale nejsou vynucené jako blokování.|  
|Typ|Win: UInt32|došlo k blokování uvolňování 0x0 - mimo kolekce paměti na pozadí.<br /><br /> 0x1 – kolekce paměti na pozadí.<br /><br /> 0x2 – uvolňování paměti blokování došlo k chybě během kolekce paměti na pozadí.|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
 [Zpět na začátek](#top)  
  
<a name="gcend_v1_event"></a>   
## <a name="gcendv1-event"></a>GCEnd_V1 událostí  
 V následující tabulce jsou uvedeny – klíčové slovo a úroveň.  
  
|– Klíčové slovo za vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá, když|  
|-----------|--------------|-----------------|  
|`GCEnd_V1`|2|Kolekce paměti byl ukončen.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|Počet|Win: UInt32|*n*tý uvolňování paměti.|  
|Hloubka|Win: UInt32|Generování, která nebyla shromážděna.|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
 [Zpět na začátek](#top)  
  
<a name="gcheapstats_v1_event"></a>   
## <a name="gcheapstatsv1-event"></a>GCHeapStats_V1 událostí  
 V následující tabulce jsou uvedeny – klíčové slovo a úroveň.  
  
|– Klíčové slovo za vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Popis|  
|-----------|--------------|-----------------|  
|`GCHeapStats_V1`|4|Zobrazuje statistiku haldy na konci každé uvolňování paměti.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|GenerationSize0|Win: UInt64|Velikost v bajtech, generace 0 paměti.|  
|TotalPromotedSize0|Win: UInt64|Počet bajtů, které jsou povýší z generace 0 na 1. generace.|  
|GenerationSize1|Win: UInt64|Velikost v bajtech paměti generace 1.|  
|TotalPromotedSize1|Win: UInt64|Počet bajtů, které jsou povýší z generace 1 na 2. generace.|  
|GenerationSize2|Win: UInt64|Velikost v bajtech, paměti, 2. generace.|  
|TotalPromotedSize2|Win: UInt64|Počet bajtů, které přežil v generace 2 po poslední kolekce.|  
|GenerationSize3|Win: UInt64|Velikost v bajtech haldě velkého objektu.|  
|TotalPromotedSize3|Win: UInt64|Počet bajtů, které přežil v haldě velkého objektu po poslední kolekce.|  
|FinalizationPromotedSize|Win: UInt64|Celková velikost v bajtech objektů, které jsou připravené pro dokončení.|  
|FinalizationPromotedCount|Win: UInt64|Počet objektů, které jsou připravené pro dokončení.|  
|PinnedObjectCount|Win: UInt32|Počet připojených objektů (nepřesunutelnou).|  
|SinkBlockCount|Win: UInt32|Počet bloků synchronizace používá.|  
|GCHandleCount|Win: UInt32|Počet uvolňování zpracovává používán.|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
 [Zpět na začátek](#top)  
  
<a name="gccreatesegment_v1_event"></a>   
## <a name="gccreatesegmentv1-event"></a>GCCreateSegment_V1 událostí  
 V následující tabulce jsou uvedeny – klíčové slovo a úroveň.  
  
|– Klíčové slovo za vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá, když|  
|-----------|--------------|-----------------|  
|`GCCreateSegment_V1`|5|Byl vytvořen nový segment kolekce paměti. Kromě toho pokud je povoleno sledování na procesu, který je již spuštěn, tato událost je aktivována pro každý existující segment.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|Adresa|Win: UInt64|Adresa segmentu.|  
|Velikost|Win: UInt64|Velikost segmentu.|  
|Typ|Win: UInt32|0x0 - malé objekty.<br /><br /> 0x1 - velké objekty.<br /><br /> 0x2 - haldy jen pro čtení.|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
 Všimněte si, že velikost segmentů přidělené modulem garbage collector závisí na implementaci a mohou podléhat změnám kdykoli, včetně v pravidelné aktualizace. Vaše aplikace by nikdy Zkontrolujte předpoklady o nebo závisí na velikosti určitý segment, ani pokusit nakonfigurovat množství paměti k dispozici pro přidělení segmentu.  
  
 [Zpět na začátek](#top)  
  
<a name="gcfreesegment_v1_event"></a>   
## <a name="gcfreesegmentv1-event"></a>GCFreeSegment_V1 událostí  
 V následující tabulce jsou uvedeny – klíčové slovo a úroveň.  
  
|– Klíčové slovo za vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá, když|  
|-----------|--------------|-----------------|  
|`GCFreeSegment_V1`|6|Byla vydána segment kolekce paměti.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|Adresa|Win: UInt64|Adresa segmentu.|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
 [Zpět na začátek](#top)  
  
<a name="gcrestarteebegin_v1_event"></a>   
## <a name="gcrestarteebeginv1-event"></a>GCRestartEEBegin_V1 událostí  
 V následující tabulce jsou uvedeny – klíčové slovo a úroveň.  
  
|– Klíčové slovo za vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá, když|  
|-----------|--------------|-----------------|  
|`GCRestartEEBegin_V1`|7|Obnovení z běžných pozastavení runtime jazyka byl zahájen.|  
  
 Žádná data.  
  
 [Zpět na začátek](#top)  
  
<a name="gcrestarteeend_v1_event"></a>   
## <a name="gcrestarteeendv1-event"></a>GCRestartEEEnd_V1 událostí  
 V následující tabulce jsou uvedeny – klíčové slovo a úroveň.  
  
|– Klíčové slovo za vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|Id události|Vyvolá, když|  
|-----------|--------------|-----------------|  
|`GCRestartEEEnd_V1`|3|Obnovení z běžných pozastavení runtime jazyka byl ukončen.|  
  
 Žádná data.  
  
 [Zpět na začátek](#top)  
  
<a name="gcsuspendee_v1_event"></a>   
## <a name="gcsuspendeev1-event"></a>GCSuspendEE_V1 událostí  
 V následující tabulce jsou uvedeny – klíčové slovo a úroveň.  
  
|– Klíčové slovo za vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá, když|  
|-----------|--------------|-----------------|  
|`GCSuspendEE_V1`|9|Začátek pozastavení provádění modul pro uvolňování paměti.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|Důvod|Win: UInt16|0x0 - Další.<br /><br /> 0x1 – uvolňování paměti.<br /><br /> 0x2 - ukončení domény aplikace.<br /><br /> 0x3 - pitching kódu.<br /><br /> 0x4 - vypnutí.<br /><br /> 0x5 - ladicí program.<br /><br /> 0x6 - přípravy pro uvolňování paměti.|  
|Počet|Win: UInt32|Počet uvolňování paměti v době. Obvykle zobrazí se následných událostí GC spuštění po této a jeho počet by tento počet + 1 jsme zvýšit GC index během uvolňování paměti.|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
 [Zpět na začátek](#top)  
  
<a name="gcsuspendeeend_v1_event"></a>   
## <a name="gcsuspendeeendv1-event"></a>GCSuspendEEEnd_V1 událostí  
 V následující tabulce jsou uvedeny – klíčové slovo a úroveň:  
  
|– Klíčové slovo za vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události:  
  
|Událost|ID události|Vyvolá, když|  
|-----------|--------------|-----------------|  
|`GCSuspendEEEnd_V1`|8|Konec pozastavení provádění modul pro uvolňování paměti.|  
  
 Žádná data.  
  
 [Zpět na začátek](#top)  
  
<a name="gcallocationtick_v2_event"></a>   
## <a name="gcallocationtickv2-event"></a>GCAllocationTick_V2 událostí  
 V následující tabulce jsou uvedeny – klíčové slovo a úroveň.  
  
|– Klíčové slovo za vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá, když|  
|-----------|--------------|-----------------|  
|`GCAllocationTick_V2`|10|Pokaždé, když je přidělen přibližně 100 KB.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|AllocationAmount|Win: UInt32|Přidělení velikost v bajtech. Tato hodnota je přesný pro přidělení, které jsou menší než délka ULONG (4,294,967,295 bajtů). Pokud přidělení je vyšší, toto pole obsahuje zkrácená hodnota. Použití `AllocationAmount64` pro velké přidělení.|  
|AllocationKind|Win: UInt32|0x0 - malé objekt přidělení (přidělení je v malých objektu haldy).<br /><br /> 0x1 - přidělení velkého objektu (přidělení je v haldě rozsáhlý objekt).|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
|AllocationAmount64|Win: UInt64|Přidělení velikost v bajtech. Tato hodnota je přesný pro velké přidělení.|  
|TypeId|Win: ukazatele|Adresa MethodTable. Pokud existuje několik typů objektů, které byly přiděleny během této události, to je adresa MethodTable, která odpovídá na poslední objekt přidělené (objekt, který způsobil prahovou hodnotu 100 KB překročení).|  
|TypeName|Win: UnicodeString|Název typu, který byl přidělen. Pokud existuje několik typů objektů, které byly přiděleny během této události, jedná se o typ objektu poslední přidělené (objekt, který způsobil prahovou hodnotu 100 KB překročení).|  
|HeapIndex|Win: UInt32|Halda, kde byl přidělen objektu. Tato hodnota je 0 (nula) při spuštění s uvolňování paměti pracovních stanic.|  
  
 [Zpět na začátek](#top)  
  
<a name="gcfinalizersbegin_v1_event"></a>   
## <a name="gcfinalizersbeginv1-event"></a>GCFinalizersBegin_V1 událostí  
 V následující tabulce jsou uvedeny – klíčové slovo a úroveň.  
  
|– Klíčové slovo za vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá, když|  
|-----------|--------------|-----------------|  
|`GCFinalizersBegin_V1`|14|Počáteční spouštění finalizační metody.|  
  
 Žádná data.  
  
 [Zpět na začátek](#top)  
  
<a name="gcfinalizersend_v1_event"></a>   
## <a name="gcfinalizersendv1-event"></a>GCFinalizersEnd_V1 událostí  
 V následující tabulce jsou uvedeny – klíčové slovo a úroveň.  
  
|– Klíčové slovo za vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá, když|  
|-----------|--------------|-----------------|  
|`GCFinalizersEnd_V1`|13|Konec systémem finalizační metody.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|Počet|Win: UInt32|Počet finalizační metody, které byly spuštěné.|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
 [Zpět na začátek](#top)  
  
<a name="gccreateconcurrentthread_v1_event"></a>   
## <a name="gccreateconcurrentthreadv1-event"></a>GCCreateConcurrentThread_V1 událostí  
 V následující tabulce jsou uvedeny – klíčové slovo a úroveň.  
  
|– Klíčové slovo za vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informativní (4)|  
|`ThreadingKeyword` (0x10000)|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá, když|  
|-----------|--------------|-----------------|  
|`GCCreateConcurrentThread_V1`|11|Byl vytvořen souběžné uvolňování paměti kolekce přístup z více vláken.|  
  
 Žádná data.  
  
 [Zpět na začátek](#top)  
  
<a name="gcterminateconcurrentthread_v1_event"></a>   
## <a name="gcterminateconcurrentthreadv1-event"></a>GCTerminateConcurrentThread_V1 událostí  
 V následující tabulce jsou uvedeny – klíčové slovo a úroveň.  
  
|– Klíčové slovo za vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informativní (4)|  
|`ThreadingKeyword` (0x10000)|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá, když|  
|-----------|--------------|-----------------|  
|`GCTerminateConcurrentThread_V1`|12|Souběžné uvolňování paměti kolekce vlákno byl ukončen.|  
  
 Žádná data.  
  
## <a name="see-also"></a>Viz také  
 [Události Trasování událostí pro Windows v CLR](../../../docs/framework/performance/clr-etw-events.md)
