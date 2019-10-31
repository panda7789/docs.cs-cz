---
title: IGCHostControl::RequestVirtualMemLimit – metoda
ms.date: 03/30/2017
api_name:
- IGCHostControl.RequestVirtualMemLimit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- RequestVirtualMemLimit
helpviewer_keywords:
- IGCHostControl::RequestVirtualMemLimit method [.NET Framework hosting]
- RequestVirtualMemLimit method [.NET Framework hosting]
ms.assetid: f4984a8c-4c0e-4460-9aa1-d022b3621228
topic_type:
- apiref
ms.openlocfilehash: ccff575974093de0bf00b257cba78c509f9cbd92
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134779"
---
# <a name="igchostcontrolrequestvirtualmemlimit-method"></a><span data-ttu-id="ba5e7-102">IGCHostControl::RequestVirtualMemLimit – metoda</span><span class="sxs-lookup"><span data-stu-id="ba5e7-102">IGCHostControl::RequestVirtualMemLimit Method</span></span>
<span data-ttu-id="ba5e7-103">Požádá hostitele o změnu omezení virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="ba5e7-103">Requests the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba5e7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ba5e7-104">Syntax</span></span>  
  
```cpp  
HRESULT RequestVirtualMemLimit (  
    [in] SIZE_T       sztMaxVirtualMemMB,  
    [in, out] SIZE_T* psztNewMaxVirtualMemMB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba5e7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ba5e7-105">Parameters</span></span>  
 `sztMaxVirtualMemMB`  
 <span data-ttu-id="ba5e7-106">pro Požadovaná velikost paměti, která má být přidělena.</span><span class="sxs-lookup"><span data-stu-id="ba5e7-106">[in] The requested size of memory to be allocated.</span></span>  
  
 `psztNewMaxVirtualMemMB`  
 <span data-ttu-id="ba5e7-107">[in, out] Ukazatel na skutečnou velikost přidělené paměti.</span><span class="sxs-lookup"><span data-stu-id="ba5e7-107">[in, out] A pointer to the actual size of memory allocated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba5e7-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ba5e7-108">Requirements</span></span>  
 <span data-ttu-id="ba5e7-109">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba5e7-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba5e7-110">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ba5e7-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ba5e7-111">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ba5e7-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ba5e7-112">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba5e7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba5e7-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ba5e7-113">See also</span></span>

- [<span data-ttu-id="ba5e7-114">IGCHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ba5e7-114">IGCHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)
