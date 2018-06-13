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
ms.openlocfilehash: 5db040f6db078b211043c547eed823c9b495ac97
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431319"
---
# <a name="iappdomainbindingonappdomain-method"></a><span data-ttu-id="6bb10-102">IAppDomainBinding::OnAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="6bb10-102">IAppDomainBinding::OnAppDomain Method</span></span>
<span data-ttu-id="6bb10-103">Voláno rozhraním modul CLR (CLR) oznámit hostitele vytvořený domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="6bb10-103">Called by the common language runtime (CLR) to notify the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bb10-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6bb10-104">Syntax</span></span>  
  
```  
HRESULT OnAppDomain (  
    [in] IUnknown* pAppdomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6bb10-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6bb10-105">Parameters</span></span>  
 `pAppdomain`  
 <span data-ttu-id="6bb10-106">[v] Ukazatel na [IUnknown](https://msdn.microsoft.com/library/94as6ehy(v=vs.110).aspx) rozhraní objekt, který představuje novou doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="6bb10-106">[in] A pointer to an [IUnknown](https://msdn.microsoft.com/library/94as6ehy(v=vs.110).aspx) interface object that represents the new application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bb10-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6bb10-107">Requirements</span></span>  
 <span data-ttu-id="6bb10-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6bb10-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bb10-109">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6bb10-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6bb10-110">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6bb10-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6bb10-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bb10-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bb10-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="6bb10-112">See Also</span></span>  
 [<span data-ttu-id="6bb10-113">IAppDomainBinding – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6bb10-113">IAppDomainBinding Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-interface.md)
