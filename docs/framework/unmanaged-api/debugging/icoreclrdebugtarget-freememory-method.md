---
title: "ICoreClrDebugTarget::FreeMemory – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICoreDebugTarget.FreeMemory
api_location: mscordbi_macx86.dll
api_type: COM
f1_keywords: ICoreClrDebugTarget::FreeMemory
helpviewer_keywords:
- remote debugging API [Silverlight]
- FreeMemory method, ICoreClrDebugTarget interface [Silverlight debugging]
- ICorClrDebugTarget::FreeMemory method [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: 98f2a0db-a6ec-4f9b-861d-f82485237d08
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2079d0363e962d0423623c7c0261cc64fc4b3237
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icoreclrdebugtargetfreememory-method"></a>ICoreClrDebugTarget::FreeMemory – metoda
Uvolní paměti přidělené [icoreclrdebugtarget::enumprocesses –](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md) a [icoreclrdebugtarget::enumruntimes –](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md) metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void FreeMemory (  
     [in] void*pMemory);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pMemory`  
 [v] Ukazatel na pole, které se vrátí, a to buď [icoreclrdebugtarget::enumprocesses –](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md) nebo [icoreclrdebugtarget::enumruntimes –](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md) metoda.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CoreClrRemoteDebuggingInterfaces.h  
  
 **Knihovna:** mscordbi_macx86.dll  
  
 **Verze rozhraní .NET framework:** 3.5 SP1  
  
## <a name="see-also"></a>Viz také  
 [ICoreClrDebugTarget – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)
