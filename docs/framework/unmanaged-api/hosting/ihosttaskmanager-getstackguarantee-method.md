---
title: IHostTaskManager::GetStackGuarantee – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 739670fb84eb0145fd8bf8073f453518487c38b0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749568"
---
# <a name="ihosttaskmanagergetstackguarantee-method"></a><span data-ttu-id="151f7-102">IHostTaskManager::GetStackGuarantee – metoda</span><span class="sxs-lookup"><span data-stu-id="151f7-102">IHostTaskManager::GetStackGuarantee Method</span></span>
<span data-ttu-id="151f7-103">Získá velikost místa zásobníku, které je zaručeno, že bude k dispozici po dokončení operace zásobníku, ale před ukončením procesu.</span><span class="sxs-lookup"><span data-stu-id="151f7-103">Gets the amount of stack space that is guaranteed to be available after a stack operation completes, but before the closing of a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="151f7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="151f7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackGuarantee(  
    [out] ULONG *pGuarantee  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="151f7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="151f7-105">Parameters</span></span>  
 `pGuarantee`  
 <span data-ttu-id="151f7-106">[out] Ukazatel na počet bajtů, které jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="151f7-106">[out] A pointer to the number of bytes that are available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="151f7-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="151f7-107">Requirements</span></span>  
 <span data-ttu-id="151f7-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="151f7-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="151f7-109">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="151f7-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="151f7-110">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="151f7-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="151f7-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="151f7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="151f7-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="151f7-112">See also</span></span>

- [<span data-ttu-id="151f7-113">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="151f7-113">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
