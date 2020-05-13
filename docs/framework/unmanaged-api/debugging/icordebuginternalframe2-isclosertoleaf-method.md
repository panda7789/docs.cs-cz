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
ms.openlocfilehash: 4a01ccd4e5cb9aadc6a693b2c6ceaff31c114bbc
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209887"
---
# <a name="icordebuginternalframe2isclosertoleaf-method"></a><span data-ttu-id="72a3b-102">ICorDebugInternalFrame2::IsCloserToLeaf – metoda</span><span class="sxs-lookup"><span data-stu-id="72a3b-102">ICorDebugInternalFrame2::IsCloserToLeaf Method</span></span>
<span data-ttu-id="72a3b-103">Kontroluje, zda `this` je interní rámec blíže k listu, než je zadaný objekt ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="72a3b-103">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72a3b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="72a3b-104">Syntax</span></span>  
  
```cpp  
HRESULT IsCloserToLeaf([in] ICorDebugFrame * pFrameToCompare,  
                       [out] BOOL * pIsCloser);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72a3b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="72a3b-105">Parameters</span></span>  
 `pFrameToCompare`  
 <span data-ttu-id="72a3b-106">pro Ukazatel na `ICorDebugFrame` objekt porovnání.</span><span class="sxs-lookup"><span data-stu-id="72a3b-106">[in] A pointer to the comparison `ICorDebugFrame` object.</span></span>  
  
 `pIsCloser`  
 <span data-ttu-id="72a3b-107">[out] `true` Pokud `this` interní rámec je blíž k listu, než je rámec určený v `pFrameToCompare` ; v opačném případě `false` .</span><span class="sxs-lookup"><span data-stu-id="72a3b-107">[out] `true` if the `this` internal frame is closer to the leaf than the frame specified by `pFrameToCompare`; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="72a3b-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="72a3b-108">Return Value</span></span>  
 <span data-ttu-id="72a3b-109">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="72a3b-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="72a3b-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="72a3b-110">HRESULT</span></span>|<span data-ttu-id="72a3b-111">Popis</span><span class="sxs-lookup"><span data-stu-id="72a3b-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="72a3b-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="72a3b-112">S_OK</span></span>|<span data-ttu-id="72a3b-113">Porovnání bylo úspěšně provedeno.</span><span class="sxs-lookup"><span data-stu-id="72a3b-113">The comparison was successfully performed.</span></span>|  
|<span data-ttu-id="72a3b-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="72a3b-114">E_FAIL</span></span>|<span data-ttu-id="72a3b-115">Porovnání nelze provést.</span><span class="sxs-lookup"><span data-stu-id="72a3b-115">The comparison could not be performed.</span></span>|  
|<span data-ttu-id="72a3b-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="72a3b-116">E_INVALIDARG</span></span>|<span data-ttu-id="72a3b-117">`pFrameToCompare`nebo `pIsCloser` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="72a3b-117">`pFrameToCompare` or `pIsCloser` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72a3b-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="72a3b-118">Remarks</span></span>  
 <span data-ttu-id="72a3b-119">`IsCloserToLeaf`dá se použít k implementaci zásady pro překládání vnitřních snímků s ostatními snímky v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="72a3b-119">`IsCloserToLeaf` can be used to implement a policy for interleaving internal frames with other frames on the stack.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72a3b-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="72a3b-120">Requirements</span></span>  
 <span data-ttu-id="72a3b-121">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72a3b-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72a3b-122">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="72a3b-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="72a3b-123">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="72a3b-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="72a3b-124">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72a3b-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72a3b-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="72a3b-125">See also</span></span>

- [<span data-ttu-id="72a3b-126">ICorDebugInternalFrame2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="72a3b-126">ICorDebugInternalFrame2 Interface</span></span>](icordebuginternalframe2-interface.md)
- [<span data-ttu-id="72a3b-127">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="72a3b-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="72a3b-128">Ladění</span><span class="sxs-lookup"><span data-stu-id="72a3b-128">Debugging</span></span>](index.md)
