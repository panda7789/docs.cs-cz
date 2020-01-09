---
title: Události Trasování událostí pro Windows uvolnění paměti
ms.date: 03/30/2017
helpviewer_keywords:
- GC events
- garbage collection events [.NET Framework]
- ETW, garbage collection events (CLR)
ms.assetid: f14b6fd7-0966-4d87-bc89-54ef3a44a94a
ms.openlocfilehash: 5ff214314b92796f4a4a89ddd33a976d8b1f21d1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716073"
---
# <a name="garbage-collection-etw-events"></a>Události Trasování událostí pro Windows uvolnění paměti

Tyto události shromažďují informace týkající se uvolňování paměti. Pomáhá při diagnostice a ladění, včetně určení počtu provedených uvolnění paměti, o tom, kolik paměti bylo uvolněno během uvolňování paměti a tak dále.

Tato kategorie se skládá z následujících událostí:

- [GCStart_V1 Event](#gcstart_v1-event)
- [Událost GCEnd_V1](#gcend_v1-event)
- [GCHeapStats_V1 Event](#gcheapstats_v1-event)
- [GCCreateSegment_V1 Event](#gccreatesegment_v1-event)
- [GCFreeSegment_V1 Event](#gcfreesegment_v1-event)
- [GCRestartEEBegin_V1 Event](#gcrestarteebegin_v1-event)
- [Událost GCRestartEEEnd_V1](#gcrestarteeend_v1-event)
- [Událost GCSuspendEE_V1](#gcsuspendee_v1-event)
- [Událost GCSuspendEEEnd_V1](#gcsuspendeeend_v1-event)
- [Událost GCAllocationTick_V2](#gcallocationtick_v2-event)
- [Událost GCFinalizersBegin_V1](#gcfinalizersbegin_v1-event)
- [Událost GCFinalizersEnd_V1](#gcfinalizersend_v1-event)
- [GCCreateConcurrentThread_V1 Event](#gccreateconcurrentthread_v1-event)
- [Událost GCTerminateConcurrentThread_V1](#gcterminateconcurrentthread_v1-event)

## <a name="gcstart_v1-event"></a>Událost GCStart_V1  

Klíčové slovo a úroveň jsou uvedeny v následující tabulce. Další informace najdete v tématu [klíčová slova a úrovně CLR ETW](clr-etw-keywords-and-levels.md).

|Klíčové slovo pro vyvolání události|Úroveň|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Informační (4)|

Následující tabulka uvádí informace o událostech:

|Událost|ID události|Vyvolá se, když|
|-----------|--------------|-----------------|
|`GCStart_V1`|1|Bylo zahájeno uvolňování paměti.|

Následující tabulka ukazuje data události:

|Název pole|Datový typ|Popis|
|----------------|---------------|-----------------|
|Počet|Win: UInt32|*N*-tou kolekci uvolnění paměti.|
|Úrovní|Win: UInt32|Shromažďovaná generace.|
|Důvod|Win: UInt32|Proč se uvolňování paměti aktivovalo:<br /><br /> 0x0 – malé přidělení haldy objektů.<br /><br /> 0x1 – vyvolané.<br /><br /> 0x2 – nedostatek paměti<br /><br /> 0x3 – prázdné.<br /><br /> 0x4 – přidělení haldy velkých objektů.<br /><br /> 0x5 – nedostatek místa (pro haldu malých objektů)<br /><br /> 0x6 mimo prostor (pro haldu velkých objektů).<br /><br /> 0x7 – vyvolané, ale nevynucené jako blokující|
|Type|Win: UInt32|0x0 – blokující uvolňování paměti se nevyskytlo mimo uvolňování paměti na pozadí.<br /><br /> 0x1 – uvolňování paměti na pozadí<br /><br /> 0x2 – blokující uvolňování paměti došlo během uvolňování paměti na pozadí.|
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|

## <a name="gcend_v1-event"></a>Událost GCEnd_V1

Klíčové slovo a úroveň jsou uvedeny v následující tabulce:

|Klíčové slovo pro vyvolání události|Úroveň|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Informační (4)|

Následující tabulka uvádí informace o událostech:

|Událost|ID události|Vyvolá se, když|
|-----------|--------------|-----------------|
|`GCEnd_V1`|2|Uvolňování paměti bylo ukončeno.|

Následující tabulka ukazuje data události:

|Název pole|Datový typ|Popis|
|----------------|---------------|-----------------|
|Počet|Win: UInt32|*N*-tou kolekci uvolnění paměti.|
|Úrovní|Win: UInt32|Shromážděná generace.|
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|

## <a name="gcheapstats_v1-event"></a>Událost GCHeapStats_V1

Klíčové slovo a úroveň jsou uvedeny v následující tabulce:

|Klíčové slovo pro vyvolání události|Úroveň|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Informační (4)|

Následující tabulka uvádí informace o událostech:

|Událost|ID události|Popis|
|-----------|--------------|-----------------|
|`GCHeapStats_V1`|4|Zobrazuje statistiku haldy na konci každého uvolňování paměti.|

Následující tabulka ukazuje data události:

|Název pole|Datový typ|Popis|
|----------------|---------------|-----------------|
|GenerationSize0|win:UInt64|Velikost paměti generace 0 v bajtech.|
|TotalPromotedSize0|win:UInt64|Počet bajtů, které jsou povýšeny z generace 0 na generaci 1.|
|GenerationSize1|win:UInt64|Velikost paměti 1. generace v bajtech|
|TotalPromotedSize1|win:UInt64|Počet bajtů, které jsou povýšeny z generace 1 na generaci 2.|
|GenerationSize2|win:UInt64|Velikost paměti generace 2 v bajtech.|
|TotalPromotedSize2|win:UInt64|Počet bajtů, které byly zachovány v generaci 2 po poslední kolekci.|
|GenerationSize3|win:UInt64|Velikost haldy velkých objektů v bajtech.|
|TotalPromotedSize3|win:UInt64|Počet bajtů, které byly zachovány v haldě velkých objektů po poslední kolekci.|
|FinalizationPromotedSize|win:UInt64|Celková velikost objektů, které jsou připraveny k dokončení, v bajtech.|
|FinalizationPromotedCount|win:UInt64|Počet objektů, které jsou připraveny k dokončení.|
|PinnedObjectCount|Win: UInt32|Počet připnutých (nepohyblivých) objektů.|
|SinkBlockCount|Win: UInt32|Počet používaných synchronizačních bloků.|
|GCHandleCount|Win: UInt32|Počet používaných obslužných rutin uvolňování paměti.|
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|
  
## <a name="gccreatesegment_v1-event"></a>GCCreateSegment_V1 Event

Klíčové slovo a úroveň jsou uvedeny v následující tabulce:

|Klíčové slovo pro vyvolání události|Úroveň|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Informační (4)|

Následující tabulka uvádí informace o událostech:

|Událost|ID události|Vyvolá se, když|
|-----------|--------------|-----------------|
|`GCCreateSegment_V1`|5|Vytvořil se nový segment uvolňování paměti. Kromě toho, když je trasování povoleno na procesu, který je již spuštěn, tato událost je vyvolána pro každý existující segment.|

Následující tabulka ukazuje data události:

|Název pole|Datový typ|Popis|
|----------------|---------------|-----------------|
|Adresa|win:UInt64|Adresa segmentu.|
|Velikost|win:UInt64|Velikost segmentu|
|Type|Win: UInt32|0x0 – malá halda objektu.<br /><br /> 0x1 – halda velkých objektů<br /><br /> 0x2 – halda jen pro čtení.|
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|

Všimněte si, že velikost segmentů přidělených systémem uvolňování paměti je specifická pro konkrétní implementaci a může se kdykoli změnit, včetně pravidelné aktualizace. Vaše aplikace by nikdy neměla zabývat ani záviset na konkrétní velikosti segmentu, ani by se neměla pokoušet nakonfigurovat množství paměti dostupné pro přidělení segmentů.

## <a name="gcfreesegment_v1-event"></a>GCFreeSegment_V1 Event

Klíčové slovo a úroveň jsou uvedeny v následující tabulce:

|Klíčové slovo pro vyvolání události|Úroveň|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Informační (4)|

Následující tabulka uvádí informace o událostech:

|Událost|ID události|Vyvolá se, když|
|-----------|--------------|-----------------|
|`GCFreeSegment_V1`|6|Byl uvolněn segment uvolňování paměti.|

Následující tabulka ukazuje data události:

|Název pole|Datový typ|Popis|
|----------------|---------------|-----------------|
|Adresa|win:UInt64|Adresa segmentu.|
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|

## <a name="gcrestarteebegin_v1-event"></a>GCRestartEEBegin_V1 Event

Klíčové slovo a úroveň jsou uvedeny v následující tabulce:

|Klíčové slovo pro vyvolání události|Úroveň|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Informační (4)|

Následující tabulka uvádí informace o událostech:

|Událost|ID události|Vyvolá se, když|
|-----------|--------------|-----------------|
|`GCRestartEEBegin_V1`|7|Bylo zahájeno obnovení z pozastavení modulu CLR (Common Language Runtime).|

Žádná data události

## <a name="gcrestarteeend_v1-event"></a>Událost GCRestartEEEnd_V1

Klíčové slovo a úroveň jsou uvedeny v následující tabulce:

|Klíčové slovo pro vyvolání události|Úroveň|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Informační (4)|

Následující tabulka uvádí informace o událostech:

|Událost|ID události|Vyvolá se, když|
|-----------|--------------|-----------------|
|`GCRestartEEEnd_V1`|3|Obnovení z odložení modulu CLR (Common Language Runtime) skončilo.|

Žádná data události

## <a name="gcsuspendee_v1-event"></a>Událost GCSuspendEE_V1

Klíčové slovo a úroveň jsou uvedeny v následující tabulce:

|Klíčové slovo pro vyvolání události|Úroveň|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Informační (4)|

Následující tabulka uvádí informace o událostech:

|Událost|ID události|Vyvolá se, když|
|-----------|--------------|-----------------|
|`GCSuspendEE_V1`|9|Začátek pozastavení spouštěcího modulu pro uvolňování paměti.|

Následující tabulka ukazuje data události:

|Název pole|Datový typ|Popis|
|----------------|---------------|-----------------|
|Důvod|Win: UInt16|0x0 – ostatní<br /><br /> 0x1 – uvolňování paměti<br /><br /> 0x2 – vypnutí aplikační domény<br /><br /> 0x3 – rozteč kódu.<br /><br /> 0x4 – vypnutí<br /><br /> 0x5 – ladicí program.<br /><br /> 0x6 – příprava pro uvolňování paměti|
|Počet|Win: UInt32|Počet GC v daném okamžiku. Obvykle se vám po tomto zobrazení zobrazí další počáteční událost GC a její počet by byl tento počet + 1, protože během uvolňování paměti narůstá index GC.|
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|

## <a name="gcsuspendeeend_v1-event"></a>Událost GCSuspendEEEnd_V1

Klíčové slovo a úroveň jsou uvedeny v následující tabulce:

|Klíčové slovo pro vyvolání události|Úroveň|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Informační (4)|

Následující tabulka uvádí informace o událostech:

|Událost|ID události|Vyvolá se, když|
|-----------|--------------|-----------------|
|`GCSuspendEEEnd_V1`|8|Konec pozastavení prováděcího modulu pro uvolňování paměti|

Žádná data události

## <a name="gcallocationtick_v2-event"></a>Událost GCAllocationTick_V2

Klíčové slovo a úroveň jsou uvedeny v následující tabulce:

|Klíčové slovo pro vyvolání události|Úroveň|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Informační (4)|

Následující tabulka uvádí informace o událostech:

|Událost|ID události|Vyvolá se, když|
|-----------|--------------|-----------------|
|`GCAllocationTick_V2`|10|Pokaždé, když se přidělí přibližně 100 KB.|

Následující tabulka ukazuje data události:

|Název pole|Datový typ|Popis|
|----------------|---------------|-----------------|
|AllocationAmount|Win: UInt32|Velikost alokace (v bajtech). Tato hodnota je přesné pro přidělení, která jsou menší než délka ULONG (4 294 967 295 bajtů). Pokud je přidělení větší, obsahuje toto pole zkrácenou hodnotu. Pro velmi velké alokace použijte `AllocationAmount64`.|
|AllocationKind|Win: UInt32|0x0 – malé přidělení objektů (přidělení je v haldě malých objektů).<br /><br /> 0x1 – velké přidělení objektů (přidělení je v haldě velkých objektů).|
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|
|AllocationAmount64|win:UInt64|Velikost alokace (v bajtech). Tato hodnota je přesné pro velmi velké přidělení.|
|IDTypu|win:Pointer|Adresa metody. Pokud existuje několik typů objektů, které byly přiděleny během této události, jedná se o adresu metody, která odpovídá poslednímu přidělenému objektu (objekt, který způsobil překročení prahové hodnoty 100 KB).|
|TypeName|win:UnicodeString|Název typu, který byl přidělen. Pokud existuje několik typů objektů, které byly přiděleny během této události, jedná se o typ posledního přiděleného objektu (objekt, který způsobil překročení prahové hodnoty 100 KB).|
|HeapIndex|Win: UInt32|Halda, ve které byl objekt přidělen. Tato hodnota je 0 (nula) při spuštění s uvolňováním paměti pracovní stanice.|

## <a name="gcfinalizersbegin_v1-event"></a>Událost GCFinalizersBegin_V1

Klíčové slovo a úroveň jsou uvedeny v následující tabulce:

|Klíčové slovo pro vyvolání události|Úroveň|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Informační (4)|

Následující tabulka uvádí informace o událostech:

|Událost|ID události|Vyvolá se, když|
|-----------|--------------|-----------------|
|`GCFinalizersBegin_V1`|14|Začátek spuštění finalizační metody.|

Žádná data události

## <a name="gcfinalizersend_v1-event"></a>Událost GCFinalizersEnd_V1

Klíčové slovo a úroveň jsou uvedeny v následující tabulce:

|Klíčové slovo pro vyvolání události|Úroveň|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Informační (4)|

Následující tabulka uvádí informace o událostech:

|Událost|ID události|Vyvolá se, když|
|-----------|--------------|-----------------|
|`GCFinalizersEnd_V1`|13|Konec spuštění finalizační metody.|

Následující tabulka ukazuje data události:

|Název pole|Datový typ|Popis|
|----------------|---------------|-----------------|
|Počet|Win: UInt32|Počet finalizační metody, které byly spuštěny.|
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|

## <a name="gccreateconcurrentthread_v1-event"></a>GCCreateConcurrentThread_V1 Event

Klíčové slovo a úroveň jsou uvedeny v následující tabulce:

|Klíčové slovo pro vyvolání události|Úroveň|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Informační (4)|
|`ThreadingKeyword` (0x10000)|Informační (4)|

Následující tabulka uvádí informace o událostech:

|Událost|ID události|Vyvolá se, když|
|-----------|--------------|-----------------|
|`GCCreateConcurrentThread_V1`|11|Bylo vytvořeno souběžné vlákno uvolňování paměti.|

Žádná data události

## <a name="gcterminateconcurrentthread_v1-event"></a>Událost GCTerminateConcurrentThread_V1

Klíčové slovo a úroveň jsou uvedeny v následující tabulce:

|Klíčové slovo pro vyvolání události|Úroveň|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Informační (4)|
|`ThreadingKeyword` (0x10000)|Informační (4)|

Následující tabulka uvádí informace o událostech:

|Událost|ID události|Vyvolá se, když|
|-----------|--------------|-----------------|
|`GCTerminateConcurrentThread_V1`|12|Vlákno souběžného uvolňování paměti bylo ukončeno.|

Žádná data události

## <a name="see-also"></a>Viz také:

- [Události Trasování událostí pro Windows v CLR](clr-etw-events.md)
