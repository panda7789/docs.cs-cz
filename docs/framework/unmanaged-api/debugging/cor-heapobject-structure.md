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
ms.openlocfilehash: 91e64bb2e1c8a7b11fe70024eb4a4fa1717c06e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407346"
---
# <a name="corheapobject-structure"></a>COR_HEAPOBJECT – struktura
Poskytuje informace o objekt na spravované haldě.  
  
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
 `COR_HEAPOBJECT` může načíst vytváření výčtu instancí [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) rozhraní objekt, který je vyplněný voláním [icordebugprocess5::enumerateheap –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) metoda.  
  
 A `COR_HEAPOBJECT` instance poskytuje informace o objekt za provozu na spravovaná halda nebo o objekt, který není root pomocí libovolného objektu, ale nebyla ještě zjištěna modulem garbage collector.  
  
 Pro lepší výkon `COR_HEAPOBJECT.address` pole `CORDB_ADDRESS` hodnota než ICorDebugValue rozhraní hodnoty používané prakticky rozhraní API pro ladění. Pokud chcete získat objekt ICorDebugValue pro daný objekt adresu, můžete předat `CORDB_ADDRESS` hodnotu [icordebugprocess5::GetObject –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md) metoda.  
  
 Pro lepší výkon `COR_HEAPOBJECT.type` pole `COR_TYPEID` hodnota než ICorDebugType rozhraní hodnoty používané prakticky rozhraní API pro ladění. Získat ICorDebugType objekt daného typu ID, abyste mohli předávat `COR_TYPEID` hodnotu [icordebugprocess5::gettypefortypeid –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md) metoda.  
  
 `COR_HEAPOBJECT` Struktura zahrnuje rozhraní modelu COM počítá odkaz. Pokud je načíst `COR_HEAPOBJECT` instance z enumerátor voláním [icordebugheapenum::Next –](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) metoda, je nutné uvolnit následně odkaz na.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Struktury pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
