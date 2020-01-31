---
title: CorDebugExceptionObjectStackFrame – struktura
ms.date: 03/30/2017
api_name:
- CorDebugExceptionObjectStackFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionObjectStackFrame
helpviewer_keywords:
- CorDebugExceptionObjectStackFrame structure [.NET Framework debugging]
ms.assetid: 542cdd81-5ae7-4361-b0ef-1ae4775df258
topic_type:
- apiref
ms.openlocfilehash: 2845c15d67e287d6efb0cd0a9c940b69de3a1c0c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789367"
---
# <a name="cordebugexceptionobjectstackframe-structure"></a>CorDebugExceptionObjectStackFrame – struktura
Představuje informace o snímku zásobníku z objektu výjimky.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct CorDebugExceptionObjectStackFrame {  
    ICorDebugModule* pModule;  
    CORDB_ADDRESS ip;  
    mdMethodDef methodDef;  
    BOOL isLastForeignExceptionFrame;  
} CorDebugExceptionObjectStackFrame;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`pModule`|Ukazatel na objekt ICorDebugModule pro aktuální rámec.|  
|`ip`|Hodnota ukazatele instrukce (EIP/RIP) pro aktuální rámec.|  
|`methodDef`|Token metody pro aktuální rámec.|  
|`isLastForeignExceptionFrame`|Hodnota, která označuje, zda je rámec posledním snímkem v cizí výjimce.|  
  
## <a name="remarks"></a>Poznámky  
 Volající musí uvolnit ukazatel na objekt ICorDebugModule, jakmile se již nepoužívá.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro ladění](debugging-structures.md)
- [Ladění](index.md)
