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
ms.openlocfilehash: 2d5dbd003d0ea5decae0025d47e6bd5c1fb1ed4a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617071"
---
# <a name="iappdomainbindingonappdomain-method"></a><span data-ttu-id="12ac7-102">IAppDomainBinding::OnAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="12ac7-102">IAppDomainBinding::OnAppDomain Method</span></span>
<span data-ttu-id="12ac7-103">Volána modulem CLR (Common Language Runtime) pro oznamování hostitele, že byla vytvořena doména aplikace.</span><span class="sxs-lookup"><span data-stu-id="12ac7-103">Called by the common language runtime (CLR) to notify the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12ac7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12ac7-104">Syntax</span></span>  
  
```cpp  
HRESULT OnAppDomain (  
    [in] IUnknown* pAppdomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12ac7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="12ac7-105">Parameters</span></span>  
 `pAppdomain`  
 <span data-ttu-id="12ac7-106">pro Ukazatel na objekt rozhraní [IUnknown](/cpp/atl/iunknown) , který představuje novou doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="12ac7-106">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) interface object that represents the new application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12ac7-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="12ac7-107">Requirements</span></span>  
 <span data-ttu-id="12ac7-108">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12ac7-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12ac7-109">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="12ac7-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="12ac7-110">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="12ac7-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="12ac7-111">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12ac7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12ac7-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="12ac7-112">See also</span></span>

- [<span data-ttu-id="12ac7-113">IAppDomainBinding – rozhraní</span><span class="sxs-lookup"><span data-stu-id="12ac7-113">IAppDomainBinding Interface</span></span>](iappdomainbinding-interface.md)
