---
title: ICorDebugMergedAssemblyRecord::Metoda GetCulture
ms.date: 03/30/2017
ms.assetid: 030b2f8c-8c21-40b7-855d-3afa78975a17
ms.openlocfilehash: ad54a93b16e803170987dd56d8063669f7e67f94
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178755"
---
# <a name="icordebugmergedassemblyrecordgetculture-method"></a>ICorDebugMergedAssemblyRecord::Metoda GetCulture
Získá řetězec název jazykové verze sestavení.  
  
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
 [v] Počet znaků ve `szCulture` vyrovnávací paměti.  
  
 `pcchCulture`  
 [out] Počet znaků skutečně zapsaných `szCulture` do vyrovnávací paměti.  
  
 `szCulture`  
 [out] Pole znaků, které obsahuje název jazykové verze.  
  
## <a name="remarks"></a>Poznámky  
 Název jazykové verze je jedinečný řetězec, který identifikuje jazykovou verzi, například "en US" (pro jazykovou verzi angličtiny (Spojené státy) nebo "neutrální" (pro neutrální jazykovou verzi).  
  
> [!NOTE]
> Tato metoda je k dispozici pouze s nativní .NET.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugMergedAssemblyRecord – rozhraní](icordebugmergedassemblyrecord-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
