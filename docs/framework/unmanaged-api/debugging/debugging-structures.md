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
ms.openlocfilehash: 23aa619d666f2e0b9eb67ab4cf8d4f92761865d3
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415322"
---
# <a name="debugging-structures"></a>Struktury pro ladění
Tato část popisuje nespravované struktury, které používá rozhraní API pro ladění.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [CLR_DEBUGGING_VERSION – struktura](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md)  
 Určuje verzi modulu common language runtime (CLR) pro účely ladění.  
  
 [CodeChunkInfo – struktura 1](../../../../docs/framework/unmanaged-api/debugging/codechunkinfo-structure.md)  
 Představuje jediný neodkazovaný blok kódu v paměti.  
  
 [CorDebugBlockingObject – struktura](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)  
 Definuje objekt, který blokuje vlákno a důvod, proč je vlákno blokované.  
  
 [CorDebugEHClause – struktura](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)  
 Představuje výjimku zpracování – klauzule (EH) pro danou část (IL intermediate language).  
  
 [CorDebugExceptionObjectStackFrame – struktura](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)  
 Představuje zásobník snímků informace z objektu výjimky.  
  
 [CorDebugExceptionObjectStackFrame – struktura](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)  
 Mapy [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID odpovídající [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) objektu.  
  
 COR_ACTIVE_FUNCTION  
 Obsahuje informace o funkcích, které jsou aktuálně aktivní vlákna snímků.  
  
 [COR_ARRAY_LAYOUT – struktura](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md)  
 Poskytuje informace o rozložení objektu array v paměti.  
  
 COR_DEBUG_IL_TO_NATIVE_MAP  
 Obsahuje posuny, které se používají k mapování kód Microsoft intermediate language (MSIL) do nativního kódu.  
  
 COR_DEBUG_STEP_RANGE  
 Obsahuje informace o posunu pro celou řadu kódu.  
  
 [COR_FIELD – struktura](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md)  
 Poskytuje informace o pole v objektu.  
  
 [COR_GC_REFERENCE – struktura](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)  
 Obsahuje informace o objektu, který má být uvolněna.  
  
 [COR_HEAPINFO – struktura](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)  
 Obsahuje obecné informace o haldě uvolňování paměti kolekce, včetně toho, zda je vyčíslitelná.  
  
 [COR_HEAPOBJECT – struktura](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)  
 Poskytuje informace o objektu na spravované haldě.  
  
 COR_IL_MAP  
 Určuje změny v relativním posunem funkce.  
  
 [COR_SEGMENT – struktura](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md)  
 Obsahuje informace o oblasti paměti spravované haldy.  
  
 [COR_TYPEID – struktura](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)  
 Obsahuje identifikátor typu.  
  
 [COR_TYPE_LAYOUT – struktura](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md)  
 Poskytuje informace o rozložení objektu v paměti.  
  
 COR_VERSION  
 Ukládá číslo standardní sestávající ze čtyř částí verze modulu common language runtime.  
  
 [StackTrace_SimpleContext – struktura](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md)  
 Poskytuje jednoduchý kontext, který jde použít místo úplné `CONTEXT` struktury.

 [Struktura CLRDATA_ADDRESS_RANGE](../../../../docs/framework/unmanaged-api/debugging/clrdata-address-range-structure.md) definuje rozsah adres.
 
 [Struktura CLRDATA_IL_ADDRESS_MAP](../../../../docs/framework/unmanaged-api/debugging/clrdata-il-address-map-structure.md) definuje IL pro mapování adresy
 
 [Struktura DacpGetModuleAddress](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-structure.md) definuje kontejner pro žádost o adresu modulu.

  
## <a name="related-sections"></a>Související oddíly  
 [Třídy typu coclass pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [Globální statické funkce pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
