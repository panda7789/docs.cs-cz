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
ms.openlocfilehash: c0e72d15ab4ca9b4468efb2a671022f30bfb3cc6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759944"
---
# <a name="icordebuginternalframe2isclosertoleaf-method"></a><span data-ttu-id="2e336-102">ICorDebugInternalFrame2::IsCloserToLeaf – metoda</span><span class="sxs-lookup"><span data-stu-id="2e336-102">ICorDebugInternalFrame2::IsCloserToLeaf Method</span></span>
<span data-ttu-id="2e336-103">Kontroluje, zda `this` vnitřní rámec je blíže než zadaný objekt ICorDebugFrame listu.</span><span class="sxs-lookup"><span data-stu-id="2e336-103">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e336-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e336-104">Syntax</span></span>  
  
```cpp  
HRESULT IsCloserToLeaf([in] ICorDebugFrame * pFrameToCompare,  
                       [out] BOOL * pIsCloser);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e336-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2e336-105">Parameters</span></span>  
 `pFrameToCompare`  
 <span data-ttu-id="2e336-106">[in] Ukazatel na porovnání `ICorDebugFrame` objektu.</span><span class="sxs-lookup"><span data-stu-id="2e336-106">[in] A pointer to the comparison `ICorDebugFrame` object.</span></span>  
  
 `pIsCloser`  
 <span data-ttu-id="2e336-107">[out] `true` Pokud `this` vnitřní rámec je blíž ke listu než rámce určené `pFrameToCompare`; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="2e336-107">[out] `true` if the `this` internal frame is closer to the leaf than the frame specified by `pFrameToCompare`; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2e336-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2e336-108">Return Value</span></span>  
 <span data-ttu-id="2e336-109">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="2e336-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="2e336-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2e336-110">HRESULT</span></span>|<span data-ttu-id="2e336-111">Popis</span><span class="sxs-lookup"><span data-stu-id="2e336-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2e336-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="2e336-112">S_OK</span></span>|<span data-ttu-id="2e336-113">Porovnání se úspěšně provedla.</span><span class="sxs-lookup"><span data-stu-id="2e336-113">The comparison was successfully performed.</span></span>|  
|<span data-ttu-id="2e336-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2e336-114">E_FAIL</span></span>|<span data-ttu-id="2e336-115">Porovnání nelze provést.</span><span class="sxs-lookup"><span data-stu-id="2e336-115">The comparison could not be performed.</span></span>|  
|<span data-ttu-id="2e336-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="2e336-116">E_INVALIDARG</span></span>|<span data-ttu-id="2e336-117">`pFrameToCompare` nebo `pIsCloser` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="2e336-117">`pFrameToCompare` or `pIsCloser` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2e336-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2e336-118">Remarks</span></span>  
 <span data-ttu-id="2e336-119">`IsCloserToLeaf` je možné implementovat zásady pro prokládání vnitřních rámcích pomocí jiné rámce v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="2e336-119">`IsCloserToLeaf` can be used to implement a policy for interleaving internal frames with other frames on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e336-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2e336-120">Requirements</span></span>  
 <span data-ttu-id="2e336-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e336-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e336-122">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2e336-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2e336-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2e336-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e336-124">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e336-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e336-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2e336-125">See also</span></span>

- [<span data-ttu-id="2e336-126">ICorDebugInternalFrame2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e336-126">ICorDebugInternalFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)
- [<span data-ttu-id="2e336-127">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="2e336-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="2e336-128">Ladění</span><span class="sxs-lookup"><span data-stu-id="2e336-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
