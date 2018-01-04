---
title: "ICorDebugMergedAssemblyRecord::GetIndex – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 98701444-b9bc-4978-9548-89ac3394147d
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 54ff8d6935f5507ab02d9d566921cb7f8a890bb0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmergedassemblyrecordgetindex-method"></a>ICorDebugMergedAssemblyRecord::GetIndex – metoda
Získá index předpona je sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetIndex(  
   [out] ULONG32 *pIndex  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pIndex`  
 [out] Ukazatel na index předponu.  
  
## <a name="remarks"></a>Poznámky  
 Index předpona se používá při prevenci kolize názvů v názvy typů sloučené metadat.  
  
> [!NOTE]
>  Tato metoda je k dispozici s .NET Native jenom.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugMergedAssemblyRecord – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
