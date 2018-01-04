---
title: "ICorDebugGCReferenceEnum::Next – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugGCReferenceEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugGCReferenceEnum::Next
helpviewer_keywords:
- Next method, ICorDebugGCReferenceEnum interface [.NET Framework debugging]
- ICorDebugGCReferenceEnum::Next method [.NET Framework debugging]
ms.assetid: 91b1345c-a94f-4ef8-9696-3823d06c6d05
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e61edea76b4e3be8a03000899b72d486163ceaf6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuggcreferenceenumnext-method"></a>ICorDebugGCReferenceEnum::Next – metoda
Získá zadaný počet [cor_gc_reference –](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instancí, které obsahují informace o objektech, které budou uvolňování paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_GC_REFERENCE roots[],   
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 celt  
 [v] Počet kořeny mají být načteny.  
  
 kořeny  
 [out] Ukazatele, každý z nich odkazuje na pole [cor_gc_reference –](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objekt, který reprezentuje kořen objekt tak, aby se uvolňování paměti.  
  
 pceltFetched  
 [out] Ukazatel na počet [cor_gc_reference –](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objekty ve skutečnosti, vrátí se v `roots`. Tato hodnota může být `null` Pokud `celt` je 1.  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugGCReferenceEnum – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
