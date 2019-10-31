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
ms.openlocfilehash: b4f228d55c9ffd6b85ebd0b430a7f5db404320f6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124337"
---
# <a name="icordebugthread3getactiveinternalframes-method"></a><span data-ttu-id="c4c87-102">ICorDebugThread3::GetActiveInternalFrames – metoda</span><span class="sxs-lookup"><span data-stu-id="c4c87-102">ICorDebugThread3::GetActiveInternalFrames Method</span></span>
<span data-ttu-id="c4c87-103">Vrátí pole vnitřních rámců (objektů[ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) ) v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="c4c87-103">Returns an array of internal frames ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objects) on the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4c87-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4c87-104">Syntax</span></span>  
  
```cpp 
HRESULT GetActiveInternalFrames  
      (  
      [in] ULONG32 cInternalFrames,  
      [out] ULONG32 *pcInternalFrames,  
      [in, out,size_is(cInternalFrames), length_is(*pcInternalFrames)]  
            ICorDebugInternalFrame2 * ppInternalFrames[]  
      );  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4c87-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c4c87-105">Parameters</span></span>  
 `cInternalFrames`  
 <span data-ttu-id="c4c87-106">pro Počet vnitřních snímků očekávaných v `ppInternalFrames`.</span><span class="sxs-lookup"><span data-stu-id="c4c87-106">[in] The number of internal frames expected in `ppInternalFrames`.</span></span>  
  
 `pcInternalFrames`  
 <span data-ttu-id="c4c87-107">mimo Ukazatel na `ULONG32`, který obsahuje počet vnitřních snímků v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="c4c87-107">[out] A pointer to a `ULONG32` that contains the number of internal frames on the stack.</span></span>  
  
 `ppInternalFrames`  
 <span data-ttu-id="c4c87-108">[in, out] Ukazatel na adresu pole vnitřních snímků v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="c4c87-108">[in, out] A pointer to the address of an array of internal frames on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c4c87-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c4c87-109">Return Value</span></span>  
 <span data-ttu-id="c4c87-110">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="c4c87-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="c4c87-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c4c87-111">HRESULT</span></span>|<span data-ttu-id="c4c87-112">Popis</span><span class="sxs-lookup"><span data-stu-id="c4c87-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c4c87-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="c4c87-113">S_OK</span></span>|<span data-ttu-id="c4c87-114">Objekt [ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) byl úspěšně vytvořen.</span><span class="sxs-lookup"><span data-stu-id="c4c87-114">The [ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) object was successfully created.</span></span>|  
|<span data-ttu-id="c4c87-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c4c87-115">E_INVALIDARG</span></span>|<span data-ttu-id="c4c87-116">`cInternalFrames` není nula a `ppInternalFrames` je `null`nebo `pcInternalFrames` `null`.</span><span class="sxs-lookup"><span data-stu-id="c4c87-116">`cInternalFrames` is not zero and `ppInternalFrames` is `null`, or `pcInternalFrames` is `null`.</span></span>|  
|<span data-ttu-id="c4c87-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="c4c87-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="c4c87-118">`ppInternalFrames` je menší než počet vnitřních snímků.</span><span class="sxs-lookup"><span data-stu-id="c4c87-118">`ppInternalFrames` is smaller than the count of internal frames.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="c4c87-119">Výjimky</span><span class="sxs-lookup"><span data-stu-id="c4c87-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4c87-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c4c87-120">Remarks</span></span>  
 <span data-ttu-id="c4c87-121">Interní snímky jsou datové struktury vložené do zásobníku modulem runtime k ukládání dočasných dat.</span><span class="sxs-lookup"><span data-stu-id="c4c87-121">Internal frames are data structures pushed onto the stack by the runtime to store temporary data.</span></span>  
  
 <span data-ttu-id="c4c87-122">Při prvním volání `GetActiveInternalFrames`byste měli nastavit parametr `cInternalFrames` na hodnotu 0 (nula) a parametr `ppInternalFrames` na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="c4c87-122">When you first call `GetActiveInternalFrames`, you should set the `cInternalFrames` parameter to 0 (zero), and the `ppInternalFrames` parameter to null.</span></span> <span data-ttu-id="c4c87-123">Když `GetActiveInternalFrames` první vrátí, `pcInternalFrames` obsahuje počet vnitřních snímků v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="c4c87-123">When `GetActiveInternalFrames` first returns, `pcInternalFrames` contains the count of the internal frames on the stack.</span></span>  
  
 <span data-ttu-id="c4c87-124">`GetActiveInternalFrames` by se měla volat podruhé.</span><span class="sxs-lookup"><span data-stu-id="c4c87-124">`GetActiveInternalFrames` should then be called a second time.</span></span> <span data-ttu-id="c4c87-125">V parametru `cInternalFrames` byste měli předat správný počet (`pcInternalFrames`) a určit ukazatel na pole odpovídající velikosti v `ppInternalFrames`.</span><span class="sxs-lookup"><span data-stu-id="c4c87-125">You should pass the proper count (`pcInternalFrames`) in the `cInternalFrames` parameter, and specify a pointer to an appropriately sized array in `ppInternalFrames`.</span></span>  
  
 <span data-ttu-id="c4c87-126">K vrácení skutečných rámců zásobníku použijte metodu [ICorDebugStackWalk:: GetFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c4c87-126">Use the [ICorDebugStackWalk::GetFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) method to return actual stack frames.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4c87-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c4c87-127">Requirements</span></span>  
 <span data-ttu-id="c4c87-128">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4c87-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4c87-129">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c4c87-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4c87-130">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c4c87-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4c87-131">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4c87-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4c87-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c4c87-132">See also</span></span>

- [<span data-ttu-id="c4c87-133">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="c4c87-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="c4c87-134">Ladění</span><span class="sxs-lookup"><span data-stu-id="c4c87-134">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
