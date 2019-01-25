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
ms.openlocfilehash: 49521e4b4ff5f8c364827b233759e163aca43e39
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54542652"
---
# <a name="cordebugblockingobject-structure"></a>CorDebugBlockingObject – struktura
Definuje objekt, který blokuje vlákno a z určitého důvodu, že je vlákno blokované.  
  
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
|`pBlockingObject`|Objekt, na kterém je blokování vlákna. Tento objekt je platný pouze po dobu trvání aktuálního stavu synchronizovaná. Pokud se dvěma vlákny blokují na stejný objekt v rámci stejného synchronizovaného stavu, můžete očekávat [icordebugvalue::getaddress –](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md) metody vrátí stejnou hodnotu. Rozhraní však může nebo nemusí být ukazatel ekvivalentní.|  
|`dwTimeout`|Počet milisekund před blokující operace způsobí vypršení časového limitu, nebo hodnota NEKONEČNO, což znamená, že bude omezen časovým limitem. Hodnota časového limitu určuje celkový čas blokující operace, bez času, který je stále zbývající.|  
|`blockingReason`|Důvodu, že je vlákno blokované, u tohoto objektu.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [Struktury pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
