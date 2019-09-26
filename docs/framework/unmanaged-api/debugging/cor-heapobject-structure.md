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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c59ddec655f3127e8dab8d8c41543f03a896cf63
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274038"
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
 `COR_HEAPOBJECT`instance lze načíst vytvořením výčtu objektu rozhraní [ICorDebugHeapEnum –](icordebugheapenum-interface.md) , který je vyplněn voláním metody [ICorDebugProcess5:: EnumerateHeap –](icordebugprocess5-enumerateheap-method.md) .  
  
 `COR_HEAPOBJECT` Instance poskytuje informace buď o živém objektu na spravované haldě, nebo o objektu, který není rootem žádného objektu, ale ještě nebyl shromážděn systémem uvolňování paměti.  
  
 Pro lepší výkon `COR_HEAPOBJECT.address` `CORDB_ADDRESS` je pole hodnota, nikoli hodnota rozhraní ICorDebugValue, která se používá v podstatě rozhraní API pro ladění. Chcete-li získat objekt ICorDebugValue pro danou adresu objektu, můžete předat `CORDB_ADDRESS` hodnotu metodě [ICorDebugProcess5:: GetObject](icordebugprocess5-getobject-method.md) .  
  
 Pro lepší výkon `COR_HEAPOBJECT.type` `COR_TYPEID` je pole hodnota, nikoli hodnota rozhraní ICorDebugType, která se používá v podstatě rozhraní API pro ladění. Chcete-li získat objekt ICorDebugType pro daný typ ID, můžete předat `COR_TYPEID` hodnotu metodě [ICorDebugProcess5:: GetTypeForTypeID –](icordebugprocess5-gettypefortypeid-method.md) .  
  
 `COR_HEAPOBJECT` Struktura zahrnuje rozhraní COM s vypočítáným odkazem. Pokud nanačítáte `COR_HEAPOBJECT` instanci z čítače pomocí volání metody [ICorDebugHeapEnum –:: Next](icordebugheapenum-next-method.md) , je nutné odkaz vydat následně.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** CorDebug. idl, CorDebug. h  
  
 **Knihovna** CorGuids.lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro ladění](debugging-structures.md)
- [Ladění](index.md)
