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
ms.openlocfilehash: 9792abb4ee38a45aae59eaf79f1f0499539bd2ae
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791766"
---
# <a name="icordebugsteppersetinterceptmask-method"></a><span data-ttu-id="83e2e-102">ICorDebugStepper::SetInterceptMask – metoda</span><span class="sxs-lookup"><span data-stu-id="83e2e-102">ICorDebugStepper::SetInterceptMask Method</span></span>
<span data-ttu-id="83e2e-103">Nastaví hodnotu, která určuje typy kódu, na které se má vzstep.</span><span class="sxs-lookup"><span data-stu-id="83e2e-103">Sets a value that specifies the types of code that are stepped into.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83e2e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83e2e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetInterceptMask (  
    [in] CorDebugIntercept    mask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83e2e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="83e2e-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="83e2e-106">pro Kombinace hodnot výčtu CorDebugIntercept –, která určuje typy kódu.</span><span class="sxs-lookup"><span data-stu-id="83e2e-106">[in] A combination of values of the CorDebugIntercept enumeration that specifies the types of code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83e2e-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="83e2e-107">Remarks</span></span>  
 <span data-ttu-id="83e2e-108">Pokud je nastaven bit pro zachytávací modul, stepper se dokončí při zjištění daného typu zachycení kódu.</span><span class="sxs-lookup"><span data-stu-id="83e2e-108">If the bit for an interceptor is set, the stepper will complete when the given type of intercepting code is encountered.</span></span> <span data-ttu-id="83e2e-109">Pokud je bit vymazán, kód zachycení se přeskočí.</span><span class="sxs-lookup"><span data-stu-id="83e2e-109">If the bit is cleared, the intercepting code will be skipped.</span></span>  
  
 <span data-ttu-id="83e2e-110">Metoda `SetInterceptMask` může mít nepředvídatelné interakce s [ICorDebugStepper:: SetUnmappedStopMask –](icordebugstepper-setunmappedstopmask-method.md) (z pohledu uživatele).</span><span class="sxs-lookup"><span data-stu-id="83e2e-110">The `SetInterceptMask` method may have unforeseen interactions with [ICorDebugStepper::SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) (from the user's point of view).</span></span> <span data-ttu-id="83e2e-111">Například pokud jedinou viditelnou část (která je neinterní) obsažená v inicializačním kódu třídy chybí informace o mapování a STOP_NO_MAPPING_INFO není nastavena (viz metoda [ICorDebugStepper:: SetUnmappedStopMask –](icordebugstepper-setunmappedstopmask-method.md) a výčet CorDebugUnmappedStop –), stepper bude Krokovat s inicializací třídy.</span><span class="sxs-lookup"><span data-stu-id="83e2e-111">For example, if the only visible (that is, non-internal) portion of class initialization code lacks mapping information and STOP_NO_MAPPING_INFO isn't set (see the [ICorDebugStepper::SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) method and the CorDebugUnmappedStop enumeration), the stepper will step over the class initialization.</span></span> <span data-ttu-id="83e2e-112">Ve výchozím nastavení se použije jenom hodnota INTERCEPT_NONE výčtu `CorDebugIntercept`.</span><span class="sxs-lookup"><span data-stu-id="83e2e-112">By default, only the INTERCEPT_NONE value of the `CorDebugIntercept` enumeration will be used.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83e2e-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="83e2e-113">Requirements</span></span>  
 <span data-ttu-id="83e2e-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83e2e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83e2e-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="83e2e-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="83e2e-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="83e2e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83e2e-117">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83e2e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
