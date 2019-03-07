---
title: ICorDebugThread2::GetActiveFunctions – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed13f78d5a1f6d54b12c86613715f4878a521bfa
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489927"
---
# <a name="icordebugthread2getactivefunctions-method"></a><span data-ttu-id="c2231-102">ICorDebugThread2::GetActiveFunctions – metoda</span><span class="sxs-lookup"><span data-stu-id="c2231-102">ICorDebugThread2::GetActiveFunctions Method</span></span>
<span data-ttu-id="c2231-103">Získá informace o funkci aktivní ve všech snímků toto vlákno.</span><span class="sxs-lookup"><span data-stu-id="c2231-103">Gets information about the active function in each of this thread's frames.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2231-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c2231-104">Syntax</span></span>  
  
```  
HRESULT GetActiveFunctions (  
    [in]   ULONG32             cFunctions,  
    [out]  ULONG32             *pcFunctions,  
    [in, out, size_is(cFunctions), length_is(*pcFunctions)]  
        COR_ACTIVE_FUNCTION    pFunctions[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2231-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c2231-105">Parameters</span></span>  
 `cFunctions`  
 <span data-ttu-id="c2231-106">[in] Velikost `pFunctions` pole.</span><span class="sxs-lookup"><span data-stu-id="c2231-106">[in] The size of the `pFunctions` array.</span></span>  
  
 `pcFunctions`  
 <span data-ttu-id="c2231-107">[out] Ukazatel na počet objektů vrácených v `pFunctions` pole.</span><span class="sxs-lookup"><span data-stu-id="c2231-107">[out] A pointer to the number of objects returned in the `pFunctions` array.</span></span> <span data-ttu-id="c2231-108">Počet objektů vrácených bude rovnat počtu spravovaných rámců v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="c2231-108">The number of objects returned will be equal to the number of managed frames on the stack.</span></span>  
  
 `pFunctions`  
 <span data-ttu-id="c2231-109">[out v] Pole objektů cor_active_function –, z nichž každý obsahuje informace o funkcích aktivní v rámcích toto vlákno.</span><span class="sxs-lookup"><span data-stu-id="c2231-109">[in, out] An array of COR_ACTIVE_FUNCTION objects, each of which contains information about the active functions in this thread's frames.</span></span>  
  
 <span data-ttu-id="c2231-110">První prvek se použije pro než pro rámce a tak dále zpět do kořenového adresáře do zásobníku.</span><span class="sxs-lookup"><span data-stu-id="c2231-110">The first element will be used for the leaf frame, and so on back to the root of the stack.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2231-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c2231-111">Remarks</span></span>  
 <span data-ttu-id="c2231-112">Pokud `pFunctions` má hodnotu null na vstupu `GetActiveFunctions` vrátí počet funkcí, které jsou v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="c2231-112">If `pFunctions` is null on input, `GetActiveFunctions` returns only the number of functions that are on the stack.</span></span> <span data-ttu-id="c2231-113">To znamená pokud `pFunctions` má hodnotu null na vstupu `GetActiveFunctions` vrací hodnotu pouze v `pcFunctions`.</span><span class="sxs-lookup"><span data-stu-id="c2231-113">That is, If `pFunctions` is null on input, `GetActiveFunctions` returns a value only in `pcFunctions`.</span></span>  
  
 <span data-ttu-id="c2231-114">`GetActiveFunctions` Metody slouží jako optimalizace za získání stejných informací z rámců v zásobníku a obsahuje pouze rámce, které by měly objekt ICorDebugILFrame jejich úplné trasování zásobníku.</span><span class="sxs-lookup"><span data-stu-id="c2231-114">The `GetActiveFunctions` method is intended as an optimization over getting the same information from frames in a stack trace, and includes only frames that would have had an ICorDebugILFrame object for them in the full stack trace.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2231-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c2231-115">Requirements</span></span>  
 <span data-ttu-id="c2231-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2231-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2231-117">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c2231-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c2231-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2231-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2231-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2231-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
