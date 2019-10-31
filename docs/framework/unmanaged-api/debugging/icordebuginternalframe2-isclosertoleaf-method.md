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
ms.openlocfilehash: 8b9ec94184945c19b77247175e51bd5e8dc1ceee
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122667"
---
# <a name="icordebuginternalframe2isclosertoleaf-method"></a><span data-ttu-id="2d005-102">ICorDebugInternalFrame2::IsCloserToLeaf – metoda</span><span class="sxs-lookup"><span data-stu-id="2d005-102">ICorDebugInternalFrame2::IsCloserToLeaf Method</span></span>
<span data-ttu-id="2d005-103">Kontroluje, zda je vnitřní rámec `this` blíž k listu, než je zadaný objekt ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="2d005-103">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d005-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2d005-104">Syntax</span></span>  
  
```cpp  
HRESULT IsCloserToLeaf([in] ICorDebugFrame * pFrameToCompare,  
                       [out] BOOL * pIsCloser);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d005-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2d005-105">Parameters</span></span>  
 `pFrameToCompare`  
 <span data-ttu-id="2d005-106">pro Ukazatel na objekt porovnání `ICorDebugFrame`.</span><span class="sxs-lookup"><span data-stu-id="2d005-106">[in] A pointer to the comparison `ICorDebugFrame` object.</span></span>  
  
 `pIsCloser`  
 <span data-ttu-id="2d005-107">[out] `true`, zda `this` interní rámec je blíž k listu, než je rámec určený `pFrameToCompare`; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="2d005-107">[out] `true` if the `this` internal frame is closer to the leaf than the frame specified by `pFrameToCompare`; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2d005-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2d005-108">Return Value</span></span>  
 <span data-ttu-id="2d005-109">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="2d005-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="2d005-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2d005-110">HRESULT</span></span>|<span data-ttu-id="2d005-111">Popis</span><span class="sxs-lookup"><span data-stu-id="2d005-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2d005-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="2d005-112">S_OK</span></span>|<span data-ttu-id="2d005-113">Porovnání bylo úspěšně provedeno.</span><span class="sxs-lookup"><span data-stu-id="2d005-113">The comparison was successfully performed.</span></span>|  
|<span data-ttu-id="2d005-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2d005-114">E_FAIL</span></span>|<span data-ttu-id="2d005-115">Porovnání nelze provést.</span><span class="sxs-lookup"><span data-stu-id="2d005-115">The comparison could not be performed.</span></span>|  
|<span data-ttu-id="2d005-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="2d005-116">E_INVALIDARG</span></span>|<span data-ttu-id="2d005-117">`pFrameToCompare` nebo `pIsCloser` je null.</span><span class="sxs-lookup"><span data-stu-id="2d005-117">`pFrameToCompare` or `pIsCloser` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d005-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2d005-118">Remarks</span></span>  
 <span data-ttu-id="2d005-119">`IsCloserToLeaf` lze použít k implementaci zásad pro překládání vnitřních snímků s ostatními snímky v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="2d005-119">`IsCloserToLeaf` can be used to implement a policy for interleaving internal frames with other frames on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d005-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2d005-120">Requirements</span></span>  
 <span data-ttu-id="2d005-121">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d005-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d005-122">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2d005-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2d005-123">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2d005-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2d005-124">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d005-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d005-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d005-125">See also</span></span>

- [<span data-ttu-id="2d005-126">ICorDebugInternalFrame2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2d005-126">ICorDebugInternalFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)
- [<span data-ttu-id="2d005-127">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="2d005-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="2d005-128">Ladění</span><span class="sxs-lookup"><span data-stu-id="2d005-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
