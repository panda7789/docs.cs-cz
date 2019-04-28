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
ms.openlocfilehash: b5b4210bda7d41b190f1025b62132c5df896a2a1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61703618"
---
# <a name="igchostsetvirtualmemlimit-method"></a><span data-ttu-id="c7a83-102">IGCHost::SetVirtualMemLimit – metoda</span><span class="sxs-lookup"><span data-stu-id="c7a83-102">IGCHost::SetVirtualMemLimit Method</span></span>
<span data-ttu-id="c7a83-103">Nastaví maximální velikost virtuální paměti modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="c7a83-103">Sets the maximum size of the runtime's virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7a83-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c7a83-104">Syntax</span></span>  
  
```  
HRESULT SetVirtualMemLimit (  
    [in] SIZE_T sztMaxVirtualMemMB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7a83-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c7a83-105">Parameters</span></span>  
 `sztMaxVirtualMemMB`  
 <span data-ttu-id="c7a83-106">[in] Maximální velikost v megabajtech, modul runtime virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="c7a83-106">[in] The maximum size, in megabytes, of the runtime's virtual memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7a83-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c7a83-107">Remarks</span></span>  
 <span data-ttu-id="c7a83-108">Maximální velikost virtuální paměti modulu runtime můžete změnit dynamicky.</span><span class="sxs-lookup"><span data-stu-id="c7a83-108">The maximum size of the runtime's virtual memory can be changed dynamically.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7a83-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c7a83-109">Requirements</span></span>  
 <span data-ttu-id="c7a83-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7a83-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7a83-111">**Záhlaví:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="c7a83-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="c7a83-112">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c7a83-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c7a83-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7a83-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7a83-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c7a83-114">See also</span></span>

- [<span data-ttu-id="c7a83-115">IGCHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c7a83-115">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
