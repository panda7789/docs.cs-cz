---
title: "ICorDebugThread2::GetTaskID – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread2.GetTaskID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread2::GetTaskID
helpviewer_keywords:
- ICorDebugThread2::GetTaskID method [.NET Framework debugging]
- GetTaskID method [.NET Framework debugging]
ms.assetid: 6ba3c6ee-4ba1-4c98-bf1e-8531acd3da09
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0e2d5a845b7047949618bed4176e6d24fee43c14
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthread2gettaskid-method"></a><span data-ttu-id="613e9-102">ICorDebugThread2::GetTaskID – metoda</span><span class="sxs-lookup"><span data-stu-id="613e9-102">ICorDebugThread2::GetTaskID Method</span></span>
<span data-ttu-id="613e9-103">Získá identifikátor úloha spuštěná na tento přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="613e9-103">Gets the identifier of the task running on this thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="613e9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="613e9-104">Syntax</span></span>  
  
```  
HRESULT GetTaskID (  
    [out] TASKID  *pTaskId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="613e9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="613e9-105">Parameters</span></span>  
 `pTaskId`  
 <span data-ttu-id="613e9-106">[out] Ukazatel na identifikátor úloha spuštěná na vlákno představuje tento objekt icordebugthread2 –.</span><span class="sxs-lookup"><span data-stu-id="613e9-106">[out] A pointer to the identifier of the task running on the thread represented by this ICorDebugThread2 object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="613e9-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="613e9-107">Remarks</span></span>  
 <span data-ttu-id="613e9-108">Úloha může být spuštěn ve vlákně pouze, pokud vlákno je přidružené k připojení.</span><span class="sxs-lookup"><span data-stu-id="613e9-108">A task can only be running on the thread if the thread is associated with a connection.</span></span> <span data-ttu-id="613e9-109">`GetTaskID`Vrátí hodnotu hodnotu `pTaskId` Pokud vlákno není přidružené k připojení.</span><span class="sxs-lookup"><span data-stu-id="613e9-109">`GetTaskID` returns zero in `pTaskId` if the thread is not associated with a connection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="613e9-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="613e9-110">Requirements</span></span>  
 <span data-ttu-id="613e9-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="613e9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="613e9-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="613e9-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="613e9-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="613e9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="613e9-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="613e9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
