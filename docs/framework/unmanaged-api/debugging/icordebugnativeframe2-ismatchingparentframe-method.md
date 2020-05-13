---
title: ICorDebugNativeFrame2::IsMatchingParentFrame – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2.IsMatchingParentFrame Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2::IsMatchingParentFrame
helpviewer_keywords:
- IsMatchingParentFrame method [.NET Framework debugging]
- ICorDebugNativeFrame2::IsMatchingParentFrame method [.NET Framework debugging]
ms.assetid: d2ca20db-df22-4528-a0dd-a09ea62c8998
topic_type:
- apiref
ms.openlocfilehash: 5bcced647af6436bd8f5b1f3779d9368b6173d11
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213033"
---
# <a name="icordebugnativeframe2ismatchingparentframe-method"></a><span data-ttu-id="11d1b-102">ICorDebugNativeFrame2::IsMatchingParentFrame – metoda</span><span class="sxs-lookup"><span data-stu-id="11d1b-102">ICorDebugNativeFrame2::IsMatchingParentFrame Method</span></span>
<span data-ttu-id="11d1b-103">Určuje, zda je určený rámec nadřazeným prvkem aktuálního rámce.</span><span class="sxs-lookup"><span data-stu-id="11d1b-103">Determines whether the specified frame is the parent of the current frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11d1b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11d1b-104">Syntax</span></span>  
  
```cpp  
HRESULT IsMatchingParentFrame([in] ICorDebugNativeFrame2  
                                      *pPotentialParentFrame,  
                              [out] BOOL *pIsParent);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11d1b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="11d1b-105">Parameters</span></span>  
 `pPotentialParentFrame`  
 <span data-ttu-id="11d1b-106">pro Ukazatel na objekt rámce, který chcete vyhodnotit pro nadřazený stav.</span><span class="sxs-lookup"><span data-stu-id="11d1b-106">[in] A pointer to the frame object that you want to evaluate for parent status.</span></span>  
  
 `pIsParent`  
 <span data-ttu-id="11d1b-107">[out] `true` Pokud `pPotentialParentFrame` je nadřazená aktuální rámec, v opačném případě `false` .</span><span class="sxs-lookup"><span data-stu-id="11d1b-107">[out] `true` if `pPotentialParentFrame` is the current frame’s parent; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="11d1b-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="11d1b-108">Return Value</span></span>  
 <span data-ttu-id="11d1b-109">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="11d1b-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="11d1b-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="11d1b-110">HRESULT</span></span>|<span data-ttu-id="11d1b-111">Popis</span><span class="sxs-lookup"><span data-stu-id="11d1b-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="11d1b-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="11d1b-112">S_OK</span></span>|<span data-ttu-id="11d1b-113">Nadřazený stav byl úspěšně vrácen.</span><span class="sxs-lookup"><span data-stu-id="11d1b-113">The parent status was successfully returned.</span></span>|  
|<span data-ttu-id="11d1b-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="11d1b-114">E_FAIL</span></span>|<span data-ttu-id="11d1b-115">Nadřazený stav nelze vrátit.</span><span class="sxs-lookup"><span data-stu-id="11d1b-115">The parent status could not be returned.</span></span>|  
|<span data-ttu-id="11d1b-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="11d1b-116">E_INVALIDARG</span></span>|<span data-ttu-id="11d1b-117">`pPotentialParentFrame`nebo `pIsParent` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="11d1b-117">`pPotentialParentFrame` or `pIsParent` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="11d1b-118">Výjimky</span><span class="sxs-lookup"><span data-stu-id="11d1b-118">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11d1b-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="11d1b-119">Remarks</span></span>  
 <span data-ttu-id="11d1b-120">`IsMatchingParentFrame`Vrátí, `true` zda je objekt Frame, který předáte metodě, nadřazený objektu rámce, na kterém byla metoda volána.</span><span class="sxs-lookup"><span data-stu-id="11d1b-120">`IsMatchingParentFrame` returns `true` if the frame object you pass to the method is the parent of the frame object on which the method was called.</span></span> <span data-ttu-id="11d1b-121">Pokud voláte metodu na rámec, který není podřízenou položkou zadaného rámce, vrátí chybu.</span><span class="sxs-lookup"><span data-stu-id="11d1b-121">If you call the method on a frame that is not a child of the specified frame, it returns an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11d1b-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="11d1b-122">Requirements</span></span>  
 <span data-ttu-id="11d1b-123">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11d1b-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11d1b-124">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="11d1b-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="11d1b-125">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="11d1b-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11d1b-126">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11d1b-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11d1b-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="11d1b-127">See also</span></span>

- [<span data-ttu-id="11d1b-128">ICorDebugNativeFrame2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="11d1b-128">ICorDebugNativeFrame2 Interface</span></span>](icordebugnativeframe2-interface.md)
- [<span data-ttu-id="11d1b-129">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="11d1b-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="11d1b-130">Ladění</span><span class="sxs-lookup"><span data-stu-id="11d1b-130">Debugging</span></span>](index.md)
