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
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412575"
---
# <a name="icordebugeval2rudeabort-method"></a><span data-ttu-id="59089-102">ICorDebugEval2::RudeAbort – metoda</span><span class="sxs-lookup"><span data-stu-id="59089-102">ICorDebugEval2::RudeAbort Method</span></span>
<span data-ttu-id="59089-103">Zruší výpočet které tento `ICorDebugEval2` právě provádí.</span><span class="sxs-lookup"><span data-stu-id="59089-103">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59089-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59089-104">Syntax</span></span>  
  
```  
HRESULT RudeAbort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="59089-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="59089-105">Remarks</span></span>  
 <span data-ttu-id="59089-106">`RudeAbort` neuvolní žádné zámku, která obsahuje vyhodnocování, tak zůstanou relaci ladění ve stavu unsafe.</span><span class="sxs-lookup"><span data-stu-id="59089-106">`RudeAbort` does not release any locks that the evaluator holds, so it leaves the debugging session in an unsafe state.</span></span> <span data-ttu-id="59089-107">Volejte tuto metodu s velmi opatrní.</span><span class="sxs-lookup"><span data-stu-id="59089-107">Call this method with extreme caution.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59089-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="59089-108">Requirements</span></span>  
 <span data-ttu-id="59089-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59089-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59089-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="59089-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="59089-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="59089-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59089-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59089-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
