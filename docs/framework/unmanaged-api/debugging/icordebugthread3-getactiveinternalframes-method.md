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
ms.openlocfilehash: 953b7c1cb5e471072776fe03e53a46d3ff19c0ac
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379854"
---
# <a name="icordebugthread3getactiveinternalframes-method"></a><span data-ttu-id="0bf0f-102">ICorDebugThread3::GetActiveInternalFrames – metoda</span><span class="sxs-lookup"><span data-stu-id="0bf0f-102">ICorDebugThread3::GetActiveInternalFrames Method</span></span>
<span data-ttu-id="0bf0f-103">Vrátí pole vnitřních rámců (objektů[ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) ) v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="0bf0f-103">Returns an array of internal frames ([ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) objects) on the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bf0f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0bf0f-104">Syntax</span></span>  
  
```cpp
HRESULT GetActiveInternalFrames  
      (  
      [in] ULONG32 cInternalFrames,  
      [out] ULONG32 *pcInternalFrames,  
      [in, out,size_is(cInternalFrames), length_is(*pcInternalFrames)]  
            ICorDebugInternalFrame2 * ppInternalFrames[]  
      );  
```  
  
## <a name="parameters"></a><span data-ttu-id="0bf0f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0bf0f-105">Parameters</span></span>  
 `cInternalFrames`  
 <span data-ttu-id="0bf0f-106">pro Počet vnitřních rámců očekávaných v `ppInternalFrames` .</span><span class="sxs-lookup"><span data-stu-id="0bf0f-106">[in] The number of internal frames expected in `ppInternalFrames`.</span></span>  
  
 `pcInternalFrames`  
 <span data-ttu-id="0bf0f-107">mimo Ukazatel na `ULONG32` , který obsahuje počet vnitřních snímků v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="0bf0f-107">[out] A pointer to a `ULONG32` that contains the number of internal frames on the stack.</span></span>  
  
 `ppInternalFrames`  
 <span data-ttu-id="0bf0f-108">[in, out] Ukazatel na adresu pole vnitřních snímků v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="0bf0f-108">[in, out] A pointer to the address of an array of internal frames on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0bf0f-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0bf0f-109">Return Value</span></span>  
 <span data-ttu-id="0bf0f-110">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="0bf0f-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="0bf0f-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0bf0f-111">HRESULT</span></span>|<span data-ttu-id="0bf0f-112">Popis</span><span class="sxs-lookup"><span data-stu-id="0bf0f-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0bf0f-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="0bf0f-113">S_OK</span></span>|<span data-ttu-id="0bf0f-114">Objekt [ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) byl úspěšně vytvořen.</span><span class="sxs-lookup"><span data-stu-id="0bf0f-114">The [ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) object was successfully created.</span></span>|  
|<span data-ttu-id="0bf0f-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="0bf0f-115">E_INVALIDARG</span></span>|<span data-ttu-id="0bf0f-116">`cInternalFrames`není nula a `ppInternalFrames` je `null` nebo `pcInternalFrames` `null` .</span><span class="sxs-lookup"><span data-stu-id="0bf0f-116">`cInternalFrames` is not zero and `ppInternalFrames` is `null`, or `pcInternalFrames` is `null`.</span></span>|  
|<span data-ttu-id="0bf0f-117">HRESULT_FROM_WIN32 (ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="0bf0f-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="0bf0f-118">`ppInternalFrames`je menší než počet vnitřních snímků.</span><span class="sxs-lookup"><span data-stu-id="0bf0f-118">`ppInternalFrames` is smaller than the count of internal frames.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="0bf0f-119">Výjimky</span><span class="sxs-lookup"><span data-stu-id="0bf0f-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0bf0f-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0bf0f-120">Remarks</span></span>  
 <span data-ttu-id="0bf0f-121">Interní snímky jsou datové struktury vložené do zásobníku modulem runtime k ukládání dočasných dat.</span><span class="sxs-lookup"><span data-stu-id="0bf0f-121">Internal frames are data structures pushed onto the stack by the runtime to store temporary data.</span></span>  
  
 <span data-ttu-id="0bf0f-122">Při prvním volání `GetActiveInternalFrames` byste měli nastavit `cInternalFrames` parametr na hodnotu 0 (nula) a `ppInternalFrames` parametr na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="0bf0f-122">When you first call `GetActiveInternalFrames`, you should set the `cInternalFrames` parameter to 0 (zero), and the `ppInternalFrames` parameter to null.</span></span> <span data-ttu-id="0bf0f-123">Při `GetActiveInternalFrames` prvním návratu `pcInternalFrames` obsahuje počet vnitřních snímků v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="0bf0f-123">When `GetActiveInternalFrames` first returns, `pcInternalFrames` contains the count of the internal frames on the stack.</span></span>  
  
 <span data-ttu-id="0bf0f-124">`GetActiveInternalFrames`by se pak mělo volat podruhé.</span><span class="sxs-lookup"><span data-stu-id="0bf0f-124">`GetActiveInternalFrames` should then be called a second time.</span></span> <span data-ttu-id="0bf0f-125">V parametru byste měli předat správný počet ( `pcInternalFrames` ) `cInternalFrames` a zadat ukazatel na pole odpovídající velikosti v `ppInternalFrames` .</span><span class="sxs-lookup"><span data-stu-id="0bf0f-125">You should pass the proper count (`pcInternalFrames`) in the `cInternalFrames` parameter, and specify a pointer to an appropriately sized array in `ppInternalFrames`.</span></span>  
  
 <span data-ttu-id="0bf0f-126">K vrácení skutečných rámců zásobníku použijte metodu [ICorDebugStackWalk:: GetFrame](icordebugthread3-getactiveinternalframes-method.md) .</span><span class="sxs-lookup"><span data-stu-id="0bf0f-126">Use the [ICorDebugStackWalk::GetFrame](icordebugthread3-getactiveinternalframes-method.md) method to return actual stack frames.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0bf0f-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0bf0f-127">Requirements</span></span>  
 <span data-ttu-id="0bf0f-128">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0bf0f-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0bf0f-129">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0bf0f-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0bf0f-130">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0bf0f-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0bf0f-131">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0bf0f-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bf0f-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="0bf0f-132">See also</span></span>

- [<span data-ttu-id="0bf0f-133">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0bf0f-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="0bf0f-134">Ladění</span><span class="sxs-lookup"><span data-stu-id="0bf0f-134">Debugging</span></span>](index.md)
