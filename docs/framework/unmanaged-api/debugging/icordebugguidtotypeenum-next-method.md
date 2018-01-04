---
title: "ICorDebugGuidToTypeEnum::Next – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugGuidToTypeEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugGuidToTypeEnum::Next
helpviewer_keywords:
- ICorDebugGuidToTypeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: c9937666-8e18-484d-9fe0-b9ac95199530
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3bcfbcfb85fc5eb1d58142af4e7d825162e9861b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugguidtotypeenumnext-method"></a>ICorDebugGuidToTypeEnum::Next – metoda
Získá zadaný počet [cordebugguidtotypemapping –](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instancí, které mapují identifikátory GUID na typ informace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched] CorDebugGuidToTypeMapping values[  ],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `celt`  
 [v] Počet objektů mapování typu GUID mají být načteny.  
  
 `values`  
 [out] Ukazatele, každý z nich odkazuje na pole [cordebugguidtotypemapping –](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objekt, který se mapuje [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID do její odpovídající ICorDebugType objektu.  
  
 `pceltFetched`  
 [out] Ukazatel na počet [cordebugguidtotypemapping –](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objekty ve skutečnosti, vrátí se v `values`.  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:**[!INCLUDE[wrt](../../../../includes/wrt-md.md)]  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugGuidToTypeEnum – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
