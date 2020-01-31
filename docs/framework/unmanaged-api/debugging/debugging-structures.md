---
title: Struktury pro ladění
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged structures [.NET Framework], debugging
- debugging structures [.NET Framework]
- structures [.NET Framework debugging]
ms.assetid: 173ba2c2-ab34-49ae-b6a8-e5c49882bf05
ms.openlocfilehash: a18094fb2621478dbdb4bbf672df436234112ed0
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793754"
---
# <a name="debugging-structures"></a>Struktury pro ladění

Tato část popisuje nespravované struktury, které používá rozhraní API pro ladění.

## <a name="in-this-section"></a>V tomto oddílu
 [Struktura CLRDATA_ADDRESS_RANGE](clrdata-address-range-structure.md) Definuje rozsah adres.

 [Struktura CLRDATA_IL_ADDRESS_MAP](clrdata-il-address-map-structure.md) Definuje mapování IL na adresu.

 [Struktura CLR_DEBUGGING_VERSION](clr-debugging-version-structure.md) Definuje verzi produktu modulu CLR (Common Language Runtime) pro účely ladění.

 [Struktura codechunkinfo –](codechunkinfo-structure.md) Představuje jeden blok kódu v paměti.

 [COR_ACTIVE_FUNCTION](cor-active-function-structure.md) Obsahuje informace o funkcích, které jsou aktuálně aktivní v rámečcích vlákna.

 [Struktura COR_ARRAY_LAYOUT](cor-array-layout-structure.md) Poskytuje informace o rozložení objektu pole v paměti.

 [COR_DEBUG_IL_TO_NATIVE_MAP](cor-debug-il-to-native-map-structure.md) Obsahuje posuny, které se používají k mapování kódu jazyka MSIL (Microsoft Intermediate Language) do nativního kódu.

 [COR_DEBUG_STEP_RANGE](cor-debug-step-range-structure.md) Obsahuje informace o posunu pro rozsah kódu.

 [Struktura COR_FIELD](cor-field-structure.md) Poskytuje informace o poli v objektu.

 [Struktura COR_GC_REFERENCE](cor-gc-reference-structure.md) Obsahuje informace o objektu, který má být shromážděn z paměti.

 [Struktura COR_HEAPINFO](cor-heapinfo-structure.md) Poskytuje obecné informace o haldě uvolňování paměti, včetně toho, zda je vyčíslitelné.

 [Struktura COR_HEAPOBJECT](cor-heapobject-structure.md) Poskytuje informace o objektu na spravované haldě.

 [COR_IL_MAP](cor-il-map-structure.md) Určuje změny relativního posunu funkce.

 [Struktura COR_SEGMENT](cor-segment-structure.md) Obsahuje informace o oblasti paměti ve spravované haldě.

 [Struktura COR_TYPEID](cor-typeid-structure.md) Obsahuje identifikátor typu.

 [Struktura COR_TYPE_LAYOUT](cor-type-layout-structure.md) Poskytuje informace o rozložení objektu v paměti.

 [COR_VERSION](cor-version-structure.md) Ukládá standardní číslo verze se čtyřmi částmi modulu CLR (Common Language Runtime).

 [Struktura CorDebugBlockingObject –](cordebugblockingobject-structure.md) Definuje objekt, který blokuje vlákno, a důvod, proč je vlákno blokované.

 [Struktura CorDebugEHClause](cordebugehclause-structure.md) Představuje klauzuli zpracování výjimek (EH) pro danou část mezilehlého jazyka (IL).

 [Struktura CorDebugExceptionObjectStackFrame –](cordebugexceptionobjectstackframe-structure.md) Představuje informace o snímku zásobníku z objektu výjimky.

 [Struktura CorDebugGuidToTypeMapping –](cordebugguidtotypemapping-structure.md) Mapuje identifikátor GUID prostředí Windows Runtime na odpovídající objekt [ICorDebugType](icordebugtype-interface.md) .

 [Struktura DacpGetModuleAddress](dacpgetmoduleaddress-structure.md) Definuje kontejner pro požadavek na adresu modulu.

 [Struktura DacpMethodDescData](dacpmethoddescdata-structure.md) Definuje přenosovou vyrovnávací paměť pro běhové informace metody.

 [Struktura DacpModuleData](dacpmoduledata-structure.md) Definuje přenosovou vyrovnávací paměť pro běhové informace modulu.

 [Struktura DacpReJitData](dacprejitdata-structure.md) Definuje základní informace o dané metodě instrumentace profileru.

 [Struktura StackTrace_SimpleContext](stacktrace-simplecontext-structure.md) Poskytuje jednoduchý kontext, který lze použít místo úplné `CONTEXT` struktury.

## <a name="related-sections"></a>Související oddíly

 [Třídy typu coclass pro ladění](debugging-coclasses.md)

 [Rozhraní pro ladění](debugging-interfaces.md)

 [Globální statické funkce pro ladění](debugging-global-static-functions.md)

 [Výčty pro ladění](debugging-enumerations.md)

 [Ladění](index.md)
