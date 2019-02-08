---
title: Struktury pro ladění
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged structures [.NET Framework], debugging
- debugging structures [.NET Framework]
- structures [.NET Framework debugging]
ms.assetid: 173ba2c2-ab34-49ae-b6a8-e5c49882bf05
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 18bf03fee1a95c898e8273fa839e41a86b2d1c32
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/07/2019
ms.locfileid: "55828368"
---
# <a name="debugging-structures"></a>Struktury pro ladění
Tato část popisuje nespravované struktury, které používá rozhraní API pro ladění.

## <a name="in-this-section"></a>V tomto oddílu
 [Struktura CLRDATA_ADDRESS_RANGE](../../../../docs/framework/unmanaged-api/debugging/clrdata-address-range-structure.md) definuje rozsah adres.

 [Struktura CLRDATA_IL_ADDRESS_MAP](../../../../docs/framework/unmanaged-api/debugging/clrdata-il-address-map-structure.md) definuje IL pro mapování adresy

 [Clr_debugging_version – struktura](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) Určuje verzi modulu common language runtime (CLR) pro účely ladění.

 [CodeChunkInfo – struktura 1](../../../../docs/framework/unmanaged-api/debugging/codechunkinfo-structure.md) představuje jediný neodkazovaný blok kódu v paměti.

 [Cor_active_function –](cor-active-function-structure.md) obsahuje informace o funkcích, které jsou aktuálně aktivní vlákna snímků.

 [Cor_array_layout – struktura](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) poskytuje informace o rozložení objektu array v paměti.

 [Cor_debug_il_to_native_map –](cor-debug-il-to-native-map-structure.md) obsahuje kód posuny, které se používají k mapování jazyk Microsoft intermediate language (MSIL) do nativního kódu.

 [Cor_debug_step_range –](cor-debug-step-range-structure.md) obsahuje informace o posunu pro celou řadu kódu.

 [Cor_field – struktura](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) poskytuje informace o pole v objektu.

 [Cor_gc_reference – struktura](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) obsahuje informace o objektu, který má být uvolněna.

 [Cor_heapinfo – struktura](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) poskytuje obecné informace o haldě uvolňování paměti kolekce, včetně toho, zda je vyčíslitelná.

 [Cor_heapobject – struktura](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) poskytuje informace o objektu na spravované haldě.

 [Cor_il_map –](cor-il-map-structure.md) určuje změny v relativním posunem funkce.

 [Cor_segment – struktura](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) obsahuje informace o oblasti paměti spravované haldy.

 [Cor_typeid – struktura](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) obsahuje identifikátor typu.

 [Cor_type_layout – struktura](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) poskytuje informace o rozložení objektu v paměti.

 [Cor_version –](cor-version-structure.md) ukládá číslo standardní sestávající ze čtyř částí verze modulu common language runtime.

 [Cordebugblockingobject – struktura](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) definuje objekt, který blokuje vlákno a důvod, proč je vlákno blokované.

 [Struktura CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) představuje klauzuli výjimka zpracování (EH) pro danou část (IL intermediate language).

 [Cordebugexceptionobjectstackframe – struktura](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) představuje zásobník snímků informace z objektu výjimky.

 [Cordebugguidtotypemapping – struktura](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) mapy [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID odpovídající [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) objektu.

 [Struktura DacpGetModuleAddress](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-structure.md) definuje kontejner pro žádost o adresu modulu.

 [Struktura DacpMethodDescData](../../../../docs/framework/unmanaged-api/debugging/dacpmethoddescdata-structure.md) definuje přenos vyrovnávací paměť pro informace o modulu runtime metody.

 [Struktura DacpModuleData](../../../../docs/framework/unmanaged-api/debugging/dacpmoduledata-structure.md) definuje přenos vyrovnávací paměť pro informace o modulu runtime.

 [Struktura DacpReJitData](../../../../docs/framework/unmanaged-api/debugging/dacprejitdata-structure.md) definuje základních informací o dané metody instrumentována profileru.

 [Stacktrace_simplecontext – struktura](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) poskytuje jednoduché kontext, který jde použít místo úplné `CONTEXT` struktury.



## <a name="related-sections"></a>Související oddíly
 [Třídy typu coclass pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)

 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

 [Globální statické funkce pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)

 [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
