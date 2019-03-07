---
title: ICorDebugMergedAssemblyRecord::GetSimpleName – metoda
ms.date: 03/30/2017
ms.assetid: bc3410f6-ebca-4bca-9b45-fc38c74fa9cb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0914c09fbbef5efb64fb253a4ea36d5b6c97ba97
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479100"
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
  
## <a name="parameters"></a>Parametry  
 `cchName`  
 [in] Počet znaků `szName` vyrovnávací paměti.  
  
 `pcchName`  
 [out] Ukazatel na počet aktuálně zapsaných do znaků `szName` vyrovnávací paměti.  
  
 `szName`  
 Ukazatel na pole znaků.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda načte jednoduchý název sestavení (například "System.Collections"), bez příponu souboru, verze, jazykovou verzi a token veřejného klíče. Odpovídá <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> vlastnost ve spravovaném kódu.  
  
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
