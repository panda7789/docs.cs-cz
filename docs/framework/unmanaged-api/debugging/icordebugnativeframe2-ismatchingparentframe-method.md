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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e215cf4f6d6c3cfde3fa723ecae67aa77e189917
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757055"
---
# <a name="icordebugnativeframe2ismatchingparentframe-method"></a><span data-ttu-id="73cc3-102">ICorDebugNativeFrame2::IsMatchingParentFrame – metoda</span><span class="sxs-lookup"><span data-stu-id="73cc3-102">ICorDebugNativeFrame2::IsMatchingParentFrame Method</span></span>
<span data-ttu-id="73cc3-103">Určuje, zda zadaného rámce je nadřazeného člena aktuální rámec.</span><span class="sxs-lookup"><span data-stu-id="73cc3-103">Determines whether the specified frame is the parent of the current frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73cc3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73cc3-104">Syntax</span></span>  
  
```cpp  
HRESULT IsMatchingParentFrame([in] ICorDebugNativeFrame2  
                                      *pPotentialParentFrame,  
                              [out] BOOL *pIsParent);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73cc3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="73cc3-105">Parameters</span></span>  
 `pPotentialParentFrame`  
 <span data-ttu-id="73cc3-106">[in] Ukazatel na rámec objekt, který chcete vyhodnotit stav nadřazené.</span><span class="sxs-lookup"><span data-stu-id="73cc3-106">[in] A pointer to the frame object that you want to evaluate for parent status.</span></span>  
  
 `pIsParent`  
 <span data-ttu-id="73cc3-107">[out] `true` Pokud `pPotentialParentFrame` je nadřazeným prvkem aktuální rámec; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="73cc3-107">[out] `true` if `pPotentialParentFrame` is the current frame’s parent; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="73cc3-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="73cc3-108">Return Value</span></span>  
 <span data-ttu-id="73cc3-109">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="73cc3-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="73cc3-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="73cc3-110">HRESULT</span></span>|<span data-ttu-id="73cc3-111">Popis</span><span class="sxs-lookup"><span data-stu-id="73cc3-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="73cc3-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="73cc3-112">S_OK</span></span>|<span data-ttu-id="73cc3-113">Stav nadřazeného byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="73cc3-113">The parent status was successfully returned.</span></span>|  
|<span data-ttu-id="73cc3-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="73cc3-114">E_FAIL</span></span>|<span data-ttu-id="73cc3-115">Stav nadřazeného nebylo možné vrátit.</span><span class="sxs-lookup"><span data-stu-id="73cc3-115">The parent status could not be returned.</span></span>|  
|<span data-ttu-id="73cc3-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="73cc3-116">E_INVALIDARG</span></span>|<span data-ttu-id="73cc3-117">`pPotentialParentFrame` nebo `pIsParent` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="73cc3-117">`pPotentialParentFrame` or `pIsParent` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="73cc3-118">Výjimky</span><span class="sxs-lookup"><span data-stu-id="73cc3-118">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73cc3-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="73cc3-119">Remarks</span></span>  
 <span data-ttu-id="73cc3-120">`IsMatchingParentFrame` Vrátí `true` Pokud orámovat objekt můžete předat metodě je nadřazeného člena orámovat objekt, na kterém byla volána metoda.</span><span class="sxs-lookup"><span data-stu-id="73cc3-120">`IsMatchingParentFrame` returns `true` if the frame object you pass to the method is the parent of the frame object on which the method was called.</span></span> <span data-ttu-id="73cc3-121">Při volání metody na snímek, který není podřízeným prvkem zadaného rámce, vrátí chybu.</span><span class="sxs-lookup"><span data-stu-id="73cc3-121">If you call the method on a frame that is not a child of the specified frame, it returns an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73cc3-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="73cc3-122">Requirements</span></span>  
 <span data-ttu-id="73cc3-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73cc3-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73cc3-124">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="73cc3-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73cc3-125">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73cc3-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73cc3-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73cc3-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73cc3-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="73cc3-127">See also</span></span>

- [<span data-ttu-id="73cc3-128">ICorDebugNativeFrame2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="73cc3-128">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)
- [<span data-ttu-id="73cc3-129">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="73cc3-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="73cc3-130">Ladění</span><span class="sxs-lookup"><span data-stu-id="73cc3-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
