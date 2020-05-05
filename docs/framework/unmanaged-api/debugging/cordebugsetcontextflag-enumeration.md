---
title: CorDebugSetContextFlag – výčet
ms.date: 03/30/2017
api_name:
- CorDebugSetContextFlag
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugSetContextFlag
helpviewer_keywords:
- CorDebugSetContextFlag enumeration [.NET Framework debugging]
ms.assetid: b30280bb-fe75-44ed-8589-bcff081fae44
topic_type:
- apiref
ms.openlocfilehash: a3214fc4e52918716f183720c7c616b1fff74bdb
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795674"
---
# <a name="cordebugsetcontextflag-enumeration"></a>CorDebugSetContextFlag – výčet
Označuje, zda je kontext z aktivního (nebo koncového) rámce v zásobníku nebo byl vypočítán odvinutím z jiného rámce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorDebugSetContextFlag  
{  
   SET_CONTEXT_FLAG_ACTIVE_FRAME = 1  
   SET_CONTEXT_FLAG_UNWIND_FRAME = 2  
}  CorDebugSetContextFlag;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|SET_CONTEXT_FLAG_ACTIVE_FRAME|Kontext je aktivní kontext vlákna.|  
|SET_CONTEXT_FLAG_UNWIND_FRAME|Kontext byl vypočítán odvinutím z jiného rámce.|  
  
## <a name="remarks"></a>Poznámky  
 `CorDebugSetContextFlag`poskytuje hodnoty, které jsou používány metodou [ICorDebugStackWalk:: SetContext](icordebugstackwalk-setcontext-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Ladění výčtů](debugging-enumerations.md)
- [Ladění](index.md)
