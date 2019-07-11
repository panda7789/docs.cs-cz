---
title: ICorDebugProcess2::GetThreadForTaskID – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetThreadForTaskID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetThreadForTaskID
helpviewer_keywords:
- ICorDebugProcess2::GetThreadForTaskId method [.NET Framework debugging]
- GetThreadForTaskID method [.NET Framework debugging]
ms.assetid: 32d54a5b-8ad3-405b-a1b9-0936a3b49d1e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c85040a31966a92ead6ca4786f62852f17923056
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736930"
---
# <a name="icordebugprocess2getthreadfortaskid-method"></a><span data-ttu-id="fcffc-102">ICorDebugProcess2::GetThreadForTaskID – metoda</span><span class="sxs-lookup"><span data-stu-id="fcffc-102">ICorDebugProcess2::GetThreadForTaskID Method</span></span>
<span data-ttu-id="fcffc-103">Získá vlákno, na kterém je spuštěn úkol se zadaným identifikátorem.</span><span class="sxs-lookup"><span data-stu-id="fcffc-103">Gets the thread on which the task with the specified identifier is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcffc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fcffc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadForTaskID (  
    [in]  TASKID            taskid,  
    [out] ICorDebugThread2  **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fcffc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fcffc-105">Parameters</span></span>  
 `taskid`  
 <span data-ttu-id="fcffc-106">[in] Identifikátor úkolu.</span><span class="sxs-lookup"><span data-stu-id="fcffc-106">[in] The identifier of the task.</span></span>  
  
 `ppThread`  
 <span data-ttu-id="fcffc-107">[out] Ukazatel na adresu icordebugthread2 – objekt, který představuje vlákna, která se má načíst.</span><span class="sxs-lookup"><span data-stu-id="fcffc-107">[out] A pointer to the address of an ICorDebugThread2 object that represents the thread to be retrieved.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fcffc-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fcffc-108">Remarks</span></span>  
 <span data-ttu-id="fcffc-109">Hostitele můžete nastavit pomocí identifikátor úkolu [iclrtask::settaskidentifier –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-settaskidentifier-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="fcffc-109">The host can set the task identifier by using the [ICLRTask::SetTaskIdentifier](../../../../docs/framework/unmanaged-api/hosting/iclrtask-settaskidentifier-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcffc-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fcffc-110">Requirements</span></span>  
 <span data-ttu-id="fcffc-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fcffc-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcffc-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fcffc-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fcffc-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fcffc-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fcffc-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcffc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
