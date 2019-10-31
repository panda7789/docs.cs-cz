---
title: 'ICorDebugMergedAssemblyRecord:: getculture – metoda'
ms.date: 03/30/2017
ms.assetid: 030b2f8c-8c21-40b7-855d-3afa78975a17
ms.openlocfilehash: f39a1f17c80d27a38c0f2a8a516405f72c79bbcf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131416"
---
# <a name="icordebugmergedassemblyrecordgetculture-method"></a>ICorDebugMergedAssemblyRecord:: getculture – metoda
Získá řetězec názvu jazykové verze sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCulture(  
   [in] ULONG32 cchCulture,   
   [out] ULONG32 *pcchCulture,   
   [out, size_is(cchCulture), length_is(*pcchCulture)] WCHAR szCulture[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `cchCulture`  
 pro Počet znaků ve vyrovnávací paměti `szCulture`.  
  
 `pcchCulture`  
 mimo Počet znaků skutečně zapsaných do vyrovnávací paměti `szCulture`.  
  
 `szCulture`  
 mimo Pole znaků, které obsahuje název jazykové verze.  
  
## <a name="remarks"></a>Poznámky  
 Název jazykové verze je jedinečný řetězec, který identifikuje jazykovou verzi, jako je "en-US" (pro anglickou (USA) jazykovou verzi), nebo "neutrální" (pro neutrální jazykovou verzi).  
  
> [!NOTE]
> Tato metoda je k dispozici pouze s .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugMergedAssemblyRecord – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
