---
title: Metoda ICorDebugDataTarget3::GetLoadedModules
ms.date: 03/30/2017
ms.assetid: 9a48c05b-1949-416e-933c-52549b6fcf5e
ms.openlocfilehash: 6ee2215e2b3e3bd911158b3fc801361fc4e22db1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136687"
---
# <a name="icordebugdatatarget3getloadedmodules-method"></a>Metoda ICorDebugDataTarget3::GetLoadedModules
Načte seznam modulů, které byly doposud načteny.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetLoadedModules(  
   [in] ULONG32 cRequestedModules,  
   [out] ULONG32 *pcFetchedModules,  
   [out, size_is(cRequestedModules), length_is(*pcFetchedModules)] ICorDebugLoadedModule *pLoadedModules[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `cRequestedModules`  
 pro Počet modulů, pro které jsou požadovány informace.  
  
 `pcFetchedModules`  
 mimo Ukazatel na počet modulů, které informace byly vráceny.  
  
 `pLoadedModules`  
 mimo Ukazatel na pole objektů [Metoda ICorDebugLoadedModule](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md) , které poskytují informace o načtených modulech.  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Tato metoda je k dispozici pouze s .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugDataTarget3 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
