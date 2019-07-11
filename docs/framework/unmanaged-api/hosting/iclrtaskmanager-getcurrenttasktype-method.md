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
ms.openlocfilehash: 595c39b56587150d0d8f9c3f8bdfcae4c075e4d8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67770171"
---
# <a name="iclrtaskmanagergetcurrenttasktype-method"></a><span data-ttu-id="cb22e-102">ICLRTaskManager::GetCurrentTaskType – metoda</span><span class="sxs-lookup"><span data-stu-id="cb22e-102">ICLRTaskManager::GetCurrentTaskType Method</span></span>
<span data-ttu-id="cb22e-103">Získá typ úkolu, který aktuálně spouští.</span><span class="sxs-lookup"><span data-stu-id="cb22e-103">Gets the type of the task that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb22e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cb22e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentTaskType(  
    [out] ETaskType *pTaskType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb22e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cb22e-105">Parameters</span></span>  
 `pTaskType`  
 <span data-ttu-id="cb22e-106">[out] Ukazatel na hodnotu [etasktype –](../../../../docs/framework/unmanaged-api/hosting/etasktype-enumeration.md) výčet, který určuje typ úkolu, který aktuálně spouští.</span><span class="sxs-lookup"><span data-stu-id="cb22e-106">[out] A pointer to a value of the [ETaskType](../../../../docs/framework/unmanaged-api/hosting/etasktype-enumeration.md) enumeration that indicates the type of task that is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb22e-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cb22e-107">Requirements</span></span>  
 <span data-ttu-id="cb22e-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb22e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb22e-109">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cb22e-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cb22e-110">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cb22e-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cb22e-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb22e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb22e-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cb22e-112">See also</span></span>

- [<span data-ttu-id="cb22e-113">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cb22e-113">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
