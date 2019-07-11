---
title: ICorDebugMergedAssemblyRecord::GetCulture – metoda
ms.date: 03/30/2017
ms.assetid: 030b2f8c-8c21-40b7-855d-3afa78975a17
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0472a52d0893bfd487cd6daa6548ec1ce0c44a9b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762206"
---
# <a name="icordebugmergedassemblyrecordgetculture-method"></a>ICorDebugMergedAssemblyRecord::GetCulture – metoda
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
 [in] Počet znaků `szCulture` vyrovnávací paměti.  
  
 `pcchCulture`  
 [out] Počet aktuálně zapsaných do znaků `szCulture` vyrovnávací paměti.  
  
 `szCulture`  
 [out] Pole znaků, který obsahuje název jazykové verze.  
  
## <a name="remarks"></a>Poznámky  
 Název jazykové verze je jedinečný řetězec, který určuje jazykovou verzi, například "en US" (pro jazykové verze Angličtina (Spojené státy)) nebo "neutrální" (pro neutrální jazykovou verzi).  
  
> [!NOTE]
>  Tato metoda je pouze k dispozici s .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugMergedAssemblyRecord – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
