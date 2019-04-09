---
title: ICLRTaskManager::GetCurrentTaskType – metoda
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.GetCurrentTaskType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::GetCurrentTaskType
helpviewer_keywords:
- GetCurrentTaskType method [.NET Framework hosting]
- ICLRTaskManager::GetCurrentTaskType method [.NET Framework hosting]
ms.assetid: 6b0d9259-dbe2-45bb-b34d-990f60c73424
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2963e2a31fd62470e3ed6933edb38119d286071b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59071971"
---
# <a name="iclrtaskmanagergetcurrenttasktype-method"></a><span data-ttu-id="dc2b6-102">ICLRTaskManager::GetCurrentTaskType – metoda</span><span class="sxs-lookup"><span data-stu-id="dc2b6-102">ICLRTaskManager::GetCurrentTaskType Method</span></span>
<span data-ttu-id="dc2b6-103">Získá typ úkolu, který aktuálně spouští.</span><span class="sxs-lookup"><span data-stu-id="dc2b6-103">Gets the type of the task that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc2b6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc2b6-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentTaskType(  
    [out] ETaskType *pTaskType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dc2b6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dc2b6-105">Parameters</span></span>  
 `pTaskType`  
 <span data-ttu-id="dc2b6-106">[out] Ukazatel na hodnotu [etasktype –](../../../../docs/framework/unmanaged-api/hosting/etasktype-enumeration.md) výčet, který určuje typ úkolu, který aktuálně spouští.</span><span class="sxs-lookup"><span data-stu-id="dc2b6-106">[out] A pointer to a value of the [ETaskType](../../../../docs/framework/unmanaged-api/hosting/etasktype-enumeration.md) enumeration that indicates the type of task that is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc2b6-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dc2b6-107">Requirements</span></span>  
 <span data-ttu-id="dc2b6-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc2b6-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc2b6-109">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dc2b6-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dc2b6-110">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dc2b6-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="dc2b6-111">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="dc2b6-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="dc2b6-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dc2b6-112">See also</span></span>

- [<span data-ttu-id="dc2b6-113">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dc2b6-113">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
