---
title: "ICorDebugDataTarget2::EnumerateThreadIDs – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: af02460f-2a45-496e-bc4e-a1ac4f80fe11
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9030f7f8453de98f535cf8212e55c7daee94e8e1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdatatarget2enumeratethreadids-method"></a>ICorDebugDataTarget2::EnumerateThreadIDs – metoda
Vrátí seznam aktivních vláken ID.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumerateThreadIDs(  
    [in] ULONG32 cThreadIds,   
    [out] ULONG32 *pcThreadIds,   
    [out, size_is(cThreadIds), length_is(*pcThreadIds)] ULONG32 pThreadIds[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 cThreadIDs  
 [v] Maximální počet vláken, jehož ID se může vracet.  
  
 pcThreadIds  
 [out] Ukazatel `ULONG32` určující, skutečný počet vláken ID zapsána do `pThreadIds` pole.  
  
 pThreadIDs  
 Pole identifikátory přístup z více vláken.  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Tato metoda je k dispozici s .NET Native jenom.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md). **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugDataTarget2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
