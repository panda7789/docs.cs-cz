---
title: ICorDebugHeapValue – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue
helpviewer_keywords:
- ICorDebugHeapValue interface [.NET Framework debugging]
ms.assetid: 1bca66db-0359-4ae8-846e-e35f7e547e8b
topic_type:
- apiref
ms.openlocfilehash: fa31b8a6cc96935319e9bef3e561790b65e33a87
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777594"
---
# <a name="icordebugheapvalue-interface"></a>ICorDebugHeapValue – rozhraní

Podtřída "ICorDebugValue", která představuje objekt, který byl shromážděn systémem uvolňování paměti modulu CLR (Common Language Runtime).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CreateRelocBreakpoint – metoda](icordebugheapvalue-createrelocbreakpoint-method.md)|Není implementováno.|  
|[IsValid – metoda](icordebugheapvalue-isvalid-method.md)|Získá hodnotu, která označuje, zda je objekt reprezentovaný tímto `ICorDebugHeapValue` platný, nebo byl uvolněn systémem uvolňování paměti. Tato metoda je zastaralá ve verzi .NET Framework 2,0.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](debugging-interfaces.md)
