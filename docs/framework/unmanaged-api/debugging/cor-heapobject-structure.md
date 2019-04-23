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
ms.openlocfilehash: f179b58ff8eb51e2843780d3212cf38ed7d13216
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59168828"
---
# <a name="corheapobject-structure"></a>COR_HEAPOBJECT – struktura
Poskytuje informace o objektu na spravované haldě.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|`type`|A [cor_typeid –](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token, který představuje typ objektu.|  
  
## <a name="remarks"></a>Poznámky  
 `COR_HEAPOBJECT` instance je možné načíst podle výčet [icordebugheapenum –](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) rozhraní objektu, který je vyplněný voláním [icordebugprocess5::enumerateheap –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) metody.  
  
 A `COR_HEAPOBJECT` instance obsahuje informace o objektu na spravované haldě za provozu nebo o objekt, který není uveden do kořene s jakýmkoli objektem, ale nebyl dosud shromažďuje systému uvolňování paměti.  
  
 Pro zajištění lepšího výkonu `COR_HEAPOBJECT.address` je pole `CORDB_ADDRESS` hodnotu, nikoli icordebugvalue – rozhraní hodnota použitá v velkou část rozhraní API pro ladění. K získání objektu ICorDebugValue pro daný objekt adresu, můžete předat `CORDB_ADDRESS` hodnota, která se [icordebugprocess5::GetObject –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md) metody.  
  
 Pro zajištění lepšího výkonu `COR_HEAPOBJECT.type` je pole `COR_TYPEID` hodnotu, nikoli icordebugtype – rozhraní hodnota použitá v velkou část rozhraní API pro ladění. Získat ICorDebugType objekt daného typu ID, můžete předat `COR_TYPEID` hodnota, která se [icordebugprocess5::gettypefortypeid –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md) metody.  
  
 `COR_HEAPOBJECT` Struktura zahrnuje rozhraní modelu COM počítaného odkazy. Pokud načtete `COR_HEAPOBJECT` instanci z výčtu voláním [icordebugheapenum::Next –](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) metoda, následně nutné uvolnit odkaz.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
