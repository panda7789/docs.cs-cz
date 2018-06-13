---
title: ICorDebugInternalFrame2::IsCloserToLeaf – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame2.IsCloserToLeaf Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame2::IsCloserToLeaf
helpviewer_keywords:
- ICorDebugInternalFrame2::IsCloserToLeaf method [.NET Framework debugging]
- IsCloserToLeaf method [.NET Framework debugging]
ms.assetid: c1d3d1eb-8370-4f25-8297-3bd262b4740a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6d26d4dc046841a891c8a36530bd579d100b8f5b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416121"
---
# <a name="icordebuginternalframe2isclosertoleaf-method"></a><span data-ttu-id="70f0e-102">ICorDebugInternalFrame2::IsCloserToLeaf – metoda</span><span class="sxs-lookup"><span data-stu-id="70f0e-102">ICorDebugInternalFrame2::IsCloserToLeaf Method</span></span>
<span data-ttu-id="70f0e-103">Kontroluje, zda `this` interní rámečku je blíž ke listu než zadaný objekt ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="70f0e-103">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70f0e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70f0e-104">Syntax</span></span>  
  
```  
HRESULT IsCloserToLeaf([in] ICorDebugFrame * pFrameToCompare,  
                       [out] BOOL * pIsCloser);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="70f0e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="70f0e-105">Parameters</span></span>  
 `pFrameToCompare`  
 <span data-ttu-id="70f0e-106">[v] Ukazatel na porovnání `ICorDebugFrame` objektu.</span><span class="sxs-lookup"><span data-stu-id="70f0e-106">[in] A pointer to the comparison `ICorDebugFrame` object.</span></span>  
  
 `pIsCloser`  
 <span data-ttu-id="70f0e-107">[out] `true` Pokud `this` interní rámečku je blíž ke listu než rámečku určeného `pFrameToCompare`, jinak hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="70f0e-107">[out] `true` if the `this` internal frame is closer to the leaf than the frame specified by `pFrameToCompare`; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="70f0e-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="70f0e-108">Return Value</span></span>  
 <span data-ttu-id="70f0e-109">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="70f0e-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="70f0e-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="70f0e-110">HRESULT</span></span>|<span data-ttu-id="70f0e-111">Popis</span><span class="sxs-lookup"><span data-stu-id="70f0e-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="70f0e-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="70f0e-112">S_OK</span></span>|<span data-ttu-id="70f0e-113">Porovnání se úspěšně provedla.</span><span class="sxs-lookup"><span data-stu-id="70f0e-113">The comparison was successfully performed.</span></span>|  
|<span data-ttu-id="70f0e-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="70f0e-114">E_FAIL</span></span>|<span data-ttu-id="70f0e-115">Nelze provést porovnání.</span><span class="sxs-lookup"><span data-stu-id="70f0e-115">The comparison could not be performed.</span></span>|  
|<span data-ttu-id="70f0e-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="70f0e-116">E_INVALIDARG</span></span>|<span data-ttu-id="70f0e-117">`pFrameToCompare` nebo `pIsCloser` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="70f0e-117">`pFrameToCompare` or `pIsCloser` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70f0e-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="70f0e-118">Remarks</span></span>  
 <span data-ttu-id="70f0e-119">`IsCloserToLeaf` slouží k implementaci zásad pro prokládání interní rámce s jiné rámce v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="70f0e-119">`IsCloserToLeaf` can be used to implement a policy for interleaving internal frames with other frames on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70f0e-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="70f0e-120">Requirements</span></span>  
 <span data-ttu-id="70f0e-121">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70f0e-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70f0e-122">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="70f0e-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="70f0e-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="70f0e-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="70f0e-124">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70f0e-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70f0e-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="70f0e-125">See Also</span></span>  
 [<span data-ttu-id="70f0e-126">ICorDebugInternalFrame2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="70f0e-126">ICorDebugInternalFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)  
 [<span data-ttu-id="70f0e-127">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="70f0e-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="70f0e-128">Ladění</span><span class="sxs-lookup"><span data-stu-id="70f0e-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
