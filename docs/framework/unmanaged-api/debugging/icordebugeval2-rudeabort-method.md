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
ms.openlocfilehash: a486935d5d53a6fc7d862160ed1186c5774814c7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084800"
---
# <a name="icordebugeval2rudeabort-method"></a><span data-ttu-id="641c4-102">ICorDebugEval2::RudeAbort – metoda</span><span class="sxs-lookup"><span data-stu-id="641c4-102">ICorDebugEval2::RudeAbort Method</span></span>
<span data-ttu-id="641c4-103">Přeruší výpočet, který tato `ICorDebugEval2` v tuto chvíli provádí.</span><span class="sxs-lookup"><span data-stu-id="641c4-103">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="641c4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="641c4-104">Syntax</span></span>  
  
```cpp  
HRESULT RudeAbort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="641c4-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="641c4-105">Remarks</span></span>  
 <span data-ttu-id="641c4-106">`RudeAbort` neuvolní žádné zámky, které filtr uchovává, takže relace ladění zůstane v nezabezpečeném stavu.</span><span class="sxs-lookup"><span data-stu-id="641c4-106">`RudeAbort` does not release any locks that the evaluator holds, so it leaves the debugging session in an unsafe state.</span></span> <span data-ttu-id="641c4-107">Zavolejte tuto metodu s mimořádnou opatrností.</span><span class="sxs-lookup"><span data-stu-id="641c4-107">Call this method with extreme caution.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="641c4-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="641c4-108">Requirements</span></span>  
 <span data-ttu-id="641c4-109">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="641c4-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="641c4-110">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="641c4-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="641c4-111">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="641c4-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="641c4-112">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="641c4-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
