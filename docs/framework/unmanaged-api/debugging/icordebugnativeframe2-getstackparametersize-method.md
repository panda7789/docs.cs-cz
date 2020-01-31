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
ms.openlocfilehash: ca742ba9e89e1d189cfa38dead314df0d8b4e9d1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792766"
---
# <a name="icordebugnativeframe2getstackparametersize-method"></a><span data-ttu-id="a7c7d-102">ICorDebugNativeFrame2::GetStackParameterSize – metoda</span><span class="sxs-lookup"><span data-stu-id="a7c7d-102">ICorDebugNativeFrame2::GetStackParameterSize Method</span></span>
<span data-ttu-id="a7c7d-103">Vrátí kumulativní velikost parametrů v zásobníku v operačních systémech x86.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-103">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7c7d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a7c7d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackParameterSize([out] ULONG32 * pSize)  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7c7d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7c7d-105">Parameters</span></span>  
 `pSize`  
 <span data-ttu-id="a7c7d-106">mimo Ukazatel na kumulativní velikost parametrů v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-106">[out] A pointer to the cumulative size of the parameters on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a7c7d-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a7c7d-107">Return Value</span></span>  
 <span data-ttu-id="a7c7d-108">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a7c7d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a7c7d-109">HRESULT</span></span>|<span data-ttu-id="a7c7d-110">Popis</span><span class="sxs-lookup"><span data-stu-id="a7c7d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a7c7d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a7c7d-111">S_OK</span></span>|<span data-ttu-id="a7c7d-112">Velikost zásobníku byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-112">The stack size was successfully returned.</span></span>|  
|<span data-ttu-id="a7c7d-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="a7c7d-113">S_FALSE</span></span>|<span data-ttu-id="a7c7d-114">`GetStackParameterSize` byla volána na platformě, která není x86.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-114">`GetStackParameterSize` was called on a non-x86 platform.</span></span>|  
|<span data-ttu-id="a7c7d-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a7c7d-115">E_FAIL</span></span>|<span data-ttu-id="a7c7d-116">`The size of the parameters could not be returned`.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-116">`The size of the parameters could not be returned`.</span></span>|  
|<span data-ttu-id="a7c7d-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a7c7d-117">E_INVALIDARG</span></span>|<span data-ttu-id="a7c7d-118">`pSize` je `null`.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-118">`pSize` Is `null`.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="a7c7d-119">Výjimky</span><span class="sxs-lookup"><span data-stu-id="a7c7d-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7c7d-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a7c7d-120">Remarks</span></span>  
 <span data-ttu-id="a7c7d-121">Metody [ICorDebugStackWalk](icordebugstackwalk-interface.md) neupravují ukazatel zásobníku pro parametry, které jsou vloženy do zásobníku.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-121">The [ICorDebugStackWalk](icordebugstackwalk-interface.md) methods do not adjust the stack pointer for parameters that are pushed on the stack.</span></span> <span data-ttu-id="a7c7d-122">Místo toho můžete použít hodnotu vrácenou `GetStackParameterSize` k úpravě ukazatele zásobníku na počáteční hodnotu nativního unwind, který pro parametry upraví.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-122">Instead, you can use the value returned by `GetStackParameterSize` to adjust the stack pointer to seed a native unwinder, which does adjust for the parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7c7d-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a7c7d-123">Requirements</span></span>  
 <span data-ttu-id="a7c7d-124">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7c7d-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7c7d-125">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a7c7d-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a7c7d-126">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a7c7d-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7c7d-127">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7c7d-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7c7d-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a7c7d-128">See also</span></span>

- [<span data-ttu-id="a7c7d-129">ICorDebugNativeFrame2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a7c7d-129">ICorDebugNativeFrame2 Interface</span></span>](icordebugnativeframe2-interface.md)
- [<span data-ttu-id="a7c7d-130">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="a7c7d-130">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="a7c7d-131">Ladění</span><span class="sxs-lookup"><span data-stu-id="a7c7d-131">Debugging</span></span>](index.md)
