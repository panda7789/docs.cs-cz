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
ms.openlocfilehash: a3d4297e3b16dd1637e6293dbf7f04d4fbeda50f
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860381"
---
# <a name="iclrdebugging-interface"></a>ICLRDebugging – rozhraní
Poskytuje metody, které zpracovávají načítání a uvolňování modulů pro ladění.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[OpenVirtualProcess – metoda](iclrdebugging-openvirtualprocess-method.md)|Získá rozhraní "ICorDebugProcess", které odpovídá modulu CLR (Common Language Runtime) načtenému v procesu.|  
|[CanUnloadNow – metoda](iclrdebugging-canunloadnow-method.md)|Určuje, zda se knihovna, která byla poskytnuta rozhraním [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) , stále používá, nebo může být uvolněna.|  
  
## <a name="remarks"></a>Poznámky  
 Můžete získat instanci `ICLRDebugging` rozhraní pomocí funkce [CLRCreateInstance –](../hosting/clrcreateinstance-function.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Debugging – rozhraní](debugging-interfaces.md)
- [Ladění](index.md)
