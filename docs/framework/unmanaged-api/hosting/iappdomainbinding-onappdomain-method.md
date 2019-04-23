---
title: IAppDomainBinding::OnAppDomain – metoda
ms.date: 03/30/2017
api_name:
- IAppDomainBinding.OnAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- OnAppDomain
helpviewer_keywords:
- IAppDomainBinding::OnAppDomain method [.NET Framework hosting]
- OnAppDomain method [.NET Framework hosting]
ms.assetid: b419dcc9-e8aa-484b-af0d-0f40358edb99
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2903395f5f834f2435b14d0b3f3e8bfe24af2867
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59183050"
---
# <a name="iappdomainbindingonappdomain-method"></a><span data-ttu-id="475ee-102">IAppDomainBinding::OnAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="475ee-102">IAppDomainBinding::OnAppDomain Method</span></span>
<span data-ttu-id="475ee-103">Volána modulem common language runtime (CLR), aby upozornil hostitele Vytvoření domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="475ee-103">Called by the common language runtime (CLR) to notify the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="475ee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="475ee-104">Syntax</span></span>  
  
```  
HRESULT OnAppDomain (  
    [in] IUnknown* pAppdomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="475ee-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="475ee-105">Parameters</span></span>  
 `pAppdomain`  
 <span data-ttu-id="475ee-106">[in] Ukazatel [IUnknown](/cpp/atl/iunknown) rozhraní objektu, který představuje nové aplikační doméně.</span><span class="sxs-lookup"><span data-stu-id="475ee-106">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) interface object that represents the new application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="475ee-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="475ee-107">Requirements</span></span>  
 <span data-ttu-id="475ee-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="475ee-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="475ee-109">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="475ee-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="475ee-110">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="475ee-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="475ee-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="475ee-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="475ee-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="475ee-112">See also</span></span>

- [<span data-ttu-id="475ee-113">IAppDomainBinding – rozhraní</span><span class="sxs-lookup"><span data-stu-id="475ee-113">IAppDomainBinding Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-interface.md)
