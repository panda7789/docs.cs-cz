---
title: Metoda ICorDebugDataTarget3::GetLoadedModules
ms.date: 03/30/2017
ms.assetid: 9a48c05b-1949-416e-933c-52549b6fcf5e
ms.openlocfilehash: d4c22146422085daa4dc9d90ae5b3735a12500c2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793558"
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
 mimo Ukazatel na pole objektů [Metoda ICorDebugLoadedModule](icordebugloadedmodule-interface.md) , které poskytují informace o načtených modulech.  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Tato metoda je k dispozici pouze s .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugDataTarget3 – rozhraní](icordebugdatatarget3-interface.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
