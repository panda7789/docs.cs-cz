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
ms.openlocfilehash: 5d76fa4b2352da18b5ef0e547ebc4e2e99d980b8
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71273999"
---
# <a name="cor_typeid-structure"></a>COR_TYPEID – struktura
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
 `COR_TYPEID` Struktura je vrácena řadou metod ladění, které poskytují informace o objektech, které mají být shromažďovány z paměti. Lze jej předat jako argument pro jiné metody ladění, které poskytují další informace o této položce. Například vytvořením výčtu objektu [ICorDebugHeapEnum –](icordebugheapenum-interface.md) můžete načíst jednotlivé objekty [COR_HEAPOBJECT](cor-heapobject-structure.md) , které reprezentují jednotlivé objekty ve spravované haldě. Pak můžete předat `COR_TYPEID` hodnotu `COR_HEAPOBJECT.type` z pole do metody [ICorDebugProcess5:: GetTypeForTypeID –](icordebugprocess5-gettypefortypeid-method.md) pro načtení objektu ICorDebugType, který poskytuje informace o typu objektu.  
  
 `COR_TYPEID` Objekt by měl být neprůhledný. K jednotlivým polím by neměl být přistup nebo manipulace. Jeho jediným použitím je identifikátor, který je k dispozici jako `out` parametr ve volání metody a který může být následně předán jiným metodám k poskytnutí dalších informací.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** CorDebug. idl, CorDebug. h  
  
 **Knihovna** CorGuids.lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro ladění](debugging-structures.md)
- [Ladění](index.md)
