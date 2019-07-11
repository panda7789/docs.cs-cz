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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 41bd4c0bb4e84b6d6f267e24808baafa57f71882
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771118"
---
# <a name="icordebugthreadcreateeval-method"></a><span data-ttu-id="ee84b-102">ICorDebugThread::CreateEval – metoda</span><span class="sxs-lookup"><span data-stu-id="ee84b-102">ICorDebugThread::CreateEval Method</span></span>
<span data-ttu-id="ee84b-103">Vytvoří objekt icordebugeval –, který shromažďuje a zveřejňuje funkce tento ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="ee84b-103">Creates an ICorDebugEval object that collects and exposes the functionality of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee84b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ee84b-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateEval (  
    [out] ICorDebugEval   **ppEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ee84b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ee84b-105">Parameters</span></span>  
 `ppEval`  
 <span data-ttu-id="ee84b-106">[out] Ukazatel na adresu `ICorDebugEval` objekt, který shromažďuje a zveřejňuje funkce pro toto vlákno.</span><span class="sxs-lookup"><span data-stu-id="ee84b-106">[out] A pointer to the address of an `ICorDebugEval` object that collects and exposes the functionality of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ee84b-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ee84b-107">Remarks</span></span>  
 <span data-ttu-id="ee84b-108">Objekt vyhodnocení zařadí nový řetězec ve vlákně než přistoupíte k jeho výpočtu.</span><span class="sxs-lookup"><span data-stu-id="ee84b-108">The evaluation object will push a new chain on the thread before doing its computation.</span></span> <span data-ttu-id="ee84b-109">Přeruší se výpočet aktuálně se provést ve vlákně, dokud se nedokončí hodnocení.</span><span class="sxs-lookup"><span data-stu-id="ee84b-109">This interrupts the computation currently being performed on the thread until the evaluation completes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee84b-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ee84b-110">Requirements</span></span>  
 <span data-ttu-id="ee84b-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee84b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee84b-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ee84b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ee84b-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ee84b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee84b-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee84b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
