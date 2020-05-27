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
ms.openlocfilehash: d76242eb8539f2e8dffbf39b7eaf595664bdce8e
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842020"
---
# <a name="ihosttaskmanagergetstackguarantee-method"></a><span data-ttu-id="a80e5-102">IHostTaskManager::GetStackGuarantee – metoda</span><span class="sxs-lookup"><span data-stu-id="a80e5-102">IHostTaskManager::GetStackGuarantee Method</span></span>
<span data-ttu-id="a80e5-103">Získá velikost prostoru zásobníku, která je zaručena k dispozici po dokončení operace zásobníku, ale před zavřením procesu.</span><span class="sxs-lookup"><span data-stu-id="a80e5-103">Gets the amount of stack space that is guaranteed to be available after a stack operation completes, but before the closing of a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a80e5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a80e5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackGuarantee(  
    [out] ULONG *pGuarantee  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a80e5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a80e5-105">Parameters</span></span>  
 `pGuarantee`  
 <span data-ttu-id="a80e5-106">mimo Ukazatel na počet bajtů, které jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="a80e5-106">[out] A pointer to the number of bytes that are available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a80e5-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a80e5-107">Requirements</span></span>  
 <span data-ttu-id="a80e5-108">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a80e5-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a80e5-109">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a80e5-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a80e5-110">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a80e5-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a80e5-111">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a80e5-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a80e5-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="a80e5-112">See also</span></span>

- [<span data-ttu-id="a80e5-113">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a80e5-113">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
