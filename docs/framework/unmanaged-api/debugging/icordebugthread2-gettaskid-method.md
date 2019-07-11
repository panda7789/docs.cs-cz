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
ms.openlocfilehash: 1272df17a9a9a500b84f62914811b8d109bf3cdd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768950"
---
# <a name="icordebugthread2gettaskid-method"></a><span data-ttu-id="9ac73-102">ICorDebugThread2::GetTaskID – metoda</span><span class="sxs-lookup"><span data-stu-id="9ac73-102">ICorDebugThread2::GetTaskID Method</span></span>
<span data-ttu-id="9ac73-103">Získá identifikátor úloha spuštěná na toto vlákno.</span><span class="sxs-lookup"><span data-stu-id="9ac73-103">Gets the identifier of the task running on this thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ac73-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ac73-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTaskID (  
    [out] TASKID  *pTaskId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ac73-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9ac73-105">Parameters</span></span>  
 `pTaskId`  
 <span data-ttu-id="9ac73-106">[out] Ukazatel na identifikátor úloha spuštěná na vlákno reprezentovaný tímto objektem icordebugthread2 –.</span><span class="sxs-lookup"><span data-stu-id="9ac73-106">[out] A pointer to the identifier of the task running on the thread represented by this ICorDebugThread2 object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ac73-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9ac73-107">Remarks</span></span>  
 <span data-ttu-id="9ac73-108">Úkol může být spuštěn ve vlákně pouze, pokud vlákno je spojen s připojením.</span><span class="sxs-lookup"><span data-stu-id="9ac73-108">A task can only be running on the thread if the thread is associated with a connection.</span></span> <span data-ttu-id="9ac73-109">`GetTaskID` Vrátí nulu `pTaskId` Pokud vlákno není přidružen k připojení.</span><span class="sxs-lookup"><span data-stu-id="9ac73-109">`GetTaskID` returns zero in `pTaskId` if the thread is not associated with a connection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ac73-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9ac73-110">Requirements</span></span>  
 <span data-ttu-id="9ac73-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ac73-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ac73-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9ac73-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9ac73-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ac73-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ac73-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ac73-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
