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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59075558"
---
# <a name="icordebugnativeframe2ischild-method"></a><span data-ttu-id="cb527-102">ICorDebugNativeFrame2::IsChild – metoda</span><span class="sxs-lookup"><span data-stu-id="cb527-102">ICorDebugNativeFrame2::IsChild Method</span></span>
<span data-ttu-id="cb527-103">Určuje, zda aktuální rámec je podřízený blok.</span><span class="sxs-lookup"><span data-stu-id="cb527-103">Determines whether the current frame is a child frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb527-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cb527-104">Syntax</span></span>  
  
```  
HRESULT IsChild([out] BOOL * pIsChild);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb527-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cb527-105">Parameters</span></span>  
 `pIsChild`  
 <span data-ttu-id="cb527-106">[out] Logická hodnota určující, zda je aktuální rámec podřízený blok.</span><span class="sxs-lookup"><span data-stu-id="cb527-106">[out] A Boolean value that specifies whether the current frame is a child frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cb527-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="cb527-107">Return Value</span></span>  
 <span data-ttu-id="cb527-108">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="cb527-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="cb527-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cb527-109">HRESULT</span></span>|<span data-ttu-id="cb527-110">Popis</span><span class="sxs-lookup"><span data-stu-id="cb527-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cb527-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="cb527-111">S_OK</span></span>|<span data-ttu-id="cb527-112">Stav podřízeného byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="cb527-112">The child status was successfully returned.</span></span>|  
|<span data-ttu-id="cb527-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cb527-113">E_FAIL</span></span>|<span data-ttu-id="cb527-114">Stav podřízeného nebylo možné vrátit.</span><span class="sxs-lookup"><span data-stu-id="cb527-114">The child status could not be returned.</span></span>|  
|<span data-ttu-id="cb527-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="cb527-115">E_INVALIDARG</span></span>|`pIsChild` <span data-ttu-id="cb527-116">má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="cb527-116">is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="cb527-117">Výjimky</span><span class="sxs-lookup"><span data-stu-id="cb527-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb527-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cb527-118">Remarks</span></span>  
 <span data-ttu-id="cb527-119">`IsChild` Vrátí metoda `true` Pokud orámovat objekt, na kterém je zavolat metodu je podřízeným prvkem jiného snímku.</span><span class="sxs-lookup"><span data-stu-id="cb527-119">The `IsChild` method returns `true` if the frame object on which you call the method is a child of another frame.</span></span> <span data-ttu-id="cb527-120">Pokud tomu tak, [ismatchingparentframe –](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md) metodu ke kontrole, zda blok je jeho nadřazeným prvkem.</span><span class="sxs-lookup"><span data-stu-id="cb527-120">If this is the case, use the [IsMatchingParentFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md) method to check whether a frame is its parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb527-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cb527-121">Requirements</span></span>  
 <span data-ttu-id="cb527-122">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb527-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb527-123">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cb527-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cb527-124">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb527-124">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="cb527-125">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="cb527-125">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cb527-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cb527-126">See also</span></span>

- [<span data-ttu-id="cb527-127">ICorDebugNativeFrame2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cb527-127">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)
- [<span data-ttu-id="cb527-128">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cb527-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="cb527-129">Ladění</span><span class="sxs-lookup"><span data-stu-id="cb527-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
