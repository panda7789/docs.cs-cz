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
ms.openlocfilehash: 22722e4d602bdb9df9877b2199b4d4271a4d3105
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792720"
---
# <a name="icordebugnativeframe2ischild-method"></a><span data-ttu-id="76372-102">ICorDebugNativeFrame2::IsChild – metoda</span><span class="sxs-lookup"><span data-stu-id="76372-102">ICorDebugNativeFrame2::IsChild Method</span></span>
<span data-ttu-id="76372-103">Určuje, zda je aktuální rámec podřízeným rámcem.</span><span class="sxs-lookup"><span data-stu-id="76372-103">Determines whether the current frame is a child frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76372-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="76372-104">Syntax</span></span>  
  
```cpp  
HRESULT IsChild([out] BOOL * pIsChild);  
```  
  
## <a name="parameters"></a><span data-ttu-id="76372-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="76372-105">Parameters</span></span>  
 `pIsChild`  
 <span data-ttu-id="76372-106">mimo Logická hodnota, která určuje, zda je aktuální rámec podřízeným rámcem.</span><span class="sxs-lookup"><span data-stu-id="76372-106">[out] A Boolean value that specifies whether the current frame is a child frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="76372-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="76372-107">Return Value</span></span>  
 <span data-ttu-id="76372-108">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="76372-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="76372-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="76372-109">HRESULT</span></span>|<span data-ttu-id="76372-110">Popis</span><span class="sxs-lookup"><span data-stu-id="76372-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="76372-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="76372-111">S_OK</span></span>|<span data-ttu-id="76372-112">Stav podřízeného objektu byl úspěšně vrácen.</span><span class="sxs-lookup"><span data-stu-id="76372-112">The child status was successfully returned.</span></span>|  
|<span data-ttu-id="76372-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="76372-113">E_FAIL</span></span>|<span data-ttu-id="76372-114">Podřízený stav nelze vrátit.</span><span class="sxs-lookup"><span data-stu-id="76372-114">The child status could not be returned.</span></span>|  
|<span data-ttu-id="76372-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="76372-115">E_INVALIDARG</span></span>|<span data-ttu-id="76372-116">`pIsChild` je null.</span><span class="sxs-lookup"><span data-stu-id="76372-116">`pIsChild` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="76372-117">Výjimky</span><span class="sxs-lookup"><span data-stu-id="76372-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76372-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="76372-118">Remarks</span></span>  
 <span data-ttu-id="76372-119">Metoda `IsChild` vrátí `true`, pokud objekt Frame, na kterém je volána metoda, je podřízenou položkou jiného rámce.</span><span class="sxs-lookup"><span data-stu-id="76372-119">The `IsChild` method returns `true` if the frame object on which you call the method is a child of another frame.</span></span> <span data-ttu-id="76372-120">Pokud se jedná o tento případ, použijte metodu [IsMatchingParentFrame –](icordebugnativeframe2-ismatchingparentframe-method.md) a ověřte, zda je rámec nadřazeným prvkem.</span><span class="sxs-lookup"><span data-stu-id="76372-120">If this is the case, use the [IsMatchingParentFrame](icordebugnativeframe2-ismatchingparentframe-method.md) method to check whether a frame is its parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76372-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="76372-121">Requirements</span></span>  
 <span data-ttu-id="76372-122">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76372-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76372-123">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="76372-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="76372-124">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="76372-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="76372-125">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76372-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76372-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="76372-126">See also</span></span>

- [<span data-ttu-id="76372-127">ICorDebugNativeFrame2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="76372-127">ICorDebugNativeFrame2 Interface</span></span>](icordebugnativeframe2-interface.md)
- [<span data-ttu-id="76372-128">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="76372-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="76372-129">Ladění</span><span class="sxs-lookup"><span data-stu-id="76372-129">Debugging</span></span>](index.md)
