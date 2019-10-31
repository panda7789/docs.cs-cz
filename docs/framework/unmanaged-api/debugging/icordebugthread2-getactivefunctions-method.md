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
ms.openlocfilehash: 9b9a301714ea60b4e3220eb75721e56e39bd9659
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139931"
---
# <a name="icordebugthread2getactivefunctions-method"></a><span data-ttu-id="0e953-102">ICorDebugThread2::GetActiveFunctions – metoda</span><span class="sxs-lookup"><span data-stu-id="0e953-102">ICorDebugThread2::GetActiveFunctions Method</span></span>
<span data-ttu-id="0e953-103">Načte informace o aktivní funkci v každém z rámců tohoto vlákna.</span><span class="sxs-lookup"><span data-stu-id="0e953-103">Gets information about the active function in each of this thread's frames.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e953-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0e953-104">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveFunctions (  
    [in]   ULONG32             cFunctions,  
    [out]  ULONG32             *pcFunctions,  
    [in, out, size_is(cFunctions), length_is(*pcFunctions)]  
        COR_ACTIVE_FUNCTION    pFunctions[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e953-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0e953-105">Parameters</span></span>  
 `cFunctions`  
 <span data-ttu-id="0e953-106">pro Velikost pole `pFunctions`.</span><span class="sxs-lookup"><span data-stu-id="0e953-106">[in] The size of the `pFunctions` array.</span></span>  
  
 `pcFunctions`  
 <span data-ttu-id="0e953-107">mimo Ukazatel na počet objektů vrácených v poli `pFunctions`.</span><span class="sxs-lookup"><span data-stu-id="0e953-107">[out] A pointer to the number of objects returned in the `pFunctions` array.</span></span> <span data-ttu-id="0e953-108">Počet vrácených objektů bude roven počtu spravovaných snímků v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="0e953-108">The number of objects returned will be equal to the number of managed frames on the stack.</span></span>  
  
 `pFunctions`  
 <span data-ttu-id="0e953-109">[in, out] Pole objektů COR_ACTIVE_FUNCTION, z nichž každá obsahuje informace o aktivních funkcích v rámečcích tohoto vlákna.</span><span class="sxs-lookup"><span data-stu-id="0e953-109">[in, out] An array of COR_ACTIVE_FUNCTION objects, each of which contains information about the active functions in this thread's frames.</span></span>  
  
 <span data-ttu-id="0e953-110">První prvek bude použit pro listový rámec a tak dále zpět do kořenového adresáře zásobníku.</span><span class="sxs-lookup"><span data-stu-id="0e953-110">The first element will be used for the leaf frame, and so on back to the root of the stack.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0e953-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0e953-111">Remarks</span></span>  
 <span data-ttu-id="0e953-112">Pokud je u vstupu `pFunctions` null, `GetActiveFunctions` vrátí pouze počet funkcí, které jsou v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="0e953-112">If `pFunctions` is null on input, `GetActiveFunctions` returns only the number of functions that are on the stack.</span></span> <span data-ttu-id="0e953-113">To znamená, že pokud `pFunctions` pro vstup hodnotu null, `GetActiveFunctions` vrátí hodnotu pouze v `pcFunctions`.</span><span class="sxs-lookup"><span data-stu-id="0e953-113">That is, If `pFunctions` is null on input, `GetActiveFunctions` returns a value only in `pcFunctions`.</span></span>  
  
 <span data-ttu-id="0e953-114">Metoda `GetActiveFunctions` je určena jako optimalizace při získávání stejných informací z snímků v trasování zásobníku a zahrnuje pouze rámce, které by měly mít pro sebe objekt ICorDebugILFrame v plném trasování zásobníku.</span><span class="sxs-lookup"><span data-stu-id="0e953-114">The `GetActiveFunctions` method is intended as an optimization over getting the same information from frames in a stack trace, and includes only frames that would have had an ICorDebugILFrame object for them in the full stack trace.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e953-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0e953-115">Requirements</span></span>  
 <span data-ttu-id="0e953-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e953-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e953-117">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0e953-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0e953-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0e953-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0e953-119">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e953-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
