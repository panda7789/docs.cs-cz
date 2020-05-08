---
title: ICorDebugEval::Abort – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval.Abort
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::Abort
helpviewer_keywords:
- Abort method, ICorDebugEval interface [.NET Framework debugging]
- ICorDebugEval::Abort method [.NET Framework debugging]
ms.assetid: 7070b6d0-f2e0-44ff-b124-0944cd807e69
topic_type:
- apiref
ms.openlocfilehash: 98a9b285323bc3ad94b4f555e72a4b3242519801
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976288"
---
# <a name="icordebugevalabort-method"></a><span data-ttu-id="cf411-102">ICorDebugEval::Abort – metoda</span><span class="sxs-lookup"><span data-stu-id="cf411-102">ICorDebugEval::Abort Method</span></span>
<span data-ttu-id="cf411-103">Přeruší výpočet, který tento objekt ICorDebugEval aktuálně provádí.</span><span class="sxs-lookup"><span data-stu-id="cf411-103">Aborts the computation this ICorDebugEval object is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf411-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cf411-104">Syntax</span></span>  
  
```cpp  
HRESULT Abort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="cf411-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cf411-105">Remarks</span></span>  
 <span data-ttu-id="cf411-106">Pokud je vyhodnocení vnořené a nejedná se o poslední z nich, `Abort` metoda může selhat.</span><span class="sxs-lookup"><span data-stu-id="cf411-106">If the evaluation is nested and it is not the most recent one, the `Abort` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf411-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cf411-107">Requirements</span></span>  
 <span data-ttu-id="cf411-108">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf411-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf411-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cf411-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cf411-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="cf411-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cf411-111">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf411-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
