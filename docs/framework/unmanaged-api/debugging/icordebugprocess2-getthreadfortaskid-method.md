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
ms.openlocfilehash: 89be29c770098d92ce3c47f7c45b1bb8580f2edb
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213514"
---
# <a name="icordebugprocess2getthreadfortaskid-method"></a><span data-ttu-id="8e004-102">ICorDebugProcess2::GetThreadForTaskID – metoda</span><span class="sxs-lookup"><span data-stu-id="8e004-102">ICorDebugProcess2::GetThreadForTaskID Method</span></span>
<span data-ttu-id="8e004-103">Získá vlákno, ve kterém je spuštěn úkol se zadaným identifikátorem.</span><span class="sxs-lookup"><span data-stu-id="8e004-103">Gets the thread on which the task with the specified identifier is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e004-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8e004-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadForTaskID (  
    [in]  TASKID            taskid,  
    [out] ICorDebugThread2  **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8e004-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8e004-105">Parameters</span></span>  
 `taskid`  
 <span data-ttu-id="8e004-106">pro Identifikátor úkolu</span><span class="sxs-lookup"><span data-stu-id="8e004-106">[in] The identifier of the task.</span></span>  
  
 `ppThread`  
 <span data-ttu-id="8e004-107">mimo Ukazatel na adresu objektu ICorDebugThread2, který představuje vlákno, které má být načteno.</span><span class="sxs-lookup"><span data-stu-id="8e004-107">[out] A pointer to the address of an ICorDebugThread2 object that represents the thread to be retrieved.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8e004-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8e004-108">Remarks</span></span>  
 <span data-ttu-id="8e004-109">Hostitel může nastavit identifikátor úlohy pomocí metody [ICLRTask:: SetTaskIdentifier –](../hosting/iclrtask-settaskidentifier-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8e004-109">The host can set the task identifier by using the [ICLRTask::SetTaskIdentifier](../hosting/iclrtask-settaskidentifier-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e004-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8e004-110">Requirements</span></span>  
 <span data-ttu-id="8e004-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e004-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e004-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8e004-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8e004-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8e004-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8e004-114">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e004-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
