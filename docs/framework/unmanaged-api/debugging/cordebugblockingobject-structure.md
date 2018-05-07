---
title: CorDebugBlockingObject – struktura
ms.date: 03/30/2017
api_name:
- CorDebugBlockingObject Structure
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugBlockingObject
helpviewer_keywords:
- CorDebugBlockingObject structure [.NET Framework debugging]
ms.assetid: 5944edd1-0914-4efa-aba0-d5a277c38b1a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed7db321b32657087b791758096c692f25f3d7f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cordebugblockingobject-structure"></a>CorDebugBlockingObject – struktura
Definuje objekt, který je blokování vlákna a určitého důvodu, že je blokované vlákno.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Typedef struct CorDebugBlockingObject  
{  
ICorDebugValue pBlockingObject;  
DWORD dwTimeout;  
CorDebugBlockingReason blockingReason;  
}  CorDebugBlockingObject;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`pBlockingObject`|Objekt, na kterém je blokování vlákno. Tento objekt je platný pouze po dobu trvání aktuálního stavu synchronizovaná. Pokud se dvěma vlákny blokují na stejný objekt v rámci stejné synchronizovaného stavu, můžete očekávat [icordebugvalue::getaddress –](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md) metoda vrátí stejnou hodnotu. Rozhraní však může nebo nemusí být ukazatel ekvivalentní.|  
|`dwTimeout`|Počet milisekund, po předtím, než blokování operace bude vypršení časového limitu, nebo hodnotu NEKONEČNÉ, který označuje, že ji není vypršení časového limitu. Hodnota časového limitu určuje celková délka čas blokování operace, není čas, který je stále zbývající.|  
|`blockingReason`|Z důvodu, že je na tomto objektu blokované vlákno.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Struktury pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
