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
ms.openlocfilehash: b88b3907eb555050de93f35411629b2bd30c7375
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212942"
---
# <a name="icordebugnativeframe2getstackparametersize-method"></a><span data-ttu-id="6b116-102">ICorDebugNativeFrame2::GetStackParameterSize – metoda</span><span class="sxs-lookup"><span data-stu-id="6b116-102">ICorDebugNativeFrame2::GetStackParameterSize Method</span></span>
<span data-ttu-id="6b116-103">Vrátí kumulativní velikost parametrů v zásobníku v operačních systémech x86.</span><span class="sxs-lookup"><span data-stu-id="6b116-103">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b116-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6b116-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackParameterSize([out] ULONG32 * pSize)  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b116-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6b116-105">Parameters</span></span>  
 `pSize`  
 <span data-ttu-id="6b116-106">mimo Ukazatel na kumulativní velikost parametrů v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="6b116-106">[out] A pointer to the cumulative size of the parameters on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6b116-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6b116-107">Return Value</span></span>  
 <span data-ttu-id="6b116-108">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="6b116-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="6b116-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6b116-109">HRESULT</span></span>|<span data-ttu-id="6b116-110">Popis</span><span class="sxs-lookup"><span data-stu-id="6b116-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6b116-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="6b116-111">S_OK</span></span>|<span data-ttu-id="6b116-112">Velikost zásobníku byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="6b116-112">The stack size was successfully returned.</span></span>|  
|<span data-ttu-id="6b116-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="6b116-113">S_FALSE</span></span>|<span data-ttu-id="6b116-114">`GetStackParameterSize`byla volána na platformě, která není x86.</span><span class="sxs-lookup"><span data-stu-id="6b116-114">`GetStackParameterSize` was called on a non-x86 platform.</span></span>|  
|<span data-ttu-id="6b116-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6b116-115">E_FAIL</span></span>|<span data-ttu-id="6b116-116">`The size of the parameters could not be returned`.</span><span class="sxs-lookup"><span data-stu-id="6b116-116">`The size of the parameters could not be returned`.</span></span>|  
|<span data-ttu-id="6b116-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="6b116-117">E_INVALIDARG</span></span>|<span data-ttu-id="6b116-118">`pSize`Je `null` .</span><span class="sxs-lookup"><span data-stu-id="6b116-118">`pSize` Is `null`.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="6b116-119">Výjimky</span><span class="sxs-lookup"><span data-stu-id="6b116-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b116-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6b116-120">Remarks</span></span>  
 <span data-ttu-id="6b116-121">Metody [ICorDebugStackWalk](icordebugstackwalk-interface.md) neupravují ukazatel zásobníku pro parametry, které jsou vloženy do zásobníku.</span><span class="sxs-lookup"><span data-stu-id="6b116-121">The [ICorDebugStackWalk](icordebugstackwalk-interface.md) methods do not adjust the stack pointer for parameters that are pushed on the stack.</span></span> <span data-ttu-id="6b116-122">Místo toho můžete použít hodnotu vrácenou `GetStackParameterSize` pro úpravu ukazatele zásobníku na osazení nativního unwindu, který je upraven pro parametry.</span><span class="sxs-lookup"><span data-stu-id="6b116-122">Instead, you can use the value returned by `GetStackParameterSize` to adjust the stack pointer to seed a native unwinder, which does adjust for the parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b116-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6b116-123">Requirements</span></span>  
 <span data-ttu-id="6b116-124">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b116-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b116-125">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6b116-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6b116-126">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6b116-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b116-127">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b116-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b116-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="6b116-128">See also</span></span>

- [<span data-ttu-id="6b116-129">ICorDebugNativeFrame2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6b116-129">ICorDebugNativeFrame2 Interface</span></span>](icordebugnativeframe2-interface.md)
- [<span data-ttu-id="6b116-130">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6b116-130">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="6b116-131">Ladění</span><span class="sxs-lookup"><span data-stu-id="6b116-131">Debugging</span></span>](index.md)
