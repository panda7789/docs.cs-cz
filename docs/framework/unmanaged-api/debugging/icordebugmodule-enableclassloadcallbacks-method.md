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
ms.openlocfilehash: 8dcf814311821218c0dfd8fdcbb91afd3973f2b4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57482467"
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a><span data-ttu-id="ee7e9-102">ICorDebugModule::EnableClassLoadCallbacks – metoda</span><span class="sxs-lookup"><span data-stu-id="ee7e9-102">ICorDebugModule::EnableClassLoadCallbacks Method</span></span>
<span data-ttu-id="ee7e9-103">Ovládací prvky, zda [icordebugmanagedcallback::loadclass –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) a [icordebugmanagedcallback::unloadclass –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) zpětná volání jsou volány pro tento modul.</span><span class="sxs-lookup"><span data-stu-id="ee7e9-103">Controls whether the [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee7e9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ee7e9-104">Syntax</span></span>  
  
```  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ee7e9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ee7e9-105">Parameters</span></span>  
 `bClassLoadCallbacks`  
 <span data-ttu-id="ee7e9-106">[in] Nastavte tuto hodnotu na `true` povolit modul CLR (CLR) k volání `ICorDebugManagedCallback::LoadClass` a `ICorDebugManagedCallback::UnloadClass` metody, pokud dojde k jejich související události.</span><span class="sxs-lookup"><span data-stu-id="ee7e9-106">[in] Set this value to `true` to enable the common language runtime (CLR) to call the `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` methods when their associated events occur.</span></span>  
  
 <span data-ttu-id="ee7e9-107">Výchozí hodnota je `false` nedynamickou modulů.</span><span class="sxs-lookup"><span data-stu-id="ee7e9-107">The default value is `false` for non-dynamic modules.</span></span> <span data-ttu-id="ee7e9-108">Hodnota je vždy `true` pro dynamické moduly a nedá se změnit.</span><span class="sxs-lookup"><span data-stu-id="ee7e9-108">The value is always `true` for dynamic modules and cannot be changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ee7e9-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ee7e9-109">Remarks</span></span>  
 <span data-ttu-id="ee7e9-110">`ICorDebugManagedCallback::LoadClass` a `ICorDebugManagedCallback::UnloadClass` zpětná volání jsou vždy povoleny pro dynamické moduly a nedá se zakázat.</span><span class="sxs-lookup"><span data-stu-id="ee7e9-110">The `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` callbacks are always enabled for dynamic modules and cannot be disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee7e9-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ee7e9-111">Requirements</span></span>  
 <span data-ttu-id="ee7e9-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee7e9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee7e9-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ee7e9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ee7e9-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ee7e9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee7e9-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee7e9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee7e9-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ee7e9-116">See also</span></span>


