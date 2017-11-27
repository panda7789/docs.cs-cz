---
title: "ICorDebugStepper::SetInterceptMask – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.SetInterceptMask
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::SetInterceptMask
helpviewer_keywords:
- SetInterceptMask method [.NET Framework debugging]
- ICorDebugStepper::SetInterceptMask method [.NET Framework debugging]
ms.assetid: 6245e2ae-5cc2-43ff-8cc1-71953d12113a
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2a99b504c0ce58ca6b89153667598cd4c2c682d9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugsteppersetinterceptmask-method"></a><span data-ttu-id="ad1a6-102">ICorDebugStepper::SetInterceptMask – metoda</span><span class="sxs-lookup"><span data-stu-id="ad1a6-102">ICorDebugStepper::SetInterceptMask Method</span></span>
<span data-ttu-id="ad1a6-103">Nastaví hodnotu, která určuje typy kód, který se stupeň do.</span><span class="sxs-lookup"><span data-stu-id="ad1a6-103">Sets a value that specifies the types of code that are stepped into.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad1a6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad1a6-104">Syntax</span></span>  
  
```  
HRESULT SetInterceptMask (  
    [in] CorDebugIntercept    mask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ad1a6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ad1a6-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="ad1a6-106">[v] Kombinace hodnot CorDebugIntercept – výčet, který určuje typy kódu.</span><span class="sxs-lookup"><span data-stu-id="ad1a6-106">[in] A combination of values of the CorDebugIntercept enumeration that specifies the types of code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad1a6-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ad1a6-107">Remarks</span></span>  
 <span data-ttu-id="ad1a6-108">Pokud je nastaven bit pro interceptoru, krokovače dokončí, když je došlo k danému typu brání kódu.</span><span class="sxs-lookup"><span data-stu-id="ad1a6-108">If the bit for an interceptor is set, the stepper will complete when the given type of intercepting code is encountered.</span></span> <span data-ttu-id="ad1a6-109">Pokud je bit není zaškrtnuto, bude přeskočen intercepting kódu.</span><span class="sxs-lookup"><span data-stu-id="ad1a6-109">If the bit is cleared, the intercepting code will be skipped.</span></span>  
  
 <span data-ttu-id="ad1a6-110">`SetInterceptMask` Metoda může mít nepředpokládaného interakce s [icordebugstepper::setunmappedstopmask –](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) (z uživatele hlediska).</span><span class="sxs-lookup"><span data-stu-id="ad1a6-110">The `SetInterceptMask` method may have unforeseen interactions with [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) (from the user's point of view).</span></span> <span data-ttu-id="ad1a6-111">Například pokud jenom viditelné (to znamená,-vnitřní) část kód inicializace třídy chybí informace o mapování a STOP_NO_MAPPING_INFO není nastavený (najdete v článku [icordebugstepper::setunmappedstopmask –](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) metoda a CorDebugUnmappedStop – výčet), bude krokovače krok přes inicializaci třídy.</span><span class="sxs-lookup"><span data-stu-id="ad1a6-111">For example, if the only visible (that is, non-internal) portion of class initialization code lacks mapping information and STOP_NO_MAPPING_INFO isn't set (see the [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) method and the CorDebugUnmappedStop enumeration), the stepper will step over the class initialization.</span></span> <span data-ttu-id="ad1a6-112">Ve výchozím nastavení pouze INTERCEPT_NONE hodnotu `CorDebugIntercept` se použije výčet.</span><span class="sxs-lookup"><span data-stu-id="ad1a6-112">By default, only the INTERCEPT_NONE value of the `CorDebugIntercept` enumeration will be used.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad1a6-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ad1a6-113">Requirements</span></span>  
 <span data-ttu-id="ad1a6-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad1a6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad1a6-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ad1a6-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ad1a6-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad1a6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad1a6-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad1a6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
