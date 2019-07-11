---
title: ICorDebugThread3::GetActiveInternalFrames – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread3.GetActiveInternalFrames Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3::GetActiveInternalFrames
helpviewer_keywords:
- ICorDebugThread3::GetActiveInternalFrames method [.NET Framework debugging]
- GetActiveInternalFrames method [.NET Framework debugging]
ms.assetid: d69796b4-5b6d-457c-85f6-2cf42e8a8773
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 58aaf0445fe42d083c12541056cb362f9a994944
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765207"
---
# <a name="icordebugthread3getactiveinternalframes-method"></a><span data-ttu-id="dda68-102">ICorDebugThread3::GetActiveInternalFrames – metoda</span><span class="sxs-lookup"><span data-stu-id="dda68-102">ICorDebugThread3::GetActiveInternalFrames Method</span></span>
<span data-ttu-id="dda68-103">Vrátí pole vnitřních rámcích ([icordebuginternalframe2 –](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objektů) v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="dda68-103">Returns an array of internal frames ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objects) on the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dda68-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dda68-104">Syntax</span></span>  
  
```cpp 
HRESULT GetActiveInternalFrames  
      (  
      [in] ULONG32 cInternalFrames,  
      [out] ULONG32 *pcInternalFrames,  
      [in, out,size_is(cInternalFrames), length_is(*pcInternalFrames)]  
            ICorDebugInternalFrame2 * ppInternalFrames[]  
      );  
```  
  
## <a name="parameters"></a><span data-ttu-id="dda68-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dda68-105">Parameters</span></span>  
 `cInternalFrames`  
 <span data-ttu-id="dda68-106">[in] Počet vnitřních rámcích, byl očekáván v `ppInternalFrames`.</span><span class="sxs-lookup"><span data-stu-id="dda68-106">[in] The number of internal frames expected in `ppInternalFrames`.</span></span>  
  
 `pcInternalFrames`  
 <span data-ttu-id="dda68-107">[out] Ukazatel `ULONG32` , který obsahuje počet vnitřních rámcích v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="dda68-107">[out] A pointer to a `ULONG32` that contains the number of internal frames on the stack.</span></span>  
  
 `ppInternalFrames`  
 <span data-ttu-id="dda68-108">[out v] Ukazatel na adresu pole interní rámce v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="dda68-108">[in, out] A pointer to the address of an array of internal frames on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dda68-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="dda68-109">Return Value</span></span>  
 <span data-ttu-id="dda68-110">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="dda68-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="dda68-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dda68-111">HRESULT</span></span>|<span data-ttu-id="dda68-112">Popis</span><span class="sxs-lookup"><span data-stu-id="dda68-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dda68-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="dda68-113">S_OK</span></span>|<span data-ttu-id="dda68-114">[Icordebuginternalframe2 –](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objekt byl úspěšně vytvořen.</span><span class="sxs-lookup"><span data-stu-id="dda68-114">The [ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) object was successfully created.</span></span>|  
|<span data-ttu-id="dda68-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="dda68-115">E_INVALIDARG</span></span>|<span data-ttu-id="dda68-116">`cInternalFrames` není nula a `ppInternalFrames` je `null`, nebo `pcInternalFrames` je `null`.</span><span class="sxs-lookup"><span data-stu-id="dda68-116">`cInternalFrames` is not zero and `ppInternalFrames` is `null`, or `pcInternalFrames` is `null`.</span></span>|  
|<span data-ttu-id="dda68-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="dda68-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="dda68-118">`ppInternalFrames` je menší než počet vnitřních rámcích.</span><span class="sxs-lookup"><span data-stu-id="dda68-118">`ppInternalFrames` is smaller than the count of internal frames.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="dda68-119">Výjimky</span><span class="sxs-lookup"><span data-stu-id="dda68-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dda68-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dda68-120">Remarks</span></span>  
 <span data-ttu-id="dda68-121">Vnitřních rámcích jsou vloženy do zásobníku modulem runtime pro ukládání dočasných dat datové struktury.</span><span class="sxs-lookup"><span data-stu-id="dda68-121">Internal frames are data structures pushed onto the stack by the runtime to store temporary data.</span></span>  
  
 <span data-ttu-id="dda68-122">Při prvním volání `GetActiveInternalFrames`, byste měli nastavit `cInternalFrames` parametru na hodnotu 0 (nula) a `ppInternalFrames` parametr na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="dda68-122">When you first call `GetActiveInternalFrames`, you should set the `cInternalFrames` parameter to 0 (zero), and the `ppInternalFrames` parameter to null.</span></span> <span data-ttu-id="dda68-123">Když `GetActiveInternalFrames` nejprve vrátí `pcInternalFrames` obsahuje počet vnitřních rámcích v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="dda68-123">When `GetActiveInternalFrames` first returns, `pcInternalFrames` contains the count of the internal frames on the stack.</span></span>  
  
 <span data-ttu-id="dda68-124">`GetActiveInternalFrames` pak lze volat podruhé.</span><span class="sxs-lookup"><span data-stu-id="dda68-124">`GetActiveInternalFrames` should then be called a second time.</span></span> <span data-ttu-id="dda68-125">Je třeba předat správný počet (`pcInternalFrames`) v `cInternalFrames` parametr, a zadejte ukazatel na odpovídající velikosti pole v `ppInternalFrames`.</span><span class="sxs-lookup"><span data-stu-id="dda68-125">You should pass the proper count (`pcInternalFrames`) in the `cInternalFrames` parameter, and specify a pointer to an appropriately sized array in `ppInternalFrames`.</span></span>  
  
 <span data-ttu-id="dda68-126">Použití [icordebugstackwalk::getframe –](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) metoda vrátí skutečný rámců zásobníku.</span><span class="sxs-lookup"><span data-stu-id="dda68-126">Use the [ICorDebugStackWalk::GetFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) method to return actual stack frames.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dda68-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dda68-127">Requirements</span></span>  
 <span data-ttu-id="dda68-128">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dda68-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dda68-129">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dda68-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dda68-130">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dda68-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dda68-131">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dda68-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dda68-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dda68-132">See also</span></span>

- [<span data-ttu-id="dda68-133">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="dda68-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="dda68-134">Ladění</span><span class="sxs-lookup"><span data-stu-id="dda68-134">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
