---
title: "ICorDebugNativeFrame2::IsChild – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame2.IsChild Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame2::IsChild
helpviewer_keywords:
- IsChild method [.NET Framework debugging]
- ICorDebugNativeFrame2::IsChild method [.NET Framework debugging]
ms.assetid: 9e2aae09-49cb-4fbd-81e5-e29cd864a88b
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 267bc2fcd03786bfceb218dd0218ffa7006f8fa7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugnativeframe2ischild-method"></a><span data-ttu-id="8078e-102">ICorDebugNativeFrame2::IsChild – metoda</span><span class="sxs-lookup"><span data-stu-id="8078e-102">ICorDebugNativeFrame2::IsChild Method</span></span>
<span data-ttu-id="8078e-103">Určuje, zda je aktuální snímek podřízeného rámce.</span><span class="sxs-lookup"><span data-stu-id="8078e-103">Determines whether the current frame is a child frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8078e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8078e-104">Syntax</span></span>  
  
```  
HRESULT IsChild([out] BOOL * pIsChild);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8078e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8078e-105">Parameters</span></span>  
 `pIsChild`  
 <span data-ttu-id="8078e-106">[out] Logická hodnota, která určuje, zda aktuální snímek podřízeného rámce.</span><span class="sxs-lookup"><span data-stu-id="8078e-106">[out] A Boolean value that specifies whether the current frame is a child frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8078e-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8078e-107">Return Value</span></span>  
 <span data-ttu-id="8078e-108">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="8078e-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="8078e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8078e-109">HRESULT</span></span>|<span data-ttu-id="8078e-110">Popis</span><span class="sxs-lookup"><span data-stu-id="8078e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8078e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="8078e-111">S_OK</span></span>|<span data-ttu-id="8078e-112">Stav podřízeného byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="8078e-112">The child status was successfully returned.</span></span>|  
|<span data-ttu-id="8078e-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8078e-113">E_FAIL</span></span>|<span data-ttu-id="8078e-114">Stav podřízeného nejde vrátit.</span><span class="sxs-lookup"><span data-stu-id="8078e-114">The child status could not be returned.</span></span>|  
|<span data-ttu-id="8078e-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="8078e-115">E_INVALIDARG</span></span>|<span data-ttu-id="8078e-116">`pIsChild`má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="8078e-116">`pIsChild` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="8078e-117">Výjimky</span><span class="sxs-lookup"><span data-stu-id="8078e-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8078e-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8078e-118">Remarks</span></span>  
 <span data-ttu-id="8078e-119">`IsChild` Metoda vrátí `true` Pokud rámce objektu, na kterém budete volat metodu je podřízená jiné rámce.</span><span class="sxs-lookup"><span data-stu-id="8078e-119">The `IsChild` method returns `true` if the frame object on which you call the method is a child of another frame.</span></span> <span data-ttu-id="8078e-120">Pokud je to tento případ, použijte [ismatchingparentframe –](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md) metoda zkontrolujte, zda rámeček je jeho nadřazeným prvkem.</span><span class="sxs-lookup"><span data-stu-id="8078e-120">If this is the case, use the [IsMatchingParentFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md) method to check whether a frame is its parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8078e-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8078e-121">Requirements</span></span>  
 <span data-ttu-id="8078e-122">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8078e-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8078e-123">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8078e-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8078e-124">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8078e-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8078e-125">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8078e-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8078e-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="8078e-126">See Also</span></span>  
 [<span data-ttu-id="8078e-127">ICorDebugNativeFrame2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8078e-127">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)  
 [<span data-ttu-id="8078e-128">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="8078e-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="8078e-129">Ladění</span><span class="sxs-lookup"><span data-stu-id="8078e-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
