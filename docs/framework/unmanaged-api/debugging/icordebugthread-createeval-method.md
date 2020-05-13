---
title: ICorDebugThread::CreateEval – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.CreateEval
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::CreateEval
helpviewer_keywords:
- CreateEval method [.NET Framework debugging]
- ICorDebugThread::CreateEval method [.NET Framework debugging]
ms.assetid: 36605067-33d3-4579-9c72-fb0e551ab0f1
topic_type:
- apiref
ms.openlocfilehash: f66ef88646c314502dcb610cec8ce822cab1fca2
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379286"
---
# <a name="icordebugthreadcreateeval-method"></a><span data-ttu-id="a8990-102">ICorDebugThread::CreateEval – metoda</span><span class="sxs-lookup"><span data-stu-id="a8990-102">ICorDebugThread::CreateEval Method</span></span>
<span data-ttu-id="a8990-103">Vytvoří objekt ICorDebugEval, který shromažďuje a zpřístupňuje funkce tohoto ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="a8990-103">Creates an ICorDebugEval object that collects and exposes the functionality of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8990-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a8990-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateEval (  
    [out] ICorDebugEval   **ppEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8990-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a8990-105">Parameters</span></span>  
 `ppEval`  
 <span data-ttu-id="a8990-106">mimo Ukazatel na adresu `ICorDebugEval` objektu, který shromažďuje a zpřístupňuje funkce tohoto vlákna.</span><span class="sxs-lookup"><span data-stu-id="a8990-106">[out] A pointer to the address of an `ICorDebugEval` object that collects and exposes the functionality of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8990-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a8990-107">Remarks</span></span>  
 <span data-ttu-id="a8990-108">Objekt vyhodnocení před provedením výpočtu napředá do vlákna nový řetěz.</span><span class="sxs-lookup"><span data-stu-id="a8990-108">The evaluation object will push a new chain on the thread before doing its computation.</span></span> <span data-ttu-id="a8990-109">Tím se přeruší výpočet, který se právě provádí ve vlákně, dokud se nedokončí vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="a8990-109">This interrupts the computation currently being performed on the thread until the evaluation completes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8990-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a8990-110">Requirements</span></span>  
 <span data-ttu-id="a8990-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8990-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8990-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a8990-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a8990-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a8990-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8990-114">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8990-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
