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
ms.openlocfilehash: b8e7fcb4f44d6bdf6f18c93b1046b549331621a4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667116"
---
# <a name="icordebugevalgetresult-method"></a><span data-ttu-id="b58fb-102">ICorDebugEval::GetResult – metoda</span><span class="sxs-lookup"><span data-stu-id="b58fb-102">ICorDebugEval::GetResult Method</span></span>
<span data-ttu-id="b58fb-103">Získá výsledky vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="b58fb-103">Gets the results of this evaluation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b58fb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b58fb-104">Syntax</span></span>  
  
```  
HRESULT GetResult (  
    [out] ICorDebugValue    **ppResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b58fb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b58fb-105">Parameters</span></span>  
 `ppResult`  
 <span data-ttu-id="b58fb-106">[out] Ukazatel na adresu ICorDebugValue objekt, který představuje výsledky hodnocení, pokud se obvykle dokončí hodnocení.</span><span class="sxs-lookup"><span data-stu-id="b58fb-106">[out] Pointer to the address of an ICorDebugValue object that represents the results of this evaluation, if the evaluation completes normally.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b58fb-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b58fb-107">Remarks</span></span>  
 <span data-ttu-id="b58fb-108">`GetResult` Metoda je platná, až po dokončení hodnocení.</span><span class="sxs-lookup"><span data-stu-id="b58fb-108">The `GetResult` method is valid only after the evaluation is completed.</span></span>  
  
 <span data-ttu-id="b58fb-109">Pokud se hodnocení dokončí za normálních okolností `ppResult` určuje výsledky.</span><span class="sxs-lookup"><span data-stu-id="b58fb-109">If the evaluation completes normally, `ppResult` specifies the results.</span></span> <span data-ttu-id="b58fb-110">Pokud je ukončena výjimku, výsledkem je výjimka vyvolána.</span><span class="sxs-lookup"><span data-stu-id="b58fb-110">If it terminates with an exception, the result is the exception thrown.</span></span> <span data-ttu-id="b58fb-111">Pokud je hodnocení pro nový objekt, výsledkem je odkaz na nový objekt.</span><span class="sxs-lookup"><span data-stu-id="b58fb-111">If the evaluation was for a new object, the result is the reference to the new object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b58fb-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b58fb-112">Requirements</span></span>  
 <span data-ttu-id="b58fb-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b58fb-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b58fb-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b58fb-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b58fb-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b58fb-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b58fb-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b58fb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
