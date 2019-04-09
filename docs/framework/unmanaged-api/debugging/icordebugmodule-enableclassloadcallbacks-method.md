---
title: ICorDebugModule::EnableClassLoadCallbacks – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule.EnableClassLoadCallbacks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::EnableClassLoadCallbacks
helpviewer_keywords:
- ICorDebugModule::EnableClassLoadCallbacks method [.NET Framework debugging]
- EnableClassLoadCallbacks method [.NET Framework debugging]
ms.assetid: 78dad5e4-8e2e-400f-bec3-92ff0205cd82
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 22a838748414f9d89cdc7ff469f7f5cc5e11b9d4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108300"
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a><span data-ttu-id="d5894-102">ICorDebugModule::EnableClassLoadCallbacks – metoda</span><span class="sxs-lookup"><span data-stu-id="d5894-102">ICorDebugModule::EnableClassLoadCallbacks Method</span></span>
<span data-ttu-id="d5894-103">Ovládací prvky, zda [icordebugmanagedcallback::loadclass –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) a [icordebugmanagedcallback::unloadclass –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) zpětná volání jsou volány pro tento modul.</span><span class="sxs-lookup"><span data-stu-id="d5894-103">Controls whether the [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5894-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5894-104">Syntax</span></span>  
  
```  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5894-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d5894-105">Parameters</span></span>  
 `bClassLoadCallbacks`  
 <span data-ttu-id="d5894-106">[in] Nastavte tuto hodnotu na `true` povolit modul CLR (CLR) k volání `ICorDebugManagedCallback::LoadClass` a `ICorDebugManagedCallback::UnloadClass` metody, pokud dojde k jejich související události.</span><span class="sxs-lookup"><span data-stu-id="d5894-106">[in] Set this value to `true` to enable the common language runtime (CLR) to call the `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` methods when their associated events occur.</span></span>  
  
 <span data-ttu-id="d5894-107">Výchozí hodnota je `false` nedynamickou modulů.</span><span class="sxs-lookup"><span data-stu-id="d5894-107">The default value is `false` for non-dynamic modules.</span></span> <span data-ttu-id="d5894-108">Hodnota je vždy `true` pro dynamické moduly a nedá se změnit.</span><span class="sxs-lookup"><span data-stu-id="d5894-108">The value is always `true` for dynamic modules and cannot be changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5894-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d5894-109">Remarks</span></span>  
 <span data-ttu-id="d5894-110">`ICorDebugManagedCallback::LoadClass` a `ICorDebugManagedCallback::UnloadClass` zpětná volání jsou vždy povoleny pro dynamické moduly a nedá se zakázat.</span><span class="sxs-lookup"><span data-stu-id="d5894-110">The `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` callbacks are always enabled for dynamic modules and cannot be disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5894-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d5894-111">Requirements</span></span>  
 <span data-ttu-id="d5894-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5894-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5894-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d5894-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d5894-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d5894-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="d5894-115">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="d5894-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d5894-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d5894-116">See also</span></span>
