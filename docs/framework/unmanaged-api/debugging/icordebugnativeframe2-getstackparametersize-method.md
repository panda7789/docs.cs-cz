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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60d1fafc1d5e718467b944276fc708ab34ddd782
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54727830"
---
# <a name="icordebugnativeframe2getstackparametersize-method"></a><span data-ttu-id="e4877-102">ICorDebugNativeFrame2::GetStackParameterSize – metoda</span><span class="sxs-lookup"><span data-stu-id="e4877-102">ICorDebugNativeFrame2::GetStackParameterSize Method</span></span>
<span data-ttu-id="e4877-103">Vrátí celková velikost parametry do zásobníku na x86 operačních systémů.</span><span class="sxs-lookup"><span data-stu-id="e4877-103">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4877-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4877-104">Syntax</span></span>  
  
```  
HRESULT GetStackParameterSize([out] ULONG32 * pSize)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e4877-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e4877-105">Parameters</span></span>  
 `pSize`  
 <span data-ttu-id="e4877-106">[out] Ukazatel na souhrnná velikost parametry do zásobníku.</span><span class="sxs-lookup"><span data-stu-id="e4877-106">[out] A pointer to the cumulative size of the parameters on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e4877-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e4877-107">Return Value</span></span>  
 <span data-ttu-id="e4877-108">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="e4877-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="e4877-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e4877-109">HRESULT</span></span>|<span data-ttu-id="e4877-110">Popis</span><span class="sxs-lookup"><span data-stu-id="e4877-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e4877-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e4877-111">S_OK</span></span>|<span data-ttu-id="e4877-112">Velikost zásobníku byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="e4877-112">The stack size was successfully returned.</span></span>|  
|<span data-ttu-id="e4877-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="e4877-113">S_FALSE</span></span>|<span data-ttu-id="e4877-114">`GetStackParameterSize` byla volána na platformě x x86.</span><span class="sxs-lookup"><span data-stu-id="e4877-114">`GetStackParameterSize` was called on a non-x86 platform.</span></span>|  
|<span data-ttu-id="e4877-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e4877-115">E_FAIL</span></span>|<span data-ttu-id="e4877-116">`The size of the parameters could not be returned`.</span><span class="sxs-lookup"><span data-stu-id="e4877-116">`The size of the parameters could not be returned`.</span></span>|  
|<span data-ttu-id="e4877-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="e4877-117">E_INVALIDARG</span></span>|<span data-ttu-id="e4877-118">`pSize` Is `null`.</span><span class="sxs-lookup"><span data-stu-id="e4877-118">`pSize` Is `null`.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="e4877-119">Výjimky</span><span class="sxs-lookup"><span data-stu-id="e4877-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4877-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e4877-120">Remarks</span></span>  
 <span data-ttu-id="e4877-121">[ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) metody Neupravovat ukazatel zásobníku pro parametry, které jsou vloženy do zásobníku.</span><span class="sxs-lookup"><span data-stu-id="e4877-121">The [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) methods do not adjust the stack pointer for parameters that are pushed on the stack.</span></span> <span data-ttu-id="e4877-122">Místo toho můžete použít hodnotu vrácenou příkazem `GetStackParameterSize` upravit ukazatel zásobníku naplnit nativní unwinder, který upravit parametry.</span><span class="sxs-lookup"><span data-stu-id="e4877-122">Instead, you can use the value returned by `GetStackParameterSize` to adjust the stack pointer to seed a native unwinder, which does adjust for the parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4877-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e4877-123">Requirements</span></span>  
 <span data-ttu-id="e4877-124">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4877-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4877-125">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e4877-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e4877-126">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e4877-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4877-127">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4877-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4877-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e4877-128">See also</span></span>
- [<span data-ttu-id="e4877-129">ICorDebugNativeFrame2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e4877-129">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)
- [<span data-ttu-id="e4877-130">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="e4877-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="e4877-131">Ladění</span><span class="sxs-lookup"><span data-stu-id="e4877-131">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
