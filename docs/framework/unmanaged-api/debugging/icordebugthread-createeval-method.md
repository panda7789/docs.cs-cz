---
title: "ICorDebugThread::CreateEval – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.CreateEval
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::CreateEval
helpviewer_keywords:
- CreateEval method [.NET Framework debugging]
- ICorDebugThread::CreateEval method [.NET Framework debugging]
ms.assetid: 36605067-33d3-4579-9c72-fb0e551ab0f1
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 766677d9eef60c811c8537bc60bb8db29dd988c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthreadcreateeval-method"></a><span data-ttu-id="0a85f-102">ICorDebugThread::CreateEval – metoda</span><span class="sxs-lookup"><span data-stu-id="0a85f-102">ICorDebugThread::CreateEval Method</span></span>
<span data-ttu-id="0a85f-103">Vytvoří objekt ICorDebugEval, který shromažďuje a zveřejňuje funkce této ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="0a85f-103">Creates an ICorDebugEval object that collects and exposes the functionality of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a85f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0a85f-104">Syntax</span></span>  
  
```  
HRESULT CreateEval (  
    [out] ICorDebugEval   **ppEval  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0a85f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0a85f-105">Parameters</span></span>  
 `ppEval`  
 <span data-ttu-id="0a85f-106">[out] Ukazatel na adresu `ICorDebugEval` objekt, který shromažďuje a zveřejňuje funkce z tohoto podprocesu.</span><span class="sxs-lookup"><span data-stu-id="0a85f-106">[out] A pointer to the address of an `ICorDebugEval` object that collects and exposes the functionality of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0a85f-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0a85f-107">Remarks</span></span>  
 <span data-ttu-id="0a85f-108">Objekt vyhodnocení předá řetěz nový ve vlákně před provedením jeho výpočtu.</span><span class="sxs-lookup"><span data-stu-id="0a85f-108">The evaluation object will push a new chain on the thread before doing its computation.</span></span> <span data-ttu-id="0a85f-109">Přeruší výpočet právě provádí na vlákno až do dokončení vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="0a85f-109">This interrupts the computation currently being performed on the thread until the evaluation completes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a85f-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0a85f-110">Requirements</span></span>  
 <span data-ttu-id="0a85f-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a85f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a85f-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0a85f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0a85f-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0a85f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0a85f-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a85f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
