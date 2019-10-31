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
ms.openlocfilehash: 22ec34c82d0f8e550dfc8941f2c048ebed6cf1d7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133026"
---
# <a name="ihosttaskmanagergetstackguarantee-method"></a><span data-ttu-id="22d27-102">IHostTaskManager::GetStackGuarantee – metoda</span><span class="sxs-lookup"><span data-stu-id="22d27-102">IHostTaskManager::GetStackGuarantee Method</span></span>
<span data-ttu-id="22d27-103">Získá velikost prostoru zásobníku, která je zaručena k dispozici po dokončení operace zásobníku, ale před zavřením procesu.</span><span class="sxs-lookup"><span data-stu-id="22d27-103">Gets the amount of stack space that is guaranteed to be available after a stack operation completes, but before the closing of a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22d27-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22d27-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackGuarantee(  
    [out] ULONG *pGuarantee  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22d27-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="22d27-105">Parameters</span></span>  
 `pGuarantee`  
 <span data-ttu-id="22d27-106">mimo Ukazatel na počet bajtů, které jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="22d27-106">[out] A pointer to the number of bytes that are available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22d27-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="22d27-107">Requirements</span></span>  
 <span data-ttu-id="22d27-108">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22d27-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22d27-109">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="22d27-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="22d27-110">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="22d27-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="22d27-111">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22d27-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22d27-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="22d27-112">See also</span></span>

- [<span data-ttu-id="22d27-113">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="22d27-113">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
