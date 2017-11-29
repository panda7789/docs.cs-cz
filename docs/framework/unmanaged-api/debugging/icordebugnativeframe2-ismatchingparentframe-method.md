---
title: "ICorDebugNativeFrame2::IsMatchingParentFrame – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame2.IsMatchingParentFrame Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame2::IsMatchingParentFrame
helpviewer_keywords:
- IsMatchingParentFrame method [.NET Framework debugging]
- ICorDebugNativeFrame2::IsMatchingParentFrame method [.NET Framework debugging]
ms.assetid: d2ca20db-df22-4528-a0dd-a09ea62c8998
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e261f4cb43843ec61ec6cbd1609e6967a4a38a82
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugnativeframe2ismatchingparentframe-method"></a><span data-ttu-id="0f224-102">ICorDebugNativeFrame2::IsMatchingParentFrame – metoda</span><span class="sxs-lookup"><span data-stu-id="0f224-102">ICorDebugNativeFrame2::IsMatchingParentFrame Method</span></span>
<span data-ttu-id="0f224-103">Určuje, zda je zadaný rámečku nadřazeného aktuální snímek.</span><span class="sxs-lookup"><span data-stu-id="0f224-103">Determines whether the specified frame is the parent of the current frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f224-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0f224-104">Syntax</span></span>  
  
```  
HRESULT IsMatchingParentFrame([in] ICorDebugNativeFrame2  
                                      *pPotentialParentFrame,  
                              [out] BOOL *pIsParent);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0f224-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0f224-105">Parameters</span></span>  
 `pPotentialParentFrame`  
 <span data-ttu-id="0f224-106">[v] Ukazatel na rámec objekt, který chcete vyhodnotit stav nadřazené.</span><span class="sxs-lookup"><span data-stu-id="0f224-106">[in] A pointer to the frame object that you want to evaluate for parent status.</span></span>  
  
 `pIsParent`  
 <span data-ttu-id="0f224-107">[out] `true` Pokud `pPotentialParentFrame` je nadřazený aktuální rámečku, jinak hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="0f224-107">[out] `true` if `pPotentialParentFrame` is the current frame’s parent; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0f224-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0f224-108">Return Value</span></span>  
 <span data-ttu-id="0f224-109">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="0f224-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="0f224-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0f224-110">HRESULT</span></span>|<span data-ttu-id="0f224-111">Popis</span><span class="sxs-lookup"><span data-stu-id="0f224-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0f224-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="0f224-112">S_OK</span></span>|<span data-ttu-id="0f224-113">Stav nadřazeného byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="0f224-113">The parent status was successfully returned.</span></span>|  
|<span data-ttu-id="0f224-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0f224-114">E_FAIL</span></span>|<span data-ttu-id="0f224-115">Stav nadřazeného nejde vrátit.</span><span class="sxs-lookup"><span data-stu-id="0f224-115">The parent status could not be returned.</span></span>|  
|<span data-ttu-id="0f224-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="0f224-116">E_INVALIDARG</span></span>|<span data-ttu-id="0f224-117">`pPotentialParentFrame`nebo `pIsParent` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="0f224-117">`pPotentialParentFrame` or `pIsParent` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="0f224-118">Výjimky</span><span class="sxs-lookup"><span data-stu-id="0f224-118">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f224-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0f224-119">Remarks</span></span>  
 <span data-ttu-id="0f224-120">`IsMatchingParentFrame`Vrátí `true` Pokud je objekt rámce předáte metodě nadřazeného objektu rámce volání metody.</span><span class="sxs-lookup"><span data-stu-id="0f224-120">`IsMatchingParentFrame` returns `true` if the frame object you pass to the method is the parent of the frame object on which the method was called.</span></span> <span data-ttu-id="0f224-121">Když zavoláte metodu na rámce, který není podřízenou zadaného rámce, vrátí chybu.</span><span class="sxs-lookup"><span data-stu-id="0f224-121">If you call the method on a frame that is not a child of the specified frame, it returns an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f224-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0f224-122">Requirements</span></span>  
 <span data-ttu-id="0f224-123">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f224-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f224-124">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0f224-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0f224-125">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0f224-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0f224-126">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f224-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f224-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="0f224-127">See Also</span></span>  
 [<span data-ttu-id="0f224-128">Icordebugnativeframe2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0f224-128">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)  
 [<span data-ttu-id="0f224-129">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="0f224-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="0f224-130">Ladění</span><span class="sxs-lookup"><span data-stu-id="0f224-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
