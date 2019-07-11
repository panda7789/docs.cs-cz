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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b12ba5ad5c85643d1f4c91585cf7abca210d22bd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752937"
---
# <a name="icordebugevalgetresult-method"></a><span data-ttu-id="42aa2-102">ICorDebugEval::GetResult – metoda</span><span class="sxs-lookup"><span data-stu-id="42aa2-102">ICorDebugEval::GetResult Method</span></span>
<span data-ttu-id="42aa2-103">Získá výsledky vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="42aa2-103">Gets the results of this evaluation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42aa2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42aa2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetResult (  
    [out] ICorDebugValue    **ppResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42aa2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="42aa2-105">Parameters</span></span>  
 `ppResult`  
 <span data-ttu-id="42aa2-106">[out] Ukazatel na adresu ICorDebugValue objekt, který představuje výsledky hodnocení, pokud se obvykle dokončí hodnocení.</span><span class="sxs-lookup"><span data-stu-id="42aa2-106">[out] Pointer to the address of an ICorDebugValue object that represents the results of this evaluation, if the evaluation completes normally.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42aa2-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="42aa2-107">Remarks</span></span>  
 <span data-ttu-id="42aa2-108">`GetResult` Metoda je platná, až po dokončení hodnocení.</span><span class="sxs-lookup"><span data-stu-id="42aa2-108">The `GetResult` method is valid only after the evaluation is completed.</span></span>  
  
 <span data-ttu-id="42aa2-109">Pokud se hodnocení dokončí za normálních okolností `ppResult` určuje výsledky.</span><span class="sxs-lookup"><span data-stu-id="42aa2-109">If the evaluation completes normally, `ppResult` specifies the results.</span></span> <span data-ttu-id="42aa2-110">Pokud je ukončena výjimku, výsledkem je výjimka vyvolána.</span><span class="sxs-lookup"><span data-stu-id="42aa2-110">If it terminates with an exception, the result is the exception thrown.</span></span> <span data-ttu-id="42aa2-111">Pokud je hodnocení pro nový objekt, výsledkem je odkaz na nový objekt.</span><span class="sxs-lookup"><span data-stu-id="42aa2-111">If the evaluation was for a new object, the result is the reference to the new object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42aa2-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="42aa2-112">Requirements</span></span>  
 <span data-ttu-id="42aa2-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42aa2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42aa2-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="42aa2-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="42aa2-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="42aa2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42aa2-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42aa2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
