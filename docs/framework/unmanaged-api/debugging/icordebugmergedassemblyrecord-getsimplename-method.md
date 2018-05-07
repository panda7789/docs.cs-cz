---
title: ICorDebugMergedAssemblyRecord::GetSimpleName – metoda
ms.date: 03/30/2017
ms.assetid: bc3410f6-ebca-4bca-9b45-fc38c74fa9cb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b8c5499b63e5201fbf42ece07f4f3eff52129e09
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmergedassemblyrecordgetsimplename-method"></a>ICorDebugMergedAssemblyRecord::GetSimpleName – metoda
Získá jednoduchý název sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetSimpleName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cchName`  
 [v] Počet znaků `szName` vyrovnávací paměti.  
  
 `pcchName`  
 [out] Ukazatel na počet znaků, které jsou ve skutečnosti zapsána do `szName` vyrovnávací paměti.  
  
 `szName`  
 Ukazatel na pole znaků.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda načte jednoduchý název sestavení (například "System.Collections"), bez přípony, verze, jazykové verze nebo tokenu veřejného klíče. Odpovídá <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> vlastnost ve spravovaném kódu.  
  
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
