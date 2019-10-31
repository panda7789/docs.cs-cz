---
title: Metoda ICorDebugLoadedModule::GetName
ms.date: 03/30/2017
ms.assetid: 88c304d5-edaa-4c0e-a8e1-144e8a76877e
ms.openlocfilehash: 4cf2c5c099de3d66878f09ff702a1cad6ddb8f57
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122626"
---
# <a name="icordebugloadedmodulegetname-method"></a>Metoda ICorDebugLoadedModule::GetName
Získá název načteného modulu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,  
   [out] ULONG32 *pcchName,  
   [out, size_is(cchName),  
   length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `cchName`  
 pro Počet znaků ve vyrovnávací paměti `szName`.  
  
 `pcchName`  
 mimo Ukazatel na počet znaků skutečně zapsaných do vyrovnávací paměti `szName`.  
  
 `szName`  
 mimo Pole znaků, které obsahují název načteného modulu.  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Tato metoda je k dispozici pouze s .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugLoadedModule – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
