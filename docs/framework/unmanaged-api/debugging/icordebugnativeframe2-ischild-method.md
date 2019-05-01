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
ms.openlocfilehash: 9503c12da9e98fbd43f3904aad25c5d10655cec2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994640"
---
# <a name="icordebugnativeframe2ischild-method"></a><span data-ttu-id="050b8-102">ICorDebugNativeFrame2::IsChild – metoda</span><span class="sxs-lookup"><span data-stu-id="050b8-102">ICorDebugNativeFrame2::IsChild Method</span></span>
<span data-ttu-id="050b8-103">Určuje, zda aktuální rámec je podřízený blok.</span><span class="sxs-lookup"><span data-stu-id="050b8-103">Determines whether the current frame is a child frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="050b8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="050b8-104">Syntax</span></span>  
  
```  
HRESULT IsChild([out] BOOL * pIsChild);  
```  
  
## <a name="parameters"></a><span data-ttu-id="050b8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="050b8-105">Parameters</span></span>  
 `pIsChild`  
 <span data-ttu-id="050b8-106">[out] Logická hodnota určující, zda je aktuální rámec podřízený blok.</span><span class="sxs-lookup"><span data-stu-id="050b8-106">[out] A Boolean value that specifies whether the current frame is a child frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="050b8-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="050b8-107">Return Value</span></span>  
 <span data-ttu-id="050b8-108">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="050b8-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="050b8-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="050b8-109">HRESULT</span></span>|<span data-ttu-id="050b8-110">Popis</span><span class="sxs-lookup"><span data-stu-id="050b8-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="050b8-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="050b8-111">S_OK</span></span>|<span data-ttu-id="050b8-112">Stav podřízeného byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="050b8-112">The child status was successfully returned.</span></span>|  
|<span data-ttu-id="050b8-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="050b8-113">E_FAIL</span></span>|<span data-ttu-id="050b8-114">Stav podřízeného nebylo možné vrátit.</span><span class="sxs-lookup"><span data-stu-id="050b8-114">The child status could not be returned.</span></span>|  
|<span data-ttu-id="050b8-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="050b8-115">E_INVALIDARG</span></span>|<span data-ttu-id="050b8-116">`pIsChild` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="050b8-116">`pIsChild` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="050b8-117">Výjimky</span><span class="sxs-lookup"><span data-stu-id="050b8-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="050b8-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="050b8-118">Remarks</span></span>  
 <span data-ttu-id="050b8-119">`IsChild` Vrátí metoda `true` Pokud orámovat objekt, na kterém je zavolat metodu je podřízeným prvkem jiného snímku.</span><span class="sxs-lookup"><span data-stu-id="050b8-119">The `IsChild` method returns `true` if the frame object on which you call the method is a child of another frame.</span></span> <span data-ttu-id="050b8-120">Pokud tomu tak, [ismatchingparentframe –](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md) metodu ke kontrole, zda blok je jeho nadřazeným prvkem.</span><span class="sxs-lookup"><span data-stu-id="050b8-120">If this is the case, use the [IsMatchingParentFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md) method to check whether a frame is its parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="050b8-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="050b8-121">Requirements</span></span>  
 <span data-ttu-id="050b8-122">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="050b8-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="050b8-123">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="050b8-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="050b8-124">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="050b8-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="050b8-125">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="050b8-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="050b8-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="050b8-126">See also</span></span>

- [<span data-ttu-id="050b8-127">ICorDebugNativeFrame2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="050b8-127">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)
- [<span data-ttu-id="050b8-128">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="050b8-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="050b8-129">Ladění</span><span class="sxs-lookup"><span data-stu-id="050b8-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
