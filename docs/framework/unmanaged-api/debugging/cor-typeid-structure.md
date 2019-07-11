---
title: COR_TYPEID – struktura
ms.date: 03/30/2017
api_name:
- COR_TYPEID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_TYPEID
helpviewer_keywords:
- COR_TYPEID structure [.NET Framework debugging]
ms.assetid: 1e172b14-ee22-4943-b3b8-3740e7bdcd2e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 426420175a7d05f39859b9e217a888a8c01b6d63
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740497"
---
# <a name="cortypeid-structure"></a>COR_TYPEID – struktura
Obsahuje identifikátor typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct COR_TYPEID{  
    UINT64 token1;  
    UINT64 token2;  
} COR_TYPEID;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`token1`|První token.|  
|`token2`|Druhý token.|  
  
## <a name="remarks"></a>Poznámky  
 `COR_TYPEID` Struktura je vrácen počet ladění metody, které poskytují informace o objektech být uvolněna. Může pak být předán jako argument jiné ladění metody, které poskytují další informace o této položce. Například vytyčením [icordebugheapenum –](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) objektu, je možné získat jednotlivé [cor_heapobject –](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objekty, které představují jednotlivé objekty na spravované haldě. Můžete předat `COR_TYPEID` hodnotu `COR_HEAPOBJECT.type` pole [icordebugprocess5::gettypefortypeid –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md) metodu pro načtení ICorDebugType objekt, který poskytuje typ informace o objektu.  
  
 A `COR_TYPEID` objektu má být neprůhledné. Jednotlivých polí by neměl být přistupovat ani s nimi manipulovat. Jako identifikátor, který je k dispozici jako je výhradní použití `out` parametr ve volání metody a, který může být předán do jiné metody, které poskytují další informace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
