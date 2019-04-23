---
title: Události Trasování událostí pro Windows uvolnění paměti
ms.date: 03/30/2017
helpviewer_keywords:
- GC events
- garbage collection events [.NET Framework]
- ETW, garbage collection events (CLR)
ms.assetid: f14b6fd7-0966-4d87-bc89-54ef3a44a94a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7f9bf0e309ec8c77d4b1d6afbf111e7eeae629ac
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59149731"
---
# <a name="garbage-collection-etw-events"></a>Události Trasování událostí pro Windows uvolnění paměti
<a name="top"></a> Tyto události shromažďovat informace týkající se uvolňování paměti. Pomáhají v Diagnostika a ladění, včetně určení, kolikrát uvolňování paměti byla provedena, kolik paměti byl uvolněn při uvolňování paměti a tak dále.  
  
 Tato kategorie se skládá z následujících událostí:  
  
-   [GCStart_V1 Event](#gcstart_v1_event)  
  
-   [GCEnd_V1 události](#gcend_v1_event)  
  
-   [GCHeapStats_V1 Event](#gcheapstats_v1_event)  
  
-   [GCCreateSegment_V1 Event](#gccreatesegment_v1_event)  
  
-   [GCFreeSegment_V1 Event](#gcfreesegment_v1_event)  
  
-   [GCRestartEEBegin_V1 Event](#gcrestarteebegin_v1_event)  
  
-   [GCRestartEEEnd_V1 Event](#gcrestarteeend_v1_event)  
  
-   [GCSuspendEE_V1 události](#gcsuspendee_v1_event)  
  
-   [GCSuspendEEEnd_V1 události](#gcsuspendeeend_v1_event)  
  
-   [GCAllocationTick_V2 události](#gcallocationtick_v2_event)  
  
-   [GCFinalizersBegin_V1 události](#gcfinalizersbegin_v1_event)  
  
-   [GCFinalizersEnd_V1 události](#gcfinalizersend_v1_event)  
  
-   [GCCreateConcurrentThread_V1 Event](#gccreateconcurrentthread_v1_event)  
  
-   [GCTerminateConcurrentThread_V1 Event](#gcterminateconcurrentthread_v1_event)  
  
<a name="gcstart_v1_event"></a>   
## <a name="gcstartv1-event"></a>GCStart_V1 Event  
 V následující tabulce jsou uvedeny klíčové slovo a úroveň. (Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Klíčové slovo pro vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`GCStart_V1`|1|Uvolňování paměti byla spuštěna.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|Počet|win:UInt32|*n*th uvolňování paměti.|  
|Hloubka|win:UInt32|Generování, jež jsou shromažďována.|  
|Důvod|win:UInt32|Proč byla aktivována. uvolnění:<br /><br /> 0x0 - přidělení haldy malých objektů.<br /><br /> 0x1 - vyvolaných.<br /><br /> 0x2 - nedostatek paměti.<br /><br /> 0x3 - prázdný.<br /><br /> 0x4 - přidělení haldy velkých objektů.<br /><br /> 0x5 - nedostatek místa (pro haldu malých objektů).<br /><br /> 0x6 - nedostatek místa (pro haldu velkých objektů).<br /><br /> 0x7 - vyvolané, ale nejsou vynucené jako blokování.|  
|Type|win:UInt32|0x0 - mimo uvolňování paměti na pozadí došlo k blokování uvolnění paměti.<br /><br /> 0x1 – uvolňování paměti na pozadí.<br /><br /> 0x2 - blokující uvolňování paměti došlo k chybě během uvolňování paměti na pozadí.|  
|ClrInstanceID|win:UInt16|Jedinečné ID instance CLR nebo CoreCLR.|  
  
 [Zpět na začátek](#top)  
  
<a name="gcend_v1_event"></a>   
## <a name="gcendv1-event"></a>GCEnd_V1 události  
 V následující tabulce jsou uvedeny klíčové slovo a úroveň.  
  
|Klíčové slovo pro vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`GCEnd_V1`|2|Kolekce paměti bylo již ukončeno.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|Počet|win:UInt32|*n*th uvolňování paměti.|  
|Hloubka|win:UInt32|Generace, která byla shromážděna.|  
|ClrInstanceID|win:UInt16|Jedinečné ID instance CLR nebo CoreCLR.|  
  
 [Zpět na začátek](#top)  
  
<a name="gcheapstats_v1_event"></a>   
## <a name="gcheapstatsv1-event"></a>GCHeapStats_V1 Event  
 V následující tabulce jsou uvedeny klíčové slovo a úroveň.  
  
|Klíčové slovo pro vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Popis|  
|-----------|--------------|-----------------|  
|`GCHeapStats_V1`|4|Zobrazuje statistiku haldě na konci každé uvolňování paměti.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|GenerationSize0|win:UInt64|Velikost v bajtech paměti generace 0.|  
|TotalPromotedSize0|win:UInt64|Počet bajtů, které jsou přesunuty z 0. generace do 1. generace.|  
|GenerationSize1|win:UInt64|Velikost v bajtech paměti generace 1.|  
|TotalPromotedSize1|win:UInt64|Počet bajtů, které jsou přesunuty z 1. generace do 2. generace.|  
|GenerationSize2|win:UInt64|Velikost v bajtech paměti generace 2.|  
|TotalPromotedSize2|win:UInt64|Počet bajtů, které zůstat naživu v generaci 2 po poslední.|  
|GenerationSize3|win:UInt64|Velikost v bajtech, velkých objektových haldách.|  
|TotalPromotedSize3|win:UInt64|Počet bajtů, které zůstat naživu haldy velkých objektů po poslední.|  
|FinalizationPromotedSize|win:UInt64|Celková velikost v bajtech, objektů, které jsou připraveny k dokončení.|  
|FinalizationPromotedCount|win:UInt64|Počet objektů, které jsou připraveny k dokončení.|  
|PinnedObjectCount|win:UInt32|Počet připojených objektů (o nepřesunutelnou).|  
|SinkBlockCount|win:UInt32|Počet bloků synchronizace používá.|  
|GCHandleCount|win:UInt32|Počet uvolňování zpracovává používá.|  
|ClrInstanceID|win:UInt16|Jedinečné ID instance CLR nebo CoreCLR.|  
  
 [Zpět na začátek](#top)  
  
<a name="gccreatesegment_v1_event"></a>   
## <a name="gccreatesegmentv1-event"></a>GCCreateSegment_V1 Event  
 V následující tabulce jsou uvedeny klíčové slovo a úroveň.  
  
|Klíčové slovo pro vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`GCCreateSegment_V1`|5|Vytvořil se nový segment kolekce uvolnění paměti. Kromě toho když je povoleno trasování procesu, který je již spuštěn, tato událost je aktivována pro každý existující segment.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|Adresa|win:UInt64|Adresa segmentu.|  
|Velikost|win:UInt64|Velikost segmentu.|  
|Type|win:UInt32|0x0 - haldy malých objektů.<br /><br /> 0x1 - velkých objektových haldách.<br /><br /> 0x2 - haldy jen pro čtení.|  
|ClrInstanceID|win:UInt16|Jedinečné ID instance CLR nebo CoreCLR.|  
  
 Mějte na paměti, že velikost segmentů přidělaná systému uvolňování paměti je specifický pro implementaci a může se změnit kdykoli, včetně v pravidelné aktualizace. Vaše aplikace by nikdy vytvořit předpoklady o nebo závisí na velikosti konkrétního segmentu, ani snažit konfigurace množství paměti k přidělení segmentu.  
  
 [Zpět na začátek](#top)  
  
<a name="gcfreesegment_v1_event"></a>   
## <a name="gcfreesegmentv1-event"></a>GCFreeSegment_V1 Event  
 V následující tabulce jsou uvedeny klíčové slovo a úroveň.  
  
|Klíčové slovo pro vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`GCFreeSegment_V1`|6|Segment uvolňování paměti kolekce byla uvolněna.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|Adresa|win:UInt64|Adresa segmentu.|  
|ClrInstanceID|win:UInt16|Jedinečné ID instance CLR nebo CoreCLR.|  
  
 [Zpět na začátek](#top)  
  
<a name="gcrestarteebegin_v1_event"></a>   
## <a name="gcrestarteebeginv1-event"></a>GCRestartEEBegin_V1 Event  
 V následující tabulce jsou uvedeny klíčové slovo a úroveň.  
  
|Klíčové slovo pro vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`GCRestartEEBegin_V1`|7|Bylo zahájeno obnovení z common language runtime pozastavení.|  
  
 Žádná data.  
  
 [Zpět na začátek](#top)  
  
<a name="gcrestarteeend_v1_event"></a>   
## <a name="gcrestarteeendv1-event"></a>GCRestartEEEnd_V1 Event  
 V následující tabulce jsou uvedeny klíčové slovo a úroveň.  
  
|Klíčové slovo pro vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|Id události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`GCRestartEEEnd_V1`|3|Obnovení z common language runtime pozastavení skončila.|  
  
 Žádná data.  
  
 [Zpět na začátek](#top)  
  
<a name="gcsuspendee_v1_event"></a>   
## <a name="gcsuspendeev1-event"></a>GCSuspendEE_V1 události  
 V následující tabulce jsou uvedeny klíčové slovo a úroveň.  
  
|Klíčové slovo pro vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`GCSuspendEE_V1`|9|Začátek pozastavení prováděcí modul pro uvolnění paměti.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|Důvod|win:UInt16|0x0 – ostatní.<br /><br /> 0x1 – uvolňování paměti.<br /><br /> 0x2 – ukončení domény aplikace.<br /><br /> 0x3 - pitching kódu.<br /><br /> 0x4 – vypnutí.<br /><br /> 0x5 – ladicí program.<br /><br /> 0x6 – Příprava pro uvolnění paměti.|  
|Počet|win:UInt32|Uvolňování paměti – počet v době. Obvykle zobrazí následující události Start uvolňování paměti po to a její vlastnosti Count by tento počet + 1 jsme zvýšit index uvolňování paměti během uvolňování paměti.|  
|ClrInstanceID|win:UInt16|Jedinečné ID instance CLR nebo CoreCLR.|  
  
 [Zpět na začátek](#top)  
  
<a name="gcsuspendeeend_v1_event"></a>   
## <a name="gcsuspendeeendv1-event"></a>GCSuspendEEEnd_V1 události  
 V následující tabulce jsou uvedeny – klíčové slovo a úroveň:  
  
|Klíčové slovo pro vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události:  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`GCSuspendEEEnd_V1`|8|Konec pozastavení prováděcí modul pro uvolnění paměti.|  
  
 Žádná data.  
  
 [Zpět na začátek](#top)  
  
<a name="gcallocationtick_v2_event"></a>   
## <a name="gcallocationtickv2-event"></a>GCAllocationTick_V2 události  
 V následující tabulce jsou uvedeny klíčové slovo a úroveň.  
  
|Klíčové slovo pro vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`GCAllocationTick_V2`|10|Pokaždé, když je přidělen přibližně 100 KB.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|AllocationAmount|win:UInt32|Přidělení velikost v bajtech. Tato hodnota je přesné pro přidělení, která jsou menší než délka ULONG (4,294,967,295 bajtů). Pokud přidělení paměti je větší, toto pole obsahuje zkrácená hodnota. Použití `AllocationAmount64` velmi velkého přidělení.|  
|AllocationKind|win:UInt32|0x0 - přidělení malých objektů (přidělení je haldy malých objektů).<br /><br /> 0x1 – rozdělení velkých objektů (přidělení je v haldy velkých objektů).|  
|ClrInstanceID|win:UInt16|Jedinečné ID instance CLR nebo CoreCLR.|  
|AllocationAmount64|win:UInt64|Přidělení velikost v bajtech. Tato hodnota je přesné pro velmi velkého přidělení.|  
|TypeId|win:Pointer|Adresa MethodTable. Když existuje několik typů objektů, které byly přiděleny během této události, jde o adresu MethodTable, která odpovídá na poslední objekt přidělený (objekt, který způsobil překročení prahovou hodnotu 100 KB).|  
|TypeName|win:UnicodeString|Název typu, který byl přidělen. Když existuje několik typů objektů, které byly přiděleny během této události, toto je typ objektu poslední přidělené (objekt, který způsobil překročení prahovou hodnotu 100 KB).|  
|HeapIndex|win:UInt32|Haldy, ve kterém byla objektu přidělena. Tato hodnota je 0 (nula), když budou běžet s uvolnění paměti pracovní stanice.|  
  
 [Zpět na začátek](#top)  
  
<a name="gcfinalizersbegin_v1_event"></a>   
## <a name="gcfinalizersbeginv1-event"></a>GCFinalizersBegin_V1 události  
 V následující tabulce jsou uvedeny klíčové slovo a úroveň.  
  
|Klíčové slovo pro vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`GCFinalizersBegin_V1`|14|Zahájení spuštění finalizační metody.|  
  
 Žádná data.  
  
 [Zpět na začátek](#top)  
  
<a name="gcfinalizersend_v1_event"></a>   
## <a name="gcfinalizersendv1-event"></a>GCFinalizersEnd_V1 události  
 V následující tabulce jsou uvedeny klíčové slovo a úroveň.  
  
|Klíčové slovo pro vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`GCFinalizersEnd_V1`|13|Konec spuštění finalizační metody.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|Počet|win:UInt32|Počet finalizační metody, které byly spuštěny.|  
|ClrInstanceID|win:UInt16|Jedinečné ID instance CLR nebo CoreCLR.|  
  
 [Zpět na začátek](#top)  
  
<a name="gccreateconcurrentthread_v1_event"></a>   
## <a name="gccreateconcurrentthreadv1-event"></a>GCCreateConcurrentThread_V1 Event  
 V následující tabulce jsou uvedeny klíčové slovo a úroveň.  
  
|Klíčové slovo pro vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informativní (4)|  
|`ThreadingKeyword` (0x10000)|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`GCCreateConcurrentThread_V1`|11|Souběžné uvolňování paměti kolekce vlákno bylo vytvořeno.|  
  
 Žádná data.  
  
 [Zpět na začátek](#top)  
  
<a name="gcterminateconcurrentthread_v1_event"></a>   
## <a name="gcterminateconcurrentthreadv1-event"></a>GCTerminateConcurrentThread_V1 události  
 V následující tabulce jsou uvedeny klíčové slovo a úroveň.  
  
|Klíčové slovo pro vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informativní (4)|  
|`ThreadingKeyword` (0x10000)|Informativní (4)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`GCTerminateConcurrentThread_V1`|12|Vlákno souběžné uvolňování paměti byla ukončena.|  
  
 Žádná data.  
  
## <a name="see-also"></a>Viz také:

- [Události Trasování událostí pro Windows v CLR](../../../docs/framework/performance/clr-etw-events.md)
