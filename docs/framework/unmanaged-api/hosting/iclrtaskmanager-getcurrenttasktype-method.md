---
title: "ICLRTaskManager::GetCurrentTaskType – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTaskManager.GetCurrentTaskType
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTaskManager::GetCurrentTaskType
helpviewer_keywords:
- GetCurrentTaskType method [.NET Framework hosting]
- ICLRTaskManager::GetCurrentTaskType method [.NET Framework hosting]
ms.assetid: 6b0d9259-dbe2-45bb-b34d-990f60c73424
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f4c1114f4d90c10d8ca40b1b6fc6e071eff5b3f2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="iclrtaskmanagergetcurrenttasktype-method"></a><span data-ttu-id="6278a-102">ICLRTaskManager::GetCurrentTaskType – metoda</span><span class="sxs-lookup"><span data-stu-id="6278a-102">ICLRTaskManager::GetCurrentTaskType Method</span></span>
<span data-ttu-id="6278a-103">Získá typ úlohy, který je aktuálně spuštěné.</span><span class="sxs-lookup"><span data-stu-id="6278a-103">Gets the type of the task that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6278a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6278a-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentTaskType(  
    [out] ETaskType *pTaskType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6278a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6278a-105">Parameters</span></span>  
 `pTaskType`  
 <span data-ttu-id="6278a-106">[out] Ukazatel na hodnotu [ETaskType](../../../../docs/framework/unmanaged-api/hosting/etasktype-enumeration.md) výčtu, která určuje typ úlohy, který je aktuálně spuštěné.</span><span class="sxs-lookup"><span data-stu-id="6278a-106">[out] A pointer to a value of the [ETaskType](../../../../docs/framework/unmanaged-api/hosting/etasktype-enumeration.md) enumeration that indicates the type of task that is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6278a-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6278a-107">Requirements</span></span>  
 <span data-ttu-id="6278a-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6278a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6278a-109">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6278a-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6278a-110">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6278a-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6278a-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6278a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6278a-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="6278a-112">See Also</span></span>  
 [<span data-ttu-id="6278a-113">Iclrtaskmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6278a-113">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
