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
ms.openlocfilehash: 25cd3e05bc80dd39d2ca558bb4dd5fb77d255f5a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791398"
---
# <a name="icordebugthread3getactiveinternalframes-method"></a><span data-ttu-id="f82ca-102">ICorDebugThread3::GetActiveInternalFrames – metoda</span><span class="sxs-lookup"><span data-stu-id="f82ca-102">ICorDebugThread3::GetActiveInternalFrames Method</span></span>
<span data-ttu-id="f82ca-103">Vrátí pole vnitřních rámců (objektů[ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) ) v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="f82ca-103">Returns an array of internal frames ([ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) objects) on the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f82ca-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f82ca-104">Syntax</span></span>  
  
```cpp 
HRESULT GetActiveInternalFrames  
      (  
      [in] ULONG32 cInternalFrames,  
      [out] ULONG32 *pcInternalFrames,  
      [in, out,size_is(cInternalFrames), length_is(*pcInternalFrames)]  
            ICorDebugInternalFrame2 * ppInternalFrames[]  
      );  
```  
  
## <a name="parameters"></a><span data-ttu-id="f82ca-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f82ca-105">Parameters</span></span>  
 `cInternalFrames`  
 <span data-ttu-id="f82ca-106">pro Počet vnitřních snímků očekávaných v `ppInternalFrames`.</span><span class="sxs-lookup"><span data-stu-id="f82ca-106">[in] The number of internal frames expected in `ppInternalFrames`.</span></span>  
  
 `pcInternalFrames`  
 <span data-ttu-id="f82ca-107">mimo Ukazatel na `ULONG32`, který obsahuje počet vnitřních snímků v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="f82ca-107">[out] A pointer to a `ULONG32` that contains the number of internal frames on the stack.</span></span>  
  
 `ppInternalFrames`  
 <span data-ttu-id="f82ca-108">[in, out] Ukazatel na adresu pole vnitřních snímků v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="f82ca-108">[in, out] A pointer to the address of an array of internal frames on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f82ca-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f82ca-109">Return Value</span></span>  
 <span data-ttu-id="f82ca-110">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="f82ca-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="f82ca-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f82ca-111">HRESULT</span></span>|<span data-ttu-id="f82ca-112">Popis</span><span class="sxs-lookup"><span data-stu-id="f82ca-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f82ca-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="f82ca-113">S_OK</span></span>|<span data-ttu-id="f82ca-114">Objekt [ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) byl úspěšně vytvořen.</span><span class="sxs-lookup"><span data-stu-id="f82ca-114">The [ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) object was successfully created.</span></span>|  
|<span data-ttu-id="f82ca-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="f82ca-115">E_INVALIDARG</span></span>|<span data-ttu-id="f82ca-116">`cInternalFrames` není nula a `ppInternalFrames` je `null`nebo `pcInternalFrames` `null`.</span><span class="sxs-lookup"><span data-stu-id="f82ca-116">`cInternalFrames` is not zero and `ppInternalFrames` is `null`, or `pcInternalFrames` is `null`.</span></span>|  
|<span data-ttu-id="f82ca-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="f82ca-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="f82ca-118">`ppInternalFrames` je menší než počet vnitřních snímků.</span><span class="sxs-lookup"><span data-stu-id="f82ca-118">`ppInternalFrames` is smaller than the count of internal frames.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="f82ca-119">Výjimky</span><span class="sxs-lookup"><span data-stu-id="f82ca-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f82ca-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f82ca-120">Remarks</span></span>  
 <span data-ttu-id="f82ca-121">Interní snímky jsou datové struktury vložené do zásobníku modulem runtime k ukládání dočasných dat.</span><span class="sxs-lookup"><span data-stu-id="f82ca-121">Internal frames are data structures pushed onto the stack by the runtime to store temporary data.</span></span>  
  
 <span data-ttu-id="f82ca-122">Při prvním volání `GetActiveInternalFrames`byste měli nastavit parametr `cInternalFrames` na hodnotu 0 (nula) a parametr `ppInternalFrames` na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="f82ca-122">When you first call `GetActiveInternalFrames`, you should set the `cInternalFrames` parameter to 0 (zero), and the `ppInternalFrames` parameter to null.</span></span> <span data-ttu-id="f82ca-123">Když `GetActiveInternalFrames` první vrátí, `pcInternalFrames` obsahuje počet vnitřních snímků v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="f82ca-123">When `GetActiveInternalFrames` first returns, `pcInternalFrames` contains the count of the internal frames on the stack.</span></span>  
  
 <span data-ttu-id="f82ca-124">`GetActiveInternalFrames` by se měla volat podruhé.</span><span class="sxs-lookup"><span data-stu-id="f82ca-124">`GetActiveInternalFrames` should then be called a second time.</span></span> <span data-ttu-id="f82ca-125">V parametru `cInternalFrames` byste měli předat správný počet (`pcInternalFrames`) a určit ukazatel na pole odpovídající velikosti v `ppInternalFrames`.</span><span class="sxs-lookup"><span data-stu-id="f82ca-125">You should pass the proper count (`pcInternalFrames`) in the `cInternalFrames` parameter, and specify a pointer to an appropriately sized array in `ppInternalFrames`.</span></span>  
  
 <span data-ttu-id="f82ca-126">K vrácení skutečných rámců zásobníku použijte metodu [ICorDebugStackWalk:: GetFrame](icordebugthread3-getactiveinternalframes-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f82ca-126">Use the [ICorDebugStackWalk::GetFrame](icordebugthread3-getactiveinternalframes-method.md) method to return actual stack frames.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f82ca-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f82ca-127">Requirements</span></span>  
 <span data-ttu-id="f82ca-128">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f82ca-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f82ca-129">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f82ca-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f82ca-130">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f82ca-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f82ca-131">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f82ca-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f82ca-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f82ca-132">See also</span></span>

- [<span data-ttu-id="f82ca-133">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="f82ca-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="f82ca-134">Ladění</span><span class="sxs-lookup"><span data-stu-id="f82ca-134">Debugging</span></span>](index.md)
