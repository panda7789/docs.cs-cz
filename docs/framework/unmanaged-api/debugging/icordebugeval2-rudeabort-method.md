---
title: ICorDebugEval2::RudeAbort – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.RudeAbort
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::RudeAbort
helpviewer_keywords:
- ICorDebugEval2::RudeAbort method [.NET Framework debugging]
- RudeAbort method, ICorDebugEval2 interface [.NET Framework debugging]
ms.assetid: 02468edf-d32b-4cb3-aaa8-3dd2abfc8b25
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0aabff090634f1ecdeec5636336ad1fb77b8b81c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988920"
---
# <a name="icordebugeval2rudeabort-method"></a><span data-ttu-id="83efe-102">ICorDebugEval2::RudeAbort – metoda</span><span class="sxs-lookup"><span data-stu-id="83efe-102">ICorDebugEval2::RudeAbort Method</span></span>
<span data-ttu-id="83efe-103">Zruší výpočet, který tato `ICorDebugEval2` v tuto chvíli provádí.</span><span class="sxs-lookup"><span data-stu-id="83efe-103">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83efe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83efe-104">Syntax</span></span>  
  
```  
HRESULT RudeAbort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="83efe-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="83efe-105">Remarks</span></span>  
 <span data-ttu-id="83efe-106">`RudeAbort` neuvolní žádné zámky, které obsahuje Chyba při vyhodnocování, tak se relace ladění zůstane ve stavu unsafe.</span><span class="sxs-lookup"><span data-stu-id="83efe-106">`RudeAbort` does not release any locks that the evaluator holds, so it leaves the debugging session in an unsafe state.</span></span> <span data-ttu-id="83efe-107">Volání této metody s nejvyšší opatrností.</span><span class="sxs-lookup"><span data-stu-id="83efe-107">Call this method with extreme caution.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83efe-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="83efe-108">Requirements</span></span>  
 <span data-ttu-id="83efe-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83efe-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83efe-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="83efe-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="83efe-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83efe-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83efe-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83efe-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
