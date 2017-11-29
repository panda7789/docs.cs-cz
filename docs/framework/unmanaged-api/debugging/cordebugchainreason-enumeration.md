---
title: "CorDebugChainReason – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugChainReason
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugChainReason
helpviewer_keywords: CorDebugChainReason enumeration [.NET Framework debugging]
ms.assetid: c915da51-50b2-41df-841a-2b971f4d0975
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0d501db111256861a3d0a602712e4c32f40b7b6e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="cordebugchainreason-enumeration"></a>CorDebugChainReason – výčet
Označuje důvod nebo důvody pro zahájení řetěz volání.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorDebugChainReason {  
    CHAIN_NONE              = 0x000,  
    CHAIN_CLASS_INIT        = 0x001,  
    CHAIN_EXCEPTION_FILTER  = 0x002,  
    CHAIN_SECURITY          = 0x004,  
    CHAIN_CONTEXT_POLICY    = 0x008,  
    CHAIN_INTERCEPTION      = 0x010,  
    CHAIN_PROCESS_START     = 0x020,  
    CHAIN_THREAD_START      = 0x040,  
    CHAIN_ENTER_MANAGED     = 0x080,  
    CHAIN_ENTER_UNMANAGED   = 0x100,  
    CHAIN_DEBUGGER_EVAL     = 0x200,  
    CHAIN_CONTEXT_SWITCH    = 0x400,  
    CHAIN_FUNC_EVAL         = 0x800  
} CorDebugChainReason;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`CHAIN_NONE`|Byla inicializována žádné řetěz volání.|  
|`CHAIN_CLASS_INIT`|Řetězu byl inicializován nástrojem konstruktor.|  
|`CHAIN_EXCEPTION_FILTER`|Řetězu byl inicializován nástrojem filtru výjimek.|  
|`CHAIN_SECURITY`|Řetězu byl inicializován nástrojem kód, který vynucuje zabezpečení.|  
|`CHAIN_CONTEXT_POLICY`|Řetězu byl inicializován nástrojem zásadu kontextu.|  
|`CHAIN_INTERCEPTION`|Nepoužívá se.|  
|`CHAIN_PROCESS_START`|Nepoužívá se.|  
|`CHAIN_THREAD_START`|Řetězu byl inicializován nástrojem spuštění provádění vlákna.|  
|`CHAIN_ENTER_MANAGED`|Řetězu byl inicializován nástrojem položku do spravovaného kódu.|  
|`CHAIN_ENTER_UNMANAGED`|Řetězu byl inicializován nástrojem položka nespravovaný kód.|  
|`CHAIN_DEBUGGER_EVAL`|Nepoužívá se.|  
|`CHAIN_CONTEXT_SWITCH`|Nepoužívá se.|  
|`CHAIN_FUNC_EVAL`|Řetězu byl inicializován nástrojem vyhodnocení funkce.|  
  
## <a name="remarks"></a>Poznámky  
 Použití [icordebugchain::getreason –](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md) metoda zjistit důvody pro zahájení řetěz volání.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Ladění výčtů](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
