---
title: "IHostTaskManager::GetStackGuarantee – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostTaskManager.GetStackGuarantee
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::GetStackGuarantee
helpviewer_keywords:
- GetStackGuarantee method [.NET Framework hosting]
- IHostTaskManager::GetStackGuarantee method [.NET Framework hosting]
ms.assetid: 8176d732-c25c-4520-811d-e3310f339947
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a2e4829083715fad8d77c1b5a2c303a07d5684ac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskmanagergetstackguarantee-method"></a><span data-ttu-id="583d1-102">IHostTaskManager::GetStackGuarantee – metoda</span><span class="sxs-lookup"><span data-stu-id="583d1-102">IHostTaskManager::GetStackGuarantee Method</span></span>
<span data-ttu-id="583d1-103">Získá velikost zásobníku místa, které se musí být k dispozici po dokončení operace zásobníku, ale před zavřením procesu.</span><span class="sxs-lookup"><span data-stu-id="583d1-103">Gets the amount of stack space that is guaranteed to be available after a stack operation completes, but before the closing of a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="583d1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="583d1-104">Syntax</span></span>  
  
```  
HRESULT GetStackGuarantee(  
    [out] ULONG *pGuarantee  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="583d1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="583d1-105">Parameters</span></span>  
 `pGuarantee`  
 <span data-ttu-id="583d1-106">[out] Ukazatel na počet bajtů, které jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="583d1-106">[out] A pointer to the number of bytes that are available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="583d1-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="583d1-107">Requirements</span></span>  
 <span data-ttu-id="583d1-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="583d1-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="583d1-109">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="583d1-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="583d1-110">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="583d1-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="583d1-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="583d1-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="583d1-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="583d1-112">See Also</span></span>  
 [<span data-ttu-id="583d1-113">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="583d1-113">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
