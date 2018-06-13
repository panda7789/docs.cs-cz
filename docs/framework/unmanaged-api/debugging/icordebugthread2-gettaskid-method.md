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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f5690856b526bf0f7bc4527d04ae8044cda1f6e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417863"
---
# <a name="icordebugthread2gettaskid-method"></a><span data-ttu-id="7e83e-102">ICorDebugThread2::GetTaskID – metoda</span><span class="sxs-lookup"><span data-stu-id="7e83e-102">ICorDebugThread2::GetTaskID Method</span></span>
<span data-ttu-id="7e83e-103">Získá identifikátor úloha spuštěná na tento přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="7e83e-103">Gets the identifier of the task running on this thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e83e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7e83e-104">Syntax</span></span>  
  
```  
HRESULT GetTaskID (  
    [out] TASKID  *pTaskId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7e83e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7e83e-105">Parameters</span></span>  
 `pTaskId`  
 <span data-ttu-id="7e83e-106">[out] Ukazatel na identifikátor úloha spuštěná na vlákno představuje tento objekt icordebugthread2 –.</span><span class="sxs-lookup"><span data-stu-id="7e83e-106">[out] A pointer to the identifier of the task running on the thread represented by this ICorDebugThread2 object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e83e-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7e83e-107">Remarks</span></span>  
 <span data-ttu-id="7e83e-108">Úloha může být spuštěn ve vlákně pouze, pokud vlákno je přidružené k připojení.</span><span class="sxs-lookup"><span data-stu-id="7e83e-108">A task can only be running on the thread if the thread is associated with a connection.</span></span> <span data-ttu-id="7e83e-109">`GetTaskID` Vrátí hodnotu hodnotu `pTaskId` Pokud vlákno není přidružené k připojení.</span><span class="sxs-lookup"><span data-stu-id="7e83e-109">`GetTaskID` returns zero in `pTaskId` if the thread is not associated with a connection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e83e-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7e83e-110">Requirements</span></span>  
 <span data-ttu-id="7e83e-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e83e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e83e-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7e83e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7e83e-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e83e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e83e-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e83e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
