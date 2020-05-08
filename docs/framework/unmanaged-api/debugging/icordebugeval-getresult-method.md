---
title: ICorDebugEval::GetResult – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval.GetResult
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::GetResult
helpviewer_keywords:
- ICorDebugEval::GetResult method [.NET Framework debugging]
- GetResult method [.NET Framework debugging]
ms.assetid: 50dbb9af-58a1-41f4-b56d-3da20011884f
topic_type:
- apiref
ms.openlocfilehash: 2d065d956319076d3b92eddafd4a2c25ffbfbac1
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976262"
---
# <a name="icordebugevalgetresult-method"></a><span data-ttu-id="efe47-102">ICorDebugEval::GetResult – metoda</span><span class="sxs-lookup"><span data-stu-id="efe47-102">ICorDebugEval::GetResult Method</span></span>
<span data-ttu-id="efe47-103">Získá výsledky tohoto vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="efe47-103">Gets the results of this evaluation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efe47-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="efe47-104">Syntax</span></span>  
  
```cpp  
HRESULT GetResult (  
    [out] ICorDebugValue    **ppResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="efe47-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="efe47-105">Parameters</span></span>  
 `ppResult`  
 <span data-ttu-id="efe47-106">mimo Ukazatel na adresu objektu ICorDebugValue, který představuje výsledky tohoto vyhodnocení, pokud se vyhodnocení dokončí normálně.</span><span class="sxs-lookup"><span data-stu-id="efe47-106">[out] Pointer to the address of an ICorDebugValue object that represents the results of this evaluation, if the evaluation completes normally.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="efe47-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="efe47-107">Remarks</span></span>  
 <span data-ttu-id="efe47-108">`GetResult` Metoda je platná až po dokončení vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="efe47-108">The `GetResult` method is valid only after the evaluation is completed.</span></span>  
  
 <span data-ttu-id="efe47-109">Pokud se vyhodnocení dokončí normálně `ppResult` , zadává výsledky.</span><span class="sxs-lookup"><span data-stu-id="efe47-109">If the evaluation completes normally, `ppResult` specifies the results.</span></span> <span data-ttu-id="efe47-110">Pokud se ukončí s výjimkou, výsledek je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="efe47-110">If it terminates with an exception, the result is the exception thrown.</span></span> <span data-ttu-id="efe47-111">Pokud bylo vyhodnocení nového objektu, výsledkem je odkaz na nový objekt.</span><span class="sxs-lookup"><span data-stu-id="efe47-111">If the evaluation was for a new object, the result is the reference to the new object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efe47-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="efe47-112">Requirements</span></span>  
 <span data-ttu-id="efe47-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="efe47-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efe47-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="efe47-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="efe47-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="efe47-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="efe47-116">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="efe47-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
