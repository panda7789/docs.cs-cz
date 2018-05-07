---
title: ICorDebugMergedAssemblyRecord::GetCulture – metoda
ms.date: 03/30/2017
ms.assetid: 030b2f8c-8c21-40b7-855d-3afa78975a17
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2f2336c89a32b202c4226f1ed194d786be6fa020
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmergedassemblyrecordgetculture-method"></a>ICorDebugMergedAssemblyRecord::GetCulture – metoda
Získá řetězec název jazykové verze sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetCulture(  
   [in] ULONG32 cchCulture,   
   [out] ULONG32 *pcchCulture,   
   [out, size_is(cchCulture), length_is(*pcchCulture)] WCHAR szCulture[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cchCulture`  
 [v] Počet znaků `szCulture` vyrovnávací paměti.  
  
 `pcchCulture`  
 [out] Počet znaků, které jsou ve skutečnosti zapsána do `szCulture` vyrovnávací paměti.  
  
 `szCulture`  
 [out] Pole znaků, který obsahuje název jazykové verze.  
  
## <a name="remarks"></a>Poznámky  
 Název jazykové verze je jedinečný řetězec, který určuje jazykovou verzi, jako je například "en US" (pro jazykovou verzi Czech (Czech Republic)), nebo "neutrální" (pro neutrální jazykovou verzi).  
  
> [!NOTE]
>  Tato metoda je k dispozici s .NET Native jenom.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugMergedAssemblyRecord – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
