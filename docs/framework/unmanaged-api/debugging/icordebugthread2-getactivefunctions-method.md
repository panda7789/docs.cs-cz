---
title: "ICorDebugThread2::GetActiveFunctions – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugThread2.GetActiveFunctions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetActiveFunctions
helpviewer_keywords:
- GetActiveFunctions method [.NET Framework debugging]
- ICorDebugThread2::GetActiveFunctions method [.NET Framework debugging]
ms.assetid: 27fae01a-ecec-423a-973e-24f8de55826c
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ecd9446f642011b21f784019f583f49e3a70433a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthread2getactivefunctions-method"></a><span data-ttu-id="958c3-102">ICorDebugThread2::GetActiveFunctions – metoda</span><span class="sxs-lookup"><span data-stu-id="958c3-102">ICorDebugThread2::GetActiveFunctions Method</span></span>
<span data-ttu-id="958c3-103">Získá informace o funkci active v každé z tohoto podprocesu rámce.</span><span class="sxs-lookup"><span data-stu-id="958c3-103">Gets information about the active function in each of this thread's frames.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="958c3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="958c3-104">Syntax</span></span>  
  
```  
HRESULT GetActiveFunctions (  
    [in]   ULONG32             cFunctions,  
    [out]  ULONG32             *pcFunctions,  
    [in, out, size_is(cFunctions), length_is(*pcFunctions)]  
        COR_ACTIVE_FUNCTION    pFunctions[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="958c3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="958c3-105">Parameters</span></span>  
 `cFunctions`  
 <span data-ttu-id="958c3-106">[v] Velikost `pFunctions` pole.</span><span class="sxs-lookup"><span data-stu-id="958c3-106">[in] The size of the `pFunctions` array.</span></span>  
  
 `pcFunctions`  
 <span data-ttu-id="958c3-107">[out] Ukazatel na počet objektů vrácený v `pFunctions` pole.</span><span class="sxs-lookup"><span data-stu-id="958c3-107">[out] A pointer to the number of objects returned in the `pFunctions` array.</span></span> <span data-ttu-id="958c3-108">Počet vrácených objektů bude rovnat počtu spravovaných rámce v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="958c3-108">The number of objects returned will be equal to the number of managed frames on the stack.</span></span>  
  
 `pFunctions`  
 <span data-ttu-id="958c3-109">[ve out] Pole objektů cor_active_function –, z nichž každý obsahuje informace o active funkcí v tohoto podprocesu rámce.</span><span class="sxs-lookup"><span data-stu-id="958c3-109">[in, out] An array of COR_ACTIVE_FUNCTION objects, each of which contains information about the active functions in this thread's frames.</span></span>  
  
 <span data-ttu-id="958c3-110">První prvek se použije pro rámce typu list a tak dále zpět do kořenového adresáře zásobníku.</span><span class="sxs-lookup"><span data-stu-id="958c3-110">The first element will be used for the leaf frame, and so on back to the root of the stack.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="958c3-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="958c3-111">Remarks</span></span>  
 <span data-ttu-id="958c3-112">Pokud `pFunctions` má hodnotu null na vstupu `GetActiveFunctions` vrátí pouze počet funkcí, které jsou v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="958c3-112">If `pFunctions` is null on input, `GetActiveFunctions` returns only the number of functions that are on the stack.</span></span> <span data-ttu-id="958c3-113">To znamená pokud `pFunctions` má hodnotu null na vstupu `GetActiveFunctions` vrací hodnotu pouze v `pcFunctions`.</span><span class="sxs-lookup"><span data-stu-id="958c3-113">That is, If `pFunctions` is null on input, `GetActiveFunctions` returns a value only in `pcFunctions`.</span></span>  
  
 <span data-ttu-id="958c3-114">`GetActiveFunctions` Metoda slouží jako optimalizace přes získávání stejné informace z rámce v trasování zásobníku a obsahuje pouze rámce, které by neměly mít objekt ICorDebugILFrame pro ně v trasování zásobníku úplné.</span><span class="sxs-lookup"><span data-stu-id="958c3-114">The `GetActiveFunctions` method is intended as an optimization over getting the same information from frames in a stack trace, and includes only frames that would have had an ICorDebugILFrame object for them in the full stack trace.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="958c3-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="958c3-115">Requirements</span></span>  
 <span data-ttu-id="958c3-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="958c3-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="958c3-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="958c3-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="958c3-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="958c3-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="958c3-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="958c3-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
