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
ms.openlocfilehash: cd04e6d8bed86039b6f43985a8fb712b4612f76d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418347"
---
# <a name="icordebugprocess2getthreadfortaskid-method"></a><span data-ttu-id="90c91-102">ICorDebugProcess2::GetThreadForTaskID – metoda</span><span class="sxs-lookup"><span data-stu-id="90c91-102">ICorDebugProcess2::GetThreadForTaskID Method</span></span>
<span data-ttu-id="90c91-103">Získá vláken, na kterém je prováděna úloha se zadaným identifikátorem.</span><span class="sxs-lookup"><span data-stu-id="90c91-103">Gets the thread on which the task with the specified identifier is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90c91-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90c91-104">Syntax</span></span>  
  
```  
HRESULT GetThreadForTaskID (  
    [in]  TASKID            taskid,  
    [out] ICorDebugThread2  **ppThread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="90c91-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="90c91-105">Parameters</span></span>  
 `taskid`  
 <span data-ttu-id="90c91-106">[v] Identifikátor úlohy.</span><span class="sxs-lookup"><span data-stu-id="90c91-106">[in] The identifier of the task.</span></span>  
  
 `ppThread`  
 <span data-ttu-id="90c91-107">[out] Ukazatel na adresu icordebugthread2 – objekt, který představuje vlákno, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="90c91-107">[out] A pointer to the address of an ICorDebugThread2 object that represents the thread to be retrieved.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90c91-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="90c91-108">Remarks</span></span>  
 <span data-ttu-id="90c91-109">Hostitele lze nastavit identifikátor úlohy pomocí [iclrtask::settaskidentifier –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-settaskidentifier-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="90c91-109">The host can set the task identifier by using the [ICLRTask::SetTaskIdentifier](../../../../docs/framework/unmanaged-api/hosting/iclrtask-settaskidentifier-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90c91-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="90c91-110">Requirements</span></span>  
 <span data-ttu-id="90c91-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90c91-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90c91-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="90c91-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="90c91-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="90c91-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90c91-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90c91-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
