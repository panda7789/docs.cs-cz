---
title: 'ICorDebugMemoryBuffer:: GetStartAddress – metoda'
ms.date: 03/30/2017
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
ms.openlocfilehash: e2876398ceaf863bbb3c7e576d59b89c52f1bdaf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127991"
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a>ICorDebugMemoryBuffer:: GetStartAddress – metoda
Získá počáteční adresu vyrovnávací paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `address`  
 mimo Ukazatel na počáteční adresu vyrovnávací paměti.  
  
## <a name="remarks"></a>Poznámky  
  
> [!WARNING]
> Tato metoda je k dispozici pouze s .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugMemoryBuffer – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
