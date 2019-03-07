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
ms.openlocfilehash: 798ef6a9b058d9d49019554feba63627360e6a0e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57480036"
---
# <a name="iappdomainbindingonappdomain-method"></a><span data-ttu-id="9ab45-102">IAppDomainBinding::OnAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="9ab45-102">IAppDomainBinding::OnAppDomain Method</span></span>
<span data-ttu-id="9ab45-103">Volána modulem common language runtime (CLR), aby upozornil hostitele Vytvoření domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="9ab45-103">Called by the common language runtime (CLR) to notify the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ab45-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ab45-104">Syntax</span></span>  
  
```  
HRESULT OnAppDomain (  
    [in] IUnknown* pAppdomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ab45-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9ab45-105">Parameters</span></span>  
 `pAppdomain`  
 <span data-ttu-id="9ab45-106">[in] Ukazatel [IUnknown](/cpp/atl/iunknown) rozhraní objektu, který představuje nové aplikační doméně.</span><span class="sxs-lookup"><span data-stu-id="9ab45-106">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) interface object that represents the new application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ab45-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9ab45-107">Requirements</span></span>  
 <span data-ttu-id="9ab45-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ab45-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ab45-109">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9ab45-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9ab45-110">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9ab45-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9ab45-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ab45-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ab45-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9ab45-112">See also</span></span>
- [<span data-ttu-id="9ab45-113">IAppDomainBinding – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9ab45-113">IAppDomainBinding Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-interface.md)
