---
title: "ICorDebugModule::EnableClassLoadCallbacks – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.EnableClassLoadCallbacks
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::EnableClassLoadCallbacks
helpviewer_keywords:
- ICorDebugModule::EnableClassLoadCallbacks method [.NET Framework debugging]
- EnableClassLoadCallbacks method [.NET Framework debugging]
ms.assetid: 78dad5e4-8e2e-400f-bec3-92ff0205cd82
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5aa4add6dcaf662f1b5ec48b1243f012a6ae1f1c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a><span data-ttu-id="3bab7-102">ICorDebugModule::EnableClassLoadCallbacks – metoda</span><span class="sxs-lookup"><span data-stu-id="3bab7-102">ICorDebugModule::EnableClassLoadCallbacks Method</span></span>
<span data-ttu-id="3bab7-103">Ovládací prvky jestli [icordebugmanagedcallback::loadclass –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) a [icordebugmanagedcallback::unloadclass –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) pro tento modul se nazývají zpětných volání.</span><span class="sxs-lookup"><span data-stu-id="3bab7-103">Controls whether the [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bab7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3bab7-104">Syntax</span></span>  
  
```  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3bab7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3bab7-105">Parameters</span></span>  
 `bClassLoadCallbacks`  
 <span data-ttu-id="3bab7-106">[v] Nastavte tuto hodnotu na `true` povolit modul CLR (CLR) k volání `ICorDebugManagedCallback::LoadClass` a `ICorDebugManagedCallback::UnloadClass` metody, pokud dojde k jejich související události.</span><span class="sxs-lookup"><span data-stu-id="3bab7-106">[in] Set this value to `true` to enable the common language runtime (CLR) to call the `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` methods when their associated events occur.</span></span>  
  
 <span data-ttu-id="3bab7-107">Výchozí hodnota je `false` pro moduly bez dynamické.</span><span class="sxs-lookup"><span data-stu-id="3bab7-107">The default value is `false` for non-dynamic modules.</span></span> <span data-ttu-id="3bab7-108">Hodnota je vždy `true` pro dynamické moduly a nedá se změnit.</span><span class="sxs-lookup"><span data-stu-id="3bab7-108">The value is always `true` for dynamic modules and cannot be changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3bab7-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3bab7-109">Remarks</span></span>  
 <span data-ttu-id="3bab7-110">`ICorDebugManagedCallback::LoadClass` a `ICorDebugManagedCallback::UnloadClass` jsou vždy povolena pro dynamické moduly zpětná volání a nedá se zakázat.</span><span class="sxs-lookup"><span data-stu-id="3bab7-110">The `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` callbacks are always enabled for dynamic modules and cannot be disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3bab7-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3bab7-111">Requirements</span></span>  
 <span data-ttu-id="3bab7-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3bab7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3bab7-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3bab7-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3bab7-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3bab7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3bab7-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3bab7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bab7-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="3bab7-116">See Also</span></span>  
    
 
