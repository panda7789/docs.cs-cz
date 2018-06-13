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
ms.openlocfilehash: 5e2d99d85a6e6b09558e5941d08a7f522aaf66cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421814"
---
# <a name="icordebugthreadcreateeval-method"></a><span data-ttu-id="482b0-102">ICorDebugThread::CreateEval – metoda</span><span class="sxs-lookup"><span data-stu-id="482b0-102">ICorDebugThread::CreateEval Method</span></span>
<span data-ttu-id="482b0-103">Vytvoří objekt ICorDebugEval, který shromažďuje a zveřejňuje funkce této ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="482b0-103">Creates an ICorDebugEval object that collects and exposes the functionality of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="482b0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="482b0-104">Syntax</span></span>  
  
```  
HRESULT CreateEval (  
    [out] ICorDebugEval   **ppEval  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="482b0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="482b0-105">Parameters</span></span>  
 `ppEval`  
 <span data-ttu-id="482b0-106">[out] Ukazatel na adresu `ICorDebugEval` objekt, který shromažďuje a zveřejňuje funkce z tohoto podprocesu.</span><span class="sxs-lookup"><span data-stu-id="482b0-106">[out] A pointer to the address of an `ICorDebugEval` object that collects and exposes the functionality of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="482b0-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="482b0-107">Remarks</span></span>  
 <span data-ttu-id="482b0-108">Objekt vyhodnocení předá řetěz nový ve vlákně před provedením jeho výpočtu.</span><span class="sxs-lookup"><span data-stu-id="482b0-108">The evaluation object will push a new chain on the thread before doing its computation.</span></span> <span data-ttu-id="482b0-109">Přeruší výpočet právě provádí na vlákno až do dokončení vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="482b0-109">This interrupts the computation currently being performed on the thread until the evaluation completes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="482b0-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="482b0-110">Requirements</span></span>  
 <span data-ttu-id="482b0-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="482b0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="482b0-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="482b0-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="482b0-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="482b0-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="482b0-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="482b0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
