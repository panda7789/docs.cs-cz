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
ms.openlocfilehash: 47968d7550c3d16d201680caab705c0d7c85c784
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59200139"
---
# <a name="icordebugnativeframe2getstackparametersize-method"></a><span data-ttu-id="aa4fe-102">ICorDebugNativeFrame2::GetStackParameterSize – metoda</span><span class="sxs-lookup"><span data-stu-id="aa4fe-102">ICorDebugNativeFrame2::GetStackParameterSize Method</span></span>
<span data-ttu-id="aa4fe-103">Vrátí celková velikost parametry do zásobníku na x86 operačních systémů.</span><span class="sxs-lookup"><span data-stu-id="aa4fe-103">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa4fe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aa4fe-104">Syntax</span></span>  
  
```  
HRESULT GetStackParameterSize([out] ULONG32 * pSize)  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa4fe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa4fe-105">Parameters</span></span>  
 `pSize`  
 <span data-ttu-id="aa4fe-106">[out] Ukazatel na souhrnná velikost parametry do zásobníku.</span><span class="sxs-lookup"><span data-stu-id="aa4fe-106">[out] A pointer to the cumulative size of the parameters on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aa4fe-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="aa4fe-107">Return Value</span></span>  
 <span data-ttu-id="aa4fe-108">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="aa4fe-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="aa4fe-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aa4fe-109">HRESULT</span></span>|<span data-ttu-id="aa4fe-110">Popis</span><span class="sxs-lookup"><span data-stu-id="aa4fe-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aa4fe-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="aa4fe-111">S_OK</span></span>|<span data-ttu-id="aa4fe-112">Velikost zásobníku byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="aa4fe-112">The stack size was successfully returned.</span></span>|  
|<span data-ttu-id="aa4fe-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="aa4fe-113">S_FALSE</span></span>|`GetStackParameterSize` <span data-ttu-id="aa4fe-114">byla volána na platformě x x86.</span><span class="sxs-lookup"><span data-stu-id="aa4fe-114">was called on a non-x86 platform.</span></span>|  
|<span data-ttu-id="aa4fe-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="aa4fe-115">E_FAIL</span></span>|`The size of the parameters could not be returned`<span data-ttu-id="aa4fe-116">.</span><span class="sxs-lookup"><span data-stu-id="aa4fe-116">.</span></span>|  
|<span data-ttu-id="aa4fe-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="aa4fe-117">E_INVALIDARG</span></span>|`pSize` <span data-ttu-id="aa4fe-118">Is `null`.</span><span class="sxs-lookup"><span data-stu-id="aa4fe-118">Is `null`.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="aa4fe-119">Výjimky</span><span class="sxs-lookup"><span data-stu-id="aa4fe-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aa4fe-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aa4fe-120">Remarks</span></span>  
 <span data-ttu-id="aa4fe-121">[ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) metody Neupravovat ukazatel zásobníku pro parametry, které jsou vloženy do zásobníku.</span><span class="sxs-lookup"><span data-stu-id="aa4fe-121">The [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) methods do not adjust the stack pointer for parameters that are pushed on the stack.</span></span> <span data-ttu-id="aa4fe-122">Místo toho můžete použít hodnotu vrácenou příkazem `GetStackParameterSize` upravit ukazatel zásobníku naplnit nativní unwinder, který upravit parametry.</span><span class="sxs-lookup"><span data-stu-id="aa4fe-122">Instead, you can use the value returned by `GetStackParameterSize` to adjust the stack pointer to seed a native unwinder, which does adjust for the parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa4fe-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aa4fe-123">Requirements</span></span>  
 <span data-ttu-id="aa4fe-124">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa4fe-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa4fe-125">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aa4fe-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aa4fe-126">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aa4fe-126">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="aa4fe-127">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="aa4fe-127">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="aa4fe-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aa4fe-128">See also</span></span>

- [<span data-ttu-id="aa4fe-129">ICorDebugNativeFrame2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aa4fe-129">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)
- [<span data-ttu-id="aa4fe-130">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aa4fe-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="aa4fe-131">Ladění</span><span class="sxs-lookup"><span data-stu-id="aa4fe-131">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
