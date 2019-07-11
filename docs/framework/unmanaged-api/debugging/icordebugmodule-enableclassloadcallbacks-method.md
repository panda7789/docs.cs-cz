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
ms.openlocfilehash: ec9b4867ad19f25e35ca31c007c0d238b949abab
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762221"
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a><span data-ttu-id="71c27-102">ICorDebugModule::EnableClassLoadCallbacks – metoda</span><span class="sxs-lookup"><span data-stu-id="71c27-102">ICorDebugModule::EnableClassLoadCallbacks Method</span></span>
<span data-ttu-id="71c27-103">Ovládací prvky, zda [icordebugmanagedcallback::loadclass –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) a [icordebugmanagedcallback::unloadclass –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) zpětná volání jsou volány pro tento modul.</span><span class="sxs-lookup"><span data-stu-id="71c27-103">Controls whether the [ICorDebugManagedCallback::LoadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71c27-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="71c27-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="71c27-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="71c27-105">Parameters</span></span>  
 `bClassLoadCallbacks`  
 <span data-ttu-id="71c27-106">[in] Nastavte tuto hodnotu na `true` povolit modul CLR (CLR) k volání `ICorDebugManagedCallback::LoadClass` a `ICorDebugManagedCallback::UnloadClass` metody, pokud dojde k jejich související události.</span><span class="sxs-lookup"><span data-stu-id="71c27-106">[in] Set this value to `true` to enable the common language runtime (CLR) to call the `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` methods when their associated events occur.</span></span>  
  
 <span data-ttu-id="71c27-107">Výchozí hodnota je `false` nedynamickou modulů.</span><span class="sxs-lookup"><span data-stu-id="71c27-107">The default value is `false` for non-dynamic modules.</span></span> <span data-ttu-id="71c27-108">Hodnota je vždy `true` pro dynamické moduly a nedá se změnit.</span><span class="sxs-lookup"><span data-stu-id="71c27-108">The value is always `true` for dynamic modules and cannot be changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="71c27-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="71c27-109">Remarks</span></span>  
 <span data-ttu-id="71c27-110">`ICorDebugManagedCallback::LoadClass` a `ICorDebugManagedCallback::UnloadClass` zpětná volání jsou vždy povoleny pro dynamické moduly a nedá se zakázat.</span><span class="sxs-lookup"><span data-stu-id="71c27-110">The `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` callbacks are always enabled for dynamic modules and cannot be disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71c27-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="71c27-111">Requirements</span></span>  
 <span data-ttu-id="71c27-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71c27-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71c27-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="71c27-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="71c27-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="71c27-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="71c27-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71c27-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71c27-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="71c27-116">See also</span></span>
