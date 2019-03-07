---
title: IGCHost::SetVirtualMemLimit – metoda
ms.date: 03/30/2017
api_name:
- IGCHost.SetVirtualMemLimit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetVirtualMemLimit
helpviewer_keywords:
- IGCHost::SetVirtualMemLimit method [.NET Framework hosting]
- SetVirtualMemLimit method [.NET Framework hosting]
ms.assetid: c7e7c2d0-e58c-4650-b40c-47b2be2cda45
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b25e9c738c95a918b79d3fd324787e4aaf3aaa7f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57502472"
---
# <a name="igchostsetvirtualmemlimit-method"></a><span data-ttu-id="277f1-102">IGCHost::SetVirtualMemLimit – metoda</span><span class="sxs-lookup"><span data-stu-id="277f1-102">IGCHost::SetVirtualMemLimit Method</span></span>
<span data-ttu-id="277f1-103">Nastaví maximální velikost virtuální paměti modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="277f1-103">Sets the maximum size of the runtime's virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="277f1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="277f1-104">Syntax</span></span>  
  
```  
HRESULT SetVirtualMemLimit (  
    [in] SIZE_T sztMaxVirtualMemMB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="277f1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="277f1-105">Parameters</span></span>  
 `sztMaxVirtualMemMB`  
 <span data-ttu-id="277f1-106">[in] Maximální velikost v megabajtech, modul runtime virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="277f1-106">[in] The maximum size, in megabytes, of the runtime's virtual memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="277f1-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="277f1-107">Remarks</span></span>  
 <span data-ttu-id="277f1-108">Maximální velikost virtuální paměti modulu runtime můžete změnit dynamicky.</span><span class="sxs-lookup"><span data-stu-id="277f1-108">The maximum size of the runtime's virtual memory can be changed dynamically.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="277f1-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="277f1-109">Requirements</span></span>  
 <span data-ttu-id="277f1-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="277f1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="277f1-111">**Záhlaví:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="277f1-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="277f1-112">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="277f1-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="277f1-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="277f1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="277f1-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="277f1-114">See also</span></span>
- [<span data-ttu-id="277f1-115">IGCHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="277f1-115">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
