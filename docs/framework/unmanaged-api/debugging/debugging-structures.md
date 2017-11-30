---
title: "Struktury pro ladění"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged structures [.NET Framework], debugging
- debugging structures [.NET Framework]
- structures [.NET Framework debugging]
ms.assetid: 173ba2c2-ab34-49ae-b6a8-e5c49882bf05
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0293a20f5f735dd38b1d167ebc5057f645fa011a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="debugging-structures"></a>Struktury pro ladění
Tato část popisuje nespravované struktury, která používá rozhraní API pro ladění.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Clr_debugging_version – struktura](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md)  
 Definuje verze produktu common language runtime (CLR) pro účely ladění.  
  
 [Codechunkinfo – – Struktura1](../../../../docs/framework/unmanaged-api/debugging/codechunkinfo-structure.md)  
 Představuje jeden blok kódu v paměti.  
  
 [Cordebugblockingobject – struktura](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)  
 Definuje objekt, který je blokování vlákna a důvod, proč je blokován vlákno.  
  
 [Struktura CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)  
 Představuje výjimku zpracování (EH) klauzuli pro určitou část převodní jazyk (IL).  
  
 [Cordebugexceptionobjectstackframe – struktura](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)  
 Představuje zásobníku rámce informace z objektu výjimky.  
  
 [Cordebugexceptionobjectstackframe – struktura](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)  
 Mapy [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID do její odpovídající [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) objektu.  
  
 COR_ACTIVE_FUNCTION –  
 Obsahuje informace o funkcích, které jsou momentálně aktivní v podprocesu rámce.  
  
 [Cor_array_layout – struktura](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md)  
 Poskytuje informace o rozložení objektu pole v paměti.  
  
 COR_DEBUG_IL_TO_NATIVE_MAP –  
 Obsahuje posuny, které se používají pro mapování kódu Microsoft (MSIL intermediate language) do nativního kódu.  
  
 COR_DEBUG_STEP_RANGE –  
 Obsahuje informace o posunu pro řadu kódu.  
  
 [Cor_field – struktura](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md)  
 Poskytuje informace o pole v objektu.  
  
 [Cor_gc_reference – struktura](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)  
 Obsahuje informace o objekt, který má být uvolňování paměti.  
  
 [Cor_heapinfo – struktura](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)  
 Poskytuje obecné informace o kolekci halda paměti, včetně toho, jestli je vyčíslitelná.  
  
 [Cor_heapobject – struktura](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)  
 Poskytuje informace o objekt na spravované haldě.  
  
 COR_IL_MAP –  
 Určuje změny v relativní posun funkce.  
  
 [Cor_segment – struktura](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md)  
 Obsahuje informace o oblasti spravovaná halda paměti.  
  
 [Cor_typeid – struktura](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)  
 Obsahuje identifikátor typu.  
  
 [Cor_type_layout – struktura](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md)  
 Poskytuje informace o rozložení objektu v paměti.  
  
 COR_VERSION –  
 Ukládá číslo standardní sestávající ze čtyř částí verze modulu CLR.  
  
 [Stacktrace_simplecontext – struktura](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md)  
 Poskytuje jednoduché kontext, který jde použít místo úplné `CONTEXT` struktura.  
  
## <a name="related-sections"></a>Související oddíly  
 [Ladění tříd typu coclass](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [Ladění v rozhraní](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [Globální statické funkce ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [Ladění výčtů](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
