---
title: ICorDebugStepper::SetInterceptMask – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetInterceptMask
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetInterceptMask
helpviewer_keywords:
- SetInterceptMask method [.NET Framework debugging]
- ICorDebugStepper::SetInterceptMask method [.NET Framework debugging]
ms.assetid: 6245e2ae-5cc2-43ff-8cc1-71953d12113a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25a9d287e6520f1fc7826d85dfbcd8e9a6da22f7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987633"
---
# <a name="icordebugsteppersetinterceptmask-method"></a><span data-ttu-id="83a82-102">ICorDebugStepper::SetInterceptMask – metoda</span><span class="sxs-lookup"><span data-stu-id="83a82-102">ICorDebugStepper::SetInterceptMask Method</span></span>
<span data-ttu-id="83a82-103">Nastaví hodnotu, která určuje typy kódu, které jsou vkročili.</span><span class="sxs-lookup"><span data-stu-id="83a82-103">Sets a value that specifies the types of code that are stepped into.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83a82-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83a82-104">Syntax</span></span>  
  
```  
HRESULT SetInterceptMask (  
    [in] CorDebugIntercept    mask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83a82-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="83a82-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="83a82-106">[in] Kombinace hodnot cordebugintercept – výčet, který určuje typy kódu.</span><span class="sxs-lookup"><span data-stu-id="83a82-106">[in] A combination of values of the CorDebugIntercept enumeration that specifies the types of code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83a82-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="83a82-107">Remarks</span></span>  
 <span data-ttu-id="83a82-108">Pokud je nastaven bit pro zachycování, krokovače dokončí, když dochází k danému typu zachycení kódu.</span><span class="sxs-lookup"><span data-stu-id="83a82-108">If the bit for an interceptor is set, the stepper will complete when the given type of intercepting code is encountered.</span></span> <span data-ttu-id="83a82-109">Pokud bit vymazán, prověřuje zachycovací kódu se přeskočí.</span><span class="sxs-lookup"><span data-stu-id="83a82-109">If the bit is cleared, the intercepting code will be skipped.</span></span>  
  
 <span data-ttu-id="83a82-110">`SetInterceptMask` Metoda může mít nepředvídatelné interakce s [icordebugstepper::setunmappedstopmask –](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) (od uživatele pohledu).</span><span class="sxs-lookup"><span data-stu-id="83a82-110">The `SetInterceptMask` method may have unforeseen interactions with [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) (from the user's point of view).</span></span> <span data-ttu-id="83a82-111">Například pokud viditelné jenom (to znamená, – vnitřní) část inicializační kód třídy chybí informace o mapování a není nastaven STOP_NO_MAPPING_INFO (naleznete v tématu [icordebugstepper::setunmappedstopmask –](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) metoda a Cordebugunmappedstop – výčet) krokovače přesune se krokování přes inicializace třídy.</span><span class="sxs-lookup"><span data-stu-id="83a82-111">For example, if the only visible (that is, non-internal) portion of class initialization code lacks mapping information and STOP_NO_MAPPING_INFO isn't set (see the [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) method and the CorDebugUnmappedStop enumeration), the stepper will step over the class initialization.</span></span> <span data-ttu-id="83a82-112">Ve výchozím nastavení pouze INTERCEPT_NONE hodnotu `CorDebugIntercept` se použije výčet.</span><span class="sxs-lookup"><span data-stu-id="83a82-112">By default, only the INTERCEPT_NONE value of the `CorDebugIntercept` enumeration will be used.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83a82-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="83a82-113">Requirements</span></span>  
 <span data-ttu-id="83a82-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83a82-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83a82-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="83a82-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="83a82-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83a82-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83a82-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83a82-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
