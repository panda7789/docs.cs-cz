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
ms.openlocfilehash: 680af5afa3ebef5bcaf9e34580e421dcc8093aaf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178469"
---
# <a name="icordebugthread3getactiveinternalframes-method"></a><span data-ttu-id="90a27-102">ICorDebugThread3::GetActiveInternalFrames – metoda</span><span class="sxs-lookup"><span data-stu-id="90a27-102">ICorDebugThread3::GetActiveInternalFrames Method</span></span>
<span data-ttu-id="90a27-103">Vrátí pole vnitřních rámců ([ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) objekty) v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="90a27-103">Returns an array of internal frames ([ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) objects) on the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90a27-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90a27-104">Syntax</span></span>  
  
```cpp
HRESULT GetActiveInternalFrames  
      (  
      [in] ULONG32 cInternalFrames,  
      [out] ULONG32 *pcInternalFrames,  
      [in, out,size_is(cInternalFrames), length_is(*pcInternalFrames)]  
            ICorDebugInternalFrame2 * ppInternalFrames[]  
      );  
```  
  
## <a name="parameters"></a><span data-ttu-id="90a27-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="90a27-105">Parameters</span></span>  
 `cInternalFrames`  
 <span data-ttu-id="90a27-106">[v] Počet interních rámců `ppInternalFrames`očekávaných v .</span><span class="sxs-lookup"><span data-stu-id="90a27-106">[in] The number of internal frames expected in `ppInternalFrames`.</span></span>  
  
 `pcInternalFrames`  
 <span data-ttu-id="90a27-107">[out] Ukazatel na `ULONG32` a, který obsahuje počet vnitřních rámců v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="90a27-107">[out] A pointer to a `ULONG32` that contains the number of internal frames on the stack.</span></span>  
  
 `ppInternalFrames`  
 <span data-ttu-id="90a27-108">[dovnitř, ven] Ukazatel na adresu pole vnitřních rámců v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="90a27-108">[in, out] A pointer to the address of an array of internal frames on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="90a27-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="90a27-109">Return Value</span></span>  
 <span data-ttu-id="90a27-110">Tato metoda vrátí následující konkrétní HRESULTs, stejně jako HRESULT chyby, které označují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="90a27-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="90a27-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="90a27-111">HRESULT</span></span>|<span data-ttu-id="90a27-112">Popis</span><span class="sxs-lookup"><span data-stu-id="90a27-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="90a27-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="90a27-113">S_OK</span></span>|<span data-ttu-id="90a27-114">Objekt [ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) byl úspěšně vytvořen.</span><span class="sxs-lookup"><span data-stu-id="90a27-114">The [ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) object was successfully created.</span></span>|  
|<span data-ttu-id="90a27-115">E_invalidarg</span><span class="sxs-lookup"><span data-stu-id="90a27-115">E_INVALIDARG</span></span>|<span data-ttu-id="90a27-116">`cInternalFrames`není nula `ppInternalFrames` `null`a `pcInternalFrames` je `null`, nebo je .</span><span class="sxs-lookup"><span data-stu-id="90a27-116">`cInternalFrames` is not zero and `ppInternalFrames` is `null`, or `pcInternalFrames` is `null`.</span></span>|  
|<span data-ttu-id="90a27-117">HRESULT_FROM_WIN32 (ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="90a27-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="90a27-118">`ppInternalFrames`je menší než počet vnitřních rámců.</span><span class="sxs-lookup"><span data-stu-id="90a27-118">`ppInternalFrames` is smaller than the count of internal frames.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="90a27-119">Výjimky</span><span class="sxs-lookup"><span data-stu-id="90a27-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90a27-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="90a27-120">Remarks</span></span>  
 <span data-ttu-id="90a27-121">Vnitřní rámce jsou datové struktury posunuté do zásobníku za běhu pro ukládání dočasných dat.</span><span class="sxs-lookup"><span data-stu-id="90a27-121">Internal frames are data structures pushed onto the stack by the runtime to store temporary data.</span></span>  
  
 <span data-ttu-id="90a27-122">Při prvním `GetActiveInternalFrames`volání byste měli `cInternalFrames` nastavit parametr na 0 `ppInternalFrames` (nula) a parametr na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="90a27-122">When you first call `GetActiveInternalFrames`, you should set the `cInternalFrames` parameter to 0 (zero), and the `ppInternalFrames` parameter to null.</span></span> <span data-ttu-id="90a27-123">Při `GetActiveInternalFrames` prvním `pcInternalFrames` vrátí, obsahuje počet vnitřních rámců v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="90a27-123">When `GetActiveInternalFrames` first returns, `pcInternalFrames` contains the count of the internal frames on the stack.</span></span>  
  
 <span data-ttu-id="90a27-124">`GetActiveInternalFrames`by pak měl být volán podruhé.</span><span class="sxs-lookup"><span data-stu-id="90a27-124">`GetActiveInternalFrames` should then be called a second time.</span></span> <span data-ttu-id="90a27-125">Měli byste předat správný`pcInternalFrames`počet `cInternalFrames` ( ) v parametru a určit ukazatel `ppInternalFrames`na vhodně velké pole v .</span><span class="sxs-lookup"><span data-stu-id="90a27-125">You should pass the proper count (`pcInternalFrames`) in the `cInternalFrames` parameter, and specify a pointer to an appropriately sized array in `ppInternalFrames`.</span></span>  
  
 <span data-ttu-id="90a27-126">Použijte metodu [ICorDebugStackWalk::GetFrame](icordebugthread3-getactiveinternalframes-method.md) k vrácení skutečných rámců zásobníku.</span><span class="sxs-lookup"><span data-stu-id="90a27-126">Use the [ICorDebugStackWalk::GetFrame](icordebugthread3-getactiveinternalframes-method.md) method to return actual stack frames.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90a27-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="90a27-127">Requirements</span></span>  
 <span data-ttu-id="90a27-128">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90a27-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90a27-129">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="90a27-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="90a27-130">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="90a27-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90a27-131">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90a27-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90a27-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="90a27-132">See also</span></span>

- [<span data-ttu-id="90a27-133">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="90a27-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="90a27-134">ladění</span><span class="sxs-lookup"><span data-stu-id="90a27-134">Debugging</span></span>](index.md)
