---
title: ICorDebugNativeFrame2::IsChild – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2.IsChild Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2::IsChild
helpviewer_keywords:
- IsChild method [.NET Framework debugging]
- ICorDebugNativeFrame2::IsChild method [.NET Framework debugging]
ms.assetid: 9e2aae09-49cb-4fbd-81e5-e29cd864a88b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 550d25e995bdfe010fb1aa664a7c9882a775f4d5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757169"
---
# <a name="icordebugnativeframe2ischild-method"></a><span data-ttu-id="e2576-102">ICorDebugNativeFrame2::IsChild – metoda</span><span class="sxs-lookup"><span data-stu-id="e2576-102">ICorDebugNativeFrame2::IsChild Method</span></span>
<span data-ttu-id="e2576-103">Určuje, zda aktuální rámec je podřízený blok.</span><span class="sxs-lookup"><span data-stu-id="e2576-103">Determines whether the current frame is a child frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2576-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e2576-104">Syntax</span></span>  
  
```cpp  
HRESULT IsChild([out] BOOL * pIsChild);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e2576-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e2576-105">Parameters</span></span>  
 `pIsChild`  
 <span data-ttu-id="e2576-106">[out] Logická hodnota určující, zda je aktuální rámec podřízený blok.</span><span class="sxs-lookup"><span data-stu-id="e2576-106">[out] A Boolean value that specifies whether the current frame is a child frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e2576-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e2576-107">Return Value</span></span>  
 <span data-ttu-id="e2576-108">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="e2576-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="e2576-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e2576-109">HRESULT</span></span>|<span data-ttu-id="e2576-110">Popis</span><span class="sxs-lookup"><span data-stu-id="e2576-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e2576-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e2576-111">S_OK</span></span>|<span data-ttu-id="e2576-112">Stav podřízeného byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="e2576-112">The child status was successfully returned.</span></span>|  
|<span data-ttu-id="e2576-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e2576-113">E_FAIL</span></span>|<span data-ttu-id="e2576-114">Stav podřízeného nebylo možné vrátit.</span><span class="sxs-lookup"><span data-stu-id="e2576-114">The child status could not be returned.</span></span>|  
|<span data-ttu-id="e2576-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="e2576-115">E_INVALIDARG</span></span>|<span data-ttu-id="e2576-116">`pIsChild` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="e2576-116">`pIsChild` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="e2576-117">Výjimky</span><span class="sxs-lookup"><span data-stu-id="e2576-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e2576-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e2576-118">Remarks</span></span>  
 <span data-ttu-id="e2576-119">`IsChild` Vrátí metoda `true` Pokud orámovat objekt, na kterém je zavolat metodu je podřízeným prvkem jiného snímku.</span><span class="sxs-lookup"><span data-stu-id="e2576-119">The `IsChild` method returns `true` if the frame object on which you call the method is a child of another frame.</span></span> <span data-ttu-id="e2576-120">Pokud tomu tak, [ismatchingparentframe –](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md) metodu ke kontrole, zda blok je jeho nadřazeným prvkem.</span><span class="sxs-lookup"><span data-stu-id="e2576-120">If this is the case, use the [IsMatchingParentFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md) method to check whether a frame is its parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2576-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e2576-121">Requirements</span></span>  
 <span data-ttu-id="e2576-122">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2576-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2576-123">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e2576-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e2576-124">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e2576-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e2576-125">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2576-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2576-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e2576-126">See also</span></span>

- [<span data-ttu-id="e2576-127">ICorDebugNativeFrame2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e2576-127">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)
- [<span data-ttu-id="e2576-128">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="e2576-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="e2576-129">Ladění</span><span class="sxs-lookup"><span data-stu-id="e2576-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
