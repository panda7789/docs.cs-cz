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
ms.openlocfilehash: efb3d913e1d8ef0c486d7e5e1d9777ae7d88bc71
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179338"
---
# <a name="cor_heapobject-structure"></a>COR_HEAPOBJECT – struktura
Obsahuje informace o objektu na spravované haldě.  
  
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
|`type`|Token [COR_TYPEID,](cor-typeid-structure.md) který představuje typ objektu.|  
  
## <a name="remarks"></a>Poznámky  
 `COR_HEAPOBJECT`instance lze načíst výčetem objektu rozhraní [ICorDebugHeapEnum,](icordebugheapenum-interface.md) který je naplněn voláním metody [ICorDebugProcess5::EnumerateHeap.](icordebugprocess5-enumerateheap-method.md)  
  
 Instance `COR_HEAPOBJECT` poskytuje informace o živém objektu na spravované haldě nebo o objektu, který není zakořeněn žádným objektem, ale ještě nebyl shromážděn systémem uvolňování paměti.  
  
 Pro lepší výkon `COR_HEAPOBJECT.address` pole `CORDB_ADDRESS` je hodnota spíše než hodnota rozhraní ICorDebugValue používá ve velké části ladění rozhraní API. Chcete-li získat objekt ICorDebugValue pro danou adresu `CORDB_ADDRESS` objektu, můžete předat hodnotu metodě [ICorDebugProcess5::GetObject.](icordebugprocess5-getobject-method.md)  
  
 Pro lepší výkon `COR_HEAPOBJECT.type` pole `COR_TYPEID` je hodnota spíše než hodnota rozhraní ICorDebugType používá ve velké části ladění rozhraní API. Chcete-li získat objekt ICorDebugType pro dané ID `COR_TYPEID` typu, můžete předat hodnotu metodě [ICorDebugProcess5::GetTypeForTypeID.](icordebugprocess5-gettypefortypeid-method.md)  
  
 `COR_HEAPOBJECT` Struktura obsahuje referenční rozhraní COM. Pokud načtete `COR_HEAPOBJECT` instanci z čítače výčtu voláním Metody [ICorDebugHeapEnum::Next,](icordebugheapenum-next-method.md) musíte následně uvolnit odkaz.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Struktury pro ladění](debugging-structures.md)
- [ladění](index.md)
