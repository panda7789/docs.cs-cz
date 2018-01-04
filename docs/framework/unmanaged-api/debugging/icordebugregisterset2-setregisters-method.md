---
title: "ICorDebugRegisterSet2::SetRegisters – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRegisterSet2.SetRegisters
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugRegisterSet2::SetRegisters
helpviewer_keywords:
- ICorDebugRegisterSet2::SetRegisters method [.NET Framework debugging]
- SetRegisters method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
ms.assetid: fe0ac7e7-c9e1-4ec1-9f4e-1c56d63d73ac
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ebf58c209834e4df8435d40616ef3a571a7c0a1b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugregisterset2setregisters-method"></a>ICorDebugRegisterSet2::SetRegisters – metoda
`SetRegisters`v rozhraní .NET Framework verze 2.0 není implementováno. Tato metoda není volána.  
  
> [!NOTE]
>  Pomocí operace vyšší úrovně, jako například [icordebugilframe::setip –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) nebo [icordebugnativeframe::setip –](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [in, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugRegisterSet2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)  
 [ICorDebugRegisterSet – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
