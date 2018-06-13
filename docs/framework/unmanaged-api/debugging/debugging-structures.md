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
ms.openlocfilehash: 6c7415920d34fc231bf82dd00199c7e01eec7a73
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408109"
---
# <a name="debugging-structures"></a>Struktury pro ladění
Tato část popisuje nespravované struktury, která používá rozhraní API pro ladění.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [CLR_DEBUGGING_VERSION – struktura](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md)  
 Definuje verze produktu common language runtime (CLR) pro účely ladění.  
  
 [CodeChunkInfo – struktura 1](../../../../docs/framework/unmanaged-api/debugging/codechunkinfo-structure.md)  
 Představuje jeden blok kódu v paměti.  
  
 [CorDebugBlockingObject – struktura](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)  
 Definuje objekt, který je blokování vlákna a důvod, proč je blokován vlákno.  
  
 [CorDebugEHClause – struktura](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)  
 Představuje výjimku zpracování (EH) klauzuli pro určitou část převodní jazyk (IL).  
  
 [CorDebugExceptionObjectStackFrame – struktura](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)  
 Představuje zásobníku rámce informace z objektu výjimky.  
  
 [CorDebugExceptionObjectStackFrame – struktura](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)  
 Mapy [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID do její odpovídající [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) objektu.  
  
 COR_ACTIVE_FUNCTION –  
 Obsahuje informace o funkcích, které jsou momentálně aktivní v podprocesu rámce.  
  
 [COR_ARRAY_LAYOUT – struktura](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md)  
 Poskytuje informace o rozložení objektu pole v paměti.  
  
 COR_DEBUG_IL_TO_NATIVE_MAP –  
 Obsahuje posuny, které se používají pro mapování kódu Microsoft (MSIL intermediate language) do nativního kódu.  
  
 COR_DEBUG_STEP_RANGE –  
 Obsahuje informace o posunu pro řadu kódu.  
  
 [COR_FIELD – struktura](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md)  
 Poskytuje informace o pole v objektu.  
  
 [COR_GC_REFERENCE – struktura](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)  
 Obsahuje informace o objekt, který má být uvolňování paměti.  
  
 [COR_HEAPINFO – struktura](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)  
 Poskytuje obecné informace o kolekci halda paměti, včetně toho, jestli je vyčíslitelná.  
  
 [COR_HEAPOBJECT – struktura](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)  
 Poskytuje informace o objekt na spravované haldě.  
  
 COR_IL_MAP –  
 Určuje změny v relativní posun funkce.  
  
 [COR_SEGMENT – struktura](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md)  
 Obsahuje informace o oblasti spravovaná halda paměti.  
  
 [COR_TYPEID – struktura](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)  
 Obsahuje identifikátor typu.  
  
 [COR_TYPE_LAYOUT – struktura](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md)  
 Poskytuje informace o rozložení objektu v paměti.  
  
 COR_VERSION –  
 Ukládá číslo standardní sestávající ze čtyř částí verze modulu CLR.  
  
 [StackTrace_SimpleContext – struktura](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md)  
 Poskytuje jednoduché kontext, který jde použít místo úplné `CONTEXT` struktura.  
  
## <a name="related-sections"></a>Související oddíly  
 [Třídy typu coclass pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [Globální statické funkce pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
