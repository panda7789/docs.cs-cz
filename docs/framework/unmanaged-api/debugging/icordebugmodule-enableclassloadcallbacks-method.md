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
ms.openlocfilehash: 1ca3adf30ad633fcfb10a4b43a435698d2899597
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213527"
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a><span data-ttu-id="ce815-102">ICorDebugModule::EnableClassLoadCallbacks – metoda</span><span class="sxs-lookup"><span data-stu-id="ce815-102">ICorDebugModule::EnableClassLoadCallbacks Method</span></span>
<span data-ttu-id="ce815-103">Určuje, zda jsou pro tento modul volána zpětná volání [ICorDebugManagedCallback:: LoadClass –](icordebugmanagedcallback-loadclass-method.md) a [ICorDebugManagedCallback:: UnloadClass –](icordebugmanagedcallback-unloadclass-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ce815-103">Controls whether the [ICorDebugManagedCallback::LoadClass](icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce815-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ce815-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce815-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce815-105">Parameters</span></span>  
 `bClassLoadCallbacks`  
 <span data-ttu-id="ce815-106">pro Nastavte tuto hodnotu, chcete-li `true` Povolit modulu CLR (Common Language Runtime) volat `ICorDebugManagedCallback::LoadClass` metody a, `ICorDebugManagedCallback::UnloadClass` když dojde k jejich přidruženým událostem.</span><span class="sxs-lookup"><span data-stu-id="ce815-106">[in] Set this value to `true` to enable the common language runtime (CLR) to call the `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` methods when their associated events occur.</span></span>  
  
 <span data-ttu-id="ce815-107">Výchozí hodnota je `false` pro jiné než dynamické moduly.</span><span class="sxs-lookup"><span data-stu-id="ce815-107">The default value is `false` for non-dynamic modules.</span></span> <span data-ttu-id="ce815-108">Hodnota je vždy `true` pro dynamické moduly a nelze ji změnit.</span><span class="sxs-lookup"><span data-stu-id="ce815-108">The value is always `true` for dynamic modules and cannot be changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce815-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ce815-109">Remarks</span></span>  
 <span data-ttu-id="ce815-110">`ICorDebugManagedCallback::LoadClass` `ICorDebugManagedCallback::UnloadClass` Zpětná volání a jsou vždy povolena pro dynamické moduly a nelze je zakázat.</span><span class="sxs-lookup"><span data-stu-id="ce815-110">The `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` callbacks are always enabled for dynamic modules and cannot be disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce815-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ce815-111">Requirements</span></span>  
 <span data-ttu-id="ce815-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce815-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce815-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ce815-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ce815-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ce815-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce815-115">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce815-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce815-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="ce815-116">See also</span></span>
