---
title: "ICorDebugEval::GetResult – metoda"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7f3d17e28686d1697417dd380782b1f037e0b5a4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugevalgetresult-method"></a><span data-ttu-id="0b13e-102">ICorDebugEval::GetResult – metoda</span><span class="sxs-lookup"><span data-stu-id="0b13e-102">ICorDebugEval::GetResult Method</span></span>
<span data-ttu-id="0b13e-103">Získá výsledky tohoto hodnocení.</span><span class="sxs-lookup"><span data-stu-id="0b13e-103">Gets the results of this evaluation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b13e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0b13e-104">Syntax</span></span>  
  
```  
HRESULT GetResult (  
    [out] ICorDebugValue    **ppResult  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0b13e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0b13e-105">Parameters</span></span>  
 `ppResult`  
 <span data-ttu-id="0b13e-106">[out] Ukazatel na adresu ICorDebugValue objekt, který představuje výsledky tohoto hodnocení, pokud vyhodnocení dokončení normálně.</span><span class="sxs-lookup"><span data-stu-id="0b13e-106">[out] Pointer to the address of an ICorDebugValue object that represents the results of this evaluation, if the evaluation completes normally.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b13e-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0b13e-107">Remarks</span></span>  
 <span data-ttu-id="0b13e-108">`GetResult` Metoda je platná pouze po dokončení vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="0b13e-108">The `GetResult` method is valid only after the evaluation is completed.</span></span>  
  
 <span data-ttu-id="0b13e-109">Za normálních okolností dokončení vyhodnocení `ppResult` určuje výsledky.</span><span class="sxs-lookup"><span data-stu-id="0b13e-109">If the evaluation completes normally, `ppResult` specifies the results.</span></span> <span data-ttu-id="0b13e-110">Pokud ho ukončí s výjimkou, výsledkem je, že došlo k výjimce.</span><span class="sxs-lookup"><span data-stu-id="0b13e-110">If it terminates with an exception, the result is the exception thrown.</span></span> <span data-ttu-id="0b13e-111">Pokud pro nový objekt, který byl vyhodnocení, výsledkem je odkaz na nový objekt.</span><span class="sxs-lookup"><span data-stu-id="0b13e-111">If the evaluation was for a new object, the result is the reference to the new object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b13e-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0b13e-112">Requirements</span></span>  
 <span data-ttu-id="0b13e-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b13e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b13e-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0b13e-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0b13e-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0b13e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b13e-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b13e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
