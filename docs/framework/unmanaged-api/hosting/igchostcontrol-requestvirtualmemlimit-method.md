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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 948b18832ccfc5e0fc2e42ee58e6444a581de260
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59209684"
---
# <a name="igchostcontrolrequestvirtualmemlimit-method"></a><span data-ttu-id="ad137-102">IGCHostControl::RequestVirtualMemLimit – metoda</span><span class="sxs-lookup"><span data-stu-id="ad137-102">IGCHostControl::RequestVirtualMemLimit Method</span></span>
<span data-ttu-id="ad137-103">Požadavky hostitele, chcete-li změnit omezení virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="ad137-103">Requests the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad137-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad137-104">Syntax</span></span>  
  
```  
HRESULT RequestVirtualMemLimit (  
    [in] SIZE_T       sztMaxVirtualMemMB,  
    [in, out] SIZE_T* psztNewMaxVirtualMemMB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad137-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ad137-105">Parameters</span></span>  
 `sztMaxVirtualMemMB`  
 <span data-ttu-id="ad137-106">[in] Požadovaná velikost paměti, která bude přidělena.</span><span class="sxs-lookup"><span data-stu-id="ad137-106">[in] The requested size of memory to be allocated.</span></span>  
  
 `psztNewMaxVirtualMemMB`  
 <span data-ttu-id="ad137-107">[out v] Ukazatel na skutečnou velikost přidělené paměti.</span><span class="sxs-lookup"><span data-stu-id="ad137-107">[in, out] A pointer to the actual size of memory allocated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad137-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ad137-108">Requirements</span></span>  
 <span data-ttu-id="ad137-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad137-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad137-110">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ad137-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ad137-111">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ad137-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="ad137-112">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="ad137-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ad137-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ad137-113">See also</span></span>

- [<span data-ttu-id="ad137-114">IGCHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ad137-114">IGCHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)
