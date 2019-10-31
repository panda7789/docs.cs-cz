---
title: COR_HEAPOBJECT – struktura
ms.date: 03/30/2017
api_name:
- COR_HEAPOBJECT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_HEAPOBJECT
helpviewer_keywords:
- COR_HEAPOBJECT structure [.NET Framework debugging]
ms.assetid: a92fdf95-492b-49ae-a741-2186e5c1d7c5
topic_type:
- apiref
ms.openlocfilehash: 270360a8950197eca14e02a60554659e5ac7b91c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099081"
---
# <a name="cor_heapobject-structure"></a>COR_HEAPOBJECT – struktura
Poskytuje informace o objektu na spravované haldě.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _COR_HEAPOBJECT {  
    CORDB_ADDRESS address;    
    ULONG64 size;             
    COR_TYPEID type;          
} COR_HEAPOBJECT;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`address`|Adresa objektu v paměti.|  
|`size`|Celková velikost objektu v bajtech.|  
|`type`|Token [COR_TYPEID](cor-typeid-structure.md) , který představuje typ objektu.|  
  
## <a name="remarks"></a>Poznámky  
 instance `COR_HEAPOBJECT` lze načíst vytvořením výčtu objektu rozhraní [ICorDebugHeapEnum –](icordebugheapenum-interface.md) , který je vyplněn voláním metody [ICorDebugProcess5:: EnumerateHeap –](icordebugprocess5-enumerateheap-method.md) .  
  
 Instance `COR_HEAPOBJECT` poskytuje informace buď o živém objektu na spravované haldě, nebo o objektu, který není rootem žádného objektu, ale ještě nebyl shromážděn systémem uvolňování paměti.  
  
 Pro lepší výkon je pole `COR_HEAPOBJECT.address` `CORDB_ADDRESS` hodnota, nikoli hodnota rozhraní ICorDebugValue, která se používá v podstatě rozhraní API pro ladění. Chcete-li získat objekt ICorDebugValue pro danou adresu objektu, můžete předat `CORDB_ADDRESS` hodnotu metodě [ICorDebugProcess5:: GetObject](icordebugprocess5-getobject-method.md) .  
  
 Pro lepší výkon je pole `COR_HEAPOBJECT.type` `COR_TYPEID` hodnota, nikoli hodnota rozhraní ICorDebugType, která se používá v podstatě rozhraní API pro ladění. Chcete-li získat objekt ICorDebugType pro daný typ ID, můžete předat `COR_TYPEID` hodnotu metodě [ICorDebugProcess5:: GetTypeForTypeID –](icordebugprocess5-gettypefortypeid-method.md) .  
  
 Struktura `COR_HEAPOBJECT` zahrnuje rozhraní COM s vypočítáným odkazem. Pokud načtete instanci `COR_HEAPOBJECT` z čítače voláním metody [ICorDebugHeapEnum –:: Next](icordebugheapenum-next-method.md) , je nutné odkaz vydat následně.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro ladění](debugging-structures.md)
- [Ladění](index.md)
