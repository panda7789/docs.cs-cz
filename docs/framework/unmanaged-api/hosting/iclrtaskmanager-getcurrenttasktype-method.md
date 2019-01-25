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
ms.openlocfilehash: 7d2a8818ef180b3522a53e29fa84453ea9033a2a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54522398"
---
# <a name="iclrtaskmanagergetcurrenttasktype-method"></a><span data-ttu-id="e58bc-102">ICLRTaskManager::GetCurrentTaskType – metoda</span><span class="sxs-lookup"><span data-stu-id="e58bc-102">ICLRTaskManager::GetCurrentTaskType Method</span></span>
<span data-ttu-id="e58bc-103">Získá typ úkolu, který aktuálně spouští.</span><span class="sxs-lookup"><span data-stu-id="e58bc-103">Gets the type of the task that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e58bc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e58bc-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentTaskType(  
    [out] ETaskType *pTaskType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e58bc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e58bc-105">Parameters</span></span>  
 `pTaskType`  
 <span data-ttu-id="e58bc-106">[out] Ukazatel na hodnotu [etasktype –](../../../../docs/framework/unmanaged-api/hosting/etasktype-enumeration.md) výčet, který určuje typ úkolu, který aktuálně spouští.</span><span class="sxs-lookup"><span data-stu-id="e58bc-106">[out] A pointer to a value of the [ETaskType](../../../../docs/framework/unmanaged-api/hosting/etasktype-enumeration.md) enumeration that indicates the type of task that is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e58bc-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e58bc-107">Requirements</span></span>  
 <span data-ttu-id="e58bc-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e58bc-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e58bc-109">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e58bc-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e58bc-110">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e58bc-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e58bc-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e58bc-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e58bc-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e58bc-112">See also</span></span>
- [<span data-ttu-id="e58bc-113">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e58bc-113">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
