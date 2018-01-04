---
title: "ICorDebugNativeFrame2::GetStackParameterSize – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame2.GetStackParameterSize Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame2::GetStackParameterSize
helpviewer_keywords:
- ICorDebugNativeFrame2::GetStackParameterSize method [.NET Framework debugging]
- GetStackParameterSize method [.NET Framework debugging]
ms.assetid: f6a449c8-a941-43ba-9a90-c98b29ae3c36
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fa7e67c252f2ece16c072e22d0333e085fbc4f65
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugnativeframe2getstackparametersize-method"></a><span data-ttu-id="31adb-102">ICorDebugNativeFrame2::GetStackParameterSize – metoda</span><span class="sxs-lookup"><span data-stu-id="31adb-102">ICorDebugNativeFrame2::GetStackParameterSize Method</span></span>
<span data-ttu-id="31adb-103">Vrátí celková velikost všech parametrů v zásobníku na x86 operační systémy.</span><span class="sxs-lookup"><span data-stu-id="31adb-103">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31adb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31adb-104">Syntax</span></span>  
  
```  
HRESULT GetStackParameterSize([out] ULONG32 * pSize)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="31adb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="31adb-105">Parameters</span></span>  
 `pSize`  
 <span data-ttu-id="31adb-106">[out] Ukazatel na celková velikost všech parametrů v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="31adb-106">[out] A pointer to the cumulative size of the parameters on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="31adb-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="31adb-107">Return Value</span></span>  
 <span data-ttu-id="31adb-108">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="31adb-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="31adb-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="31adb-109">HRESULT</span></span>|<span data-ttu-id="31adb-110">Popis</span><span class="sxs-lookup"><span data-stu-id="31adb-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="31adb-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="31adb-111">S_OK</span></span>|<span data-ttu-id="31adb-112">Velikost zásobníku byl byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="31adb-112">The stack size was successfully returned.</span></span>|  
|<span data-ttu-id="31adb-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="31adb-113">S_FALSE</span></span>|<span data-ttu-id="31adb-114">`GetStackParameterSize`na platformě není x86 byla volána.</span><span class="sxs-lookup"><span data-stu-id="31adb-114">`GetStackParameterSize` was called on a non-x86 platform.</span></span>|  
|<span data-ttu-id="31adb-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="31adb-115">E_FAIL</span></span>|<span data-ttu-id="31adb-116">`The size of the parameters could not be returned`.</span><span class="sxs-lookup"><span data-stu-id="31adb-116">`The size of the parameters could not be returned`.</span></span>|  
|<span data-ttu-id="31adb-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="31adb-117">E_INVALIDARG</span></span>|<span data-ttu-id="31adb-118">`pSize`Je `null`.</span><span class="sxs-lookup"><span data-stu-id="31adb-118">`pSize` Is `null`.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="31adb-119">Výjimky</span><span class="sxs-lookup"><span data-stu-id="31adb-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31adb-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="31adb-120">Remarks</span></span>  
 <span data-ttu-id="31adb-121">[ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) metody neměnit ukazatel zásobníku pro parametry, které se instaluje v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="31adb-121">The [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) methods do not adjust the stack pointer for parameters that are pushed on the stack.</span></span> <span data-ttu-id="31adb-122">Místo toho můžete použít hodnoty vrácené `GetStackParameterSize` upravit ukazatel zásobníku počáteční hodnoty nativní unwinder, který upravit parametry.</span><span class="sxs-lookup"><span data-stu-id="31adb-122">Instead, you can use the value returned by `GetStackParameterSize` to adjust the stack pointer to seed a native unwinder, which does adjust for the parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31adb-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="31adb-123">Requirements</span></span>  
 <span data-ttu-id="31adb-124">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31adb-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31adb-125">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="31adb-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="31adb-126">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="31adb-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31adb-127">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31adb-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31adb-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="31adb-128">See Also</span></span>  
 [<span data-ttu-id="31adb-129">ICorDebugNativeFrame2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="31adb-129">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)  
 [<span data-ttu-id="31adb-130">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="31adb-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="31adb-131">Ladění</span><span class="sxs-lookup"><span data-stu-id="31adb-131">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
