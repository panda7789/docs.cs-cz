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
ms.openlocfilehash: 57de11c1c40c05befcf3c99c31c2e07e1ecaec5a
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71273969"
---
# <a name="cordebugblockingobject-structure"></a>CorDebugBlockingObject – struktura
Definuje objekt, který blokuje vlákno, a konkrétní důvod, proč je vlákno blokované.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
|`pBlockingObject`|Objekt, na kterém vlákno blokuje. Tento objekt je platný pouze po dobu trvání aktuálního synchronizovaného stavu. Pokud jsou dvě vlákna blokována u stejného objektu ve stejném synchronizovaném stavu, může být očekávána metoda [ICorDebugValue:: GetAddress](icordebugvalue-getaddress-method.md) , která vrací stejnou hodnotu. Rozhraní však mohou nebo nemusí být ekvivalentem ukazatele.|  
|`dwTimeout`|Počet milisekund, po jejichž uplynutí vyprší časový limit operace blokování, nebo hodnota nekonečno, což znamená, že nedojde k vypršení časového limitu. Hodnota časového limitu určuje celkovou dobu blokující operace, nikoli čas, který je stále zbývající.|  
|`blockingReason`|Důvod, proč je vlákno na tomto objektu blokováno.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** CorDebug. idl  
  
 **Knihovna** CorGuids.lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro ladění](debugging-structures.md)
- [Ladění](index.md)
