---
title: ICorDebugThread2::GetTaskID – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetTaskID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetTaskID
helpviewer_keywords:
- ICorDebugThread2::GetTaskID method [.NET Framework debugging]
- GetTaskID method [.NET Framework debugging]
ms.assetid: 6ba3c6ee-4ba1-4c98-bf1e-8531acd3da09
topic_type:
- apiref
ms.openlocfilehash: d5f2838007504e56ad44614a6778083be046629f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140082"
---
# <a name="icordebugthread2gettaskid-method"></a><span data-ttu-id="7413c-102">ICorDebugThread2::GetTaskID – metoda</span><span class="sxs-lookup"><span data-stu-id="7413c-102">ICorDebugThread2::GetTaskID Method</span></span>
<span data-ttu-id="7413c-103">Získá identifikátor úlohy spuštěné v tomto vlákně.</span><span class="sxs-lookup"><span data-stu-id="7413c-103">Gets the identifier of the task running on this thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7413c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7413c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTaskID (  
    [out] TASKID  *pTaskId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7413c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7413c-105">Parameters</span></span>  
 `pTaskId`  
 <span data-ttu-id="7413c-106">mimo Ukazatel na identifikátor úlohy spuštěné ve vlákně reprezentované tímto objektem ICorDebugThread2.</span><span class="sxs-lookup"><span data-stu-id="7413c-106">[out] A pointer to the identifier of the task running on the thread represented by this ICorDebugThread2 object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7413c-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7413c-107">Remarks</span></span>  
 <span data-ttu-id="7413c-108">Úloha může být spuštěna pouze ve vlákně, pokud je vlákno přidruženo k připojení.</span><span class="sxs-lookup"><span data-stu-id="7413c-108">A task can only be running on the thread if the thread is associated with a connection.</span></span> <span data-ttu-id="7413c-109">`GetTaskID` vrátí nulu v `pTaskId`, pokud vlákno není přidruženo k připojení.</span><span class="sxs-lookup"><span data-stu-id="7413c-109">`GetTaskID` returns zero in `pTaskId` if the thread is not associated with a connection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7413c-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7413c-110">Requirements</span></span>  
 <span data-ttu-id="7413c-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7413c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7413c-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7413c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7413c-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7413c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7413c-114">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7413c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
