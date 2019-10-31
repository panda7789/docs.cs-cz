---
title: ICorDebugNativeFrame2::GetStackParameterSize – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2.GetStackParameterSize Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2::GetStackParameterSize
helpviewer_keywords:
- ICorDebugNativeFrame2::GetStackParameterSize method [.NET Framework debugging]
- GetStackParameterSize method [.NET Framework debugging]
ms.assetid: f6a449c8-a941-43ba-9a90-c98b29ae3c36
topic_type:
- apiref
ms.openlocfilehash: 4dd9760c347bbc23f3e8225c1ff748c6b7b8bfe1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096529"
---
# <a name="icordebugnativeframe2getstackparametersize-method"></a><span data-ttu-id="e9253-102">ICorDebugNativeFrame2::GetStackParameterSize – metoda</span><span class="sxs-lookup"><span data-stu-id="e9253-102">ICorDebugNativeFrame2::GetStackParameterSize Method</span></span>
<span data-ttu-id="e9253-103">Vrátí kumulativní velikost parametrů v zásobníku v operačních systémech x86.</span><span class="sxs-lookup"><span data-stu-id="e9253-103">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9253-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9253-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackParameterSize([out] ULONG32 * pSize)  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9253-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9253-105">Parameters</span></span>  
 `pSize`  
 <span data-ttu-id="e9253-106">mimo Ukazatel na kumulativní velikost parametrů v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="e9253-106">[out] A pointer to the cumulative size of the parameters on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e9253-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e9253-107">Return Value</span></span>  
 <span data-ttu-id="e9253-108">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="e9253-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="e9253-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e9253-109">HRESULT</span></span>|<span data-ttu-id="e9253-110">Popis</span><span class="sxs-lookup"><span data-stu-id="e9253-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e9253-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e9253-111">S_OK</span></span>|<span data-ttu-id="e9253-112">Velikost zásobníku byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="e9253-112">The stack size was successfully returned.</span></span>|  
|<span data-ttu-id="e9253-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="e9253-113">S_FALSE</span></span>|<span data-ttu-id="e9253-114">`GetStackParameterSize` byla volána na platformě, která není x86.</span><span class="sxs-lookup"><span data-stu-id="e9253-114">`GetStackParameterSize` was called on a non-x86 platform.</span></span>|  
|<span data-ttu-id="e9253-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e9253-115">E_FAIL</span></span>|<span data-ttu-id="e9253-116">`The size of the parameters could not be returned`.</span><span class="sxs-lookup"><span data-stu-id="e9253-116">`The size of the parameters could not be returned`.</span></span>|  
|<span data-ttu-id="e9253-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="e9253-117">E_INVALIDARG</span></span>|<span data-ttu-id="e9253-118">`pSize` je `null`.</span><span class="sxs-lookup"><span data-stu-id="e9253-118">`pSize` Is `null`.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="e9253-119">Výjimky</span><span class="sxs-lookup"><span data-stu-id="e9253-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9253-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e9253-120">Remarks</span></span>  
 <span data-ttu-id="e9253-121">Metody [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) neupravují ukazatel zásobníku pro parametry, které jsou vloženy do zásobníku.</span><span class="sxs-lookup"><span data-stu-id="e9253-121">The [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) methods do not adjust the stack pointer for parameters that are pushed on the stack.</span></span> <span data-ttu-id="e9253-122">Místo toho můžete použít hodnotu vrácenou `GetStackParameterSize` k úpravě ukazatele zásobníku na počáteční hodnotu nativního unwind, který pro parametry upraví.</span><span class="sxs-lookup"><span data-stu-id="e9253-122">Instead, you can use the value returned by `GetStackParameterSize` to adjust the stack pointer to seed a native unwinder, which does adjust for the parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9253-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e9253-123">Requirements</span></span>  
 <span data-ttu-id="e9253-124">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9253-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9253-125">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e9253-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e9253-126">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e9253-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9253-127">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9253-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9253-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e9253-128">See also</span></span>

- [<span data-ttu-id="e9253-129">ICorDebugNativeFrame2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e9253-129">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)
- [<span data-ttu-id="e9253-130">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="e9253-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="e9253-131">Ladění</span><span class="sxs-lookup"><span data-stu-id="e9253-131">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
