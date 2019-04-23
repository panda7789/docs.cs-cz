---
title: CorDebugChainReason – výčet
ms.date: 03/30/2017
api_name:
- CorDebugChainReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugChainReason
helpviewer_keywords:
- CorDebugChainReason enumeration [.NET Framework debugging]
ms.assetid: c915da51-50b2-41df-841a-2b971f4d0975
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cac790ebbf25ee3095db293ba90612be37fff9b9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59190441"
---
# <a name="cordebugchainreason-enumeration"></a>CorDebugChainReason – výčet
Označuje důvod nebo důvodů, proč inicializační řetězec volání.  
  
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
|`CHAIN_NONE`|Bylo zahájeno žádný řetězec volání.|  
|`CHAIN_CLASS_INIT`|Řetězec byl inicializován nástrojem konstruktor.|  
|`CHAIN_EXCEPTION_FILTER`|Řetězec byl inicializován nástrojem filtr výjimek.|  
|`CHAIN_SECURITY`|Řetězec byl inicializován nástrojem kód, který vynucuje zabezpečení.|  
|`CHAIN_CONTEXT_POLICY`|Řetězec byl inicializován nástrojem zásadu kontextu.|  
|`CHAIN_INTERCEPTION`|Nepoužívá se.|  
|`CHAIN_PROCESS_START`|Nepoužívá se.|  
|`CHAIN_THREAD_START`|Řetězec byl inicializován nástrojem začátku spuštění vlákna.|  
|`CHAIN_ENTER_MANAGED`|Řetězec byl inicializován nástrojem položku do spravovaného kódu.|  
|`CHAIN_ENTER_UNMANAGED`|Řetězec byl inicializován nástrojem vstupem nespravovaného kódu.|  
|`CHAIN_DEBUGGER_EVAL`|Nepoužívá se.|  
|`CHAIN_CONTEXT_SWITCH`|Nepoužívá se.|  
|`CHAIN_FUNC_EVAL`|Řetězec byl inicializován nástrojem vyhodnocení funkce.|  
  
## <a name="remarks"></a>Poznámky  
 Použití [icordebugchain::getreason –](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md) metoda zjistit důvody pro zahájení řetěz volání.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
