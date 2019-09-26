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
ms.openlocfilehash: fce803544b393ac2c441779183cbf49d4c39bdae
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71273982"
---
# <a name="cordebugchainreason-enumeration"></a>CorDebugChainReason – výčet
Určuje důvod nebo důvody pro zahájení řetězu volání.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
|`CHAIN_NONE`|Neinicioval se žádný řetěz volání.|  
|`CHAIN_CLASS_INIT`|Řetěz byl iniciován konstruktorem.|  
|`CHAIN_EXCEPTION_FILTER`|Řetěz byl iniciován filtrem výjimky.|  
|`CHAIN_SECURITY`|Řetězec byl iniciován kódem, který vynutil zabezpečení.|  
|`CHAIN_CONTEXT_POLICY`|Řetěz byl iniciován zásadami kontextu.|  
|`CHAIN_INTERCEPTION`|Nepoužívá se.|  
|`CHAIN_PROCESS_START`|Nepoužívá se.|  
|`CHAIN_THREAD_START`|Řetěz byl iniciován zahájením provádění vlákna.|  
|`CHAIN_ENTER_MANAGED`|Řetězec byl iniciován zadáním do spravovaného kódu.|  
|`CHAIN_ENTER_UNMANAGED`|Řetězec byl iniciován vložením do nespravovaného kódu.|  
|`CHAIN_DEBUGGER_EVAL`|Nepoužívá se.|  
|`CHAIN_CONTEXT_SWITCH`|Nepoužívá se.|  
|`CHAIN_FUNC_EVAL`|Řetěz byl iniciován vyhodnocením funkce.|  
  
## <a name="remarks"></a>Poznámky  
 Použijte metodu [ICorDebugChain:: getdůvod](icordebugchain-getreason-method.md) k zjištění důvodů pro zahájení řetězu volání.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** CorDebug. idl, CorDebug. h  
  
 **Knihovna** CorGuids.lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro ladění](debugging-enumerations.md)
