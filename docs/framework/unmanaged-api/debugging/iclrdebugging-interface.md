---
title: ICLRDebugging – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRDebugging
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging
helpviewer_keywords:
- ICLRDebugging interface [.NET Framework debugging]
ms.assetid: 429d8fce-b1b1-49d7-895c-28c1c1aa2dbd
topic_type:
- apiref
ms.openlocfilehash: 6506b11d97490f796486729dbeb612e47762b60a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73111440"
---
# <a name="iclrdebugging-interface"></a>ICLRDebugging – rozhraní
Poskytuje metody, které zpracovávají načítání a uvolňování modulů pro ladění.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[OpenVirtualProcess – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md)|Získá rozhraní "ICorDebugProcess", které odpovídá modulu CLR (Common Language Runtime) načtenému v procesu.|  
|[CanUnloadNow – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md)|Určuje, zda se knihovna, která byla poskytnuta rozhraním [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) , stále používá, nebo může být uvolněna.|  
  
## <a name="remarks"></a>Poznámky  
 Můžete získat instanci rozhraní `ICLRDebugging` pomocí funkce [CLRCreateInstance –](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
