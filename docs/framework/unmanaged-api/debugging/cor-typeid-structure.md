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
ms.openlocfilehash: 4f6dbe8c17bd6a91078b87a87c1055fbf4977a88
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132298"
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
 Struktura `COR_TYPEID` je vrácena několika metodami ladění, které poskytují informace o objektech, které mají být sbírány do paměti. Lze jej předat jako argument pro jiné metody ladění, které poskytují další informace o této položce. Například vytvořením výčtu objektu [ICorDebugHeapEnum –](icordebugheapenum-interface.md) můžete načíst jednotlivé objekty [COR_HEAPOBJECT](cor-heapobject-structure.md) , které reprezentují jednotlivé objekty ve spravované haldě. Pak můžete předat `COR_TYPEID` hodnotu z pole `COR_HEAPOBJECT.type` do metody [ICorDebugProcess5:: GetTypeForTypeID –](icordebugprocess5-gettypefortypeid-method.md) pro načtení objektu ICorDebugType, který poskytuje informace o typu objektu.  
  
 Objekt `COR_TYPEID` má být neprůhledný. K jednotlivým polím by neměl být přistup nebo manipulace. Jeho jediným použitím je identifikátor, který je k dispozici jako parametr `out` ve volání metody a který může být následně předán jiným metodám k poskytnutí dalších informací.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro ladění](debugging-structures.md)
- [Ladění](index.md)
