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
ms.openlocfilehash: 5dd93dcc29ace6573e313f732c45af0dfbb900e1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782216"
---
# <a name="icordebuginternalframe2isclosertoleaf-method"></a><span data-ttu-id="081f3-102">ICorDebugInternalFrame2::IsCloserToLeaf – metoda</span><span class="sxs-lookup"><span data-stu-id="081f3-102">ICorDebugInternalFrame2::IsCloserToLeaf Method</span></span>
<span data-ttu-id="081f3-103">Kontroluje, zda je vnitřní rámec `this` blíž k listu, než je zadaný objekt ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="081f3-103">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="081f3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="081f3-104">Syntax</span></span>  
  
```cpp  
HRESULT IsCloserToLeaf([in] ICorDebugFrame * pFrameToCompare,  
                       [out] BOOL * pIsCloser);  
```  
  
## <a name="parameters"></a><span data-ttu-id="081f3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="081f3-105">Parameters</span></span>  
 `pFrameToCompare`  
 <span data-ttu-id="081f3-106">pro Ukazatel na objekt porovnání `ICorDebugFrame`.</span><span class="sxs-lookup"><span data-stu-id="081f3-106">[in] A pointer to the comparison `ICorDebugFrame` object.</span></span>  
  
 `pIsCloser`  
 <span data-ttu-id="081f3-107">[out] `true`, zda `this` interní rámec je blíž k listu, než je rámec určený `pFrameToCompare`; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="081f3-107">[out] `true` if the `this` internal frame is closer to the leaf than the frame specified by `pFrameToCompare`; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="081f3-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="081f3-108">Return Value</span></span>  
 <span data-ttu-id="081f3-109">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="081f3-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="081f3-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="081f3-110">HRESULT</span></span>|<span data-ttu-id="081f3-111">Popis</span><span class="sxs-lookup"><span data-stu-id="081f3-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="081f3-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="081f3-112">S_OK</span></span>|<span data-ttu-id="081f3-113">Porovnání bylo úspěšně provedeno.</span><span class="sxs-lookup"><span data-stu-id="081f3-113">The comparison was successfully performed.</span></span>|  
|<span data-ttu-id="081f3-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="081f3-114">E_FAIL</span></span>|<span data-ttu-id="081f3-115">Porovnání nelze provést.</span><span class="sxs-lookup"><span data-stu-id="081f3-115">The comparison could not be performed.</span></span>|  
|<span data-ttu-id="081f3-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="081f3-116">E_INVALIDARG</span></span>|<span data-ttu-id="081f3-117">`pFrameToCompare` nebo `pIsCloser` je null.</span><span class="sxs-lookup"><span data-stu-id="081f3-117">`pFrameToCompare` or `pIsCloser` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="081f3-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="081f3-118">Remarks</span></span>  
 <span data-ttu-id="081f3-119">`IsCloserToLeaf` lze použít k implementaci zásad pro překládání vnitřních snímků s ostatními snímky v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="081f3-119">`IsCloserToLeaf` can be used to implement a policy for interleaving internal frames with other frames on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="081f3-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="081f3-120">Requirements</span></span>  
 <span data-ttu-id="081f3-121">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="081f3-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="081f3-122">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="081f3-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="081f3-123">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="081f3-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="081f3-124">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="081f3-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="081f3-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="081f3-125">See also</span></span>

- [<span data-ttu-id="081f3-126">ICorDebugInternalFrame2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="081f3-126">ICorDebugInternalFrame2 Interface</span></span>](icordebuginternalframe2-interface.md)
- [<span data-ttu-id="081f3-127">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="081f3-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="081f3-128">Ladění</span><span class="sxs-lookup"><span data-stu-id="081f3-128">Debugging</span></span>](index.md)
