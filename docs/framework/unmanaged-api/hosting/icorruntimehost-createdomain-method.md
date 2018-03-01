---
title: "ICorRuntimeHost::CreateDomain – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorRuntimeHost.CreateDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomain
helpviewer_keywords:
- CreateDomain method [.NET Framework hosting]
- ICorRuntimeHost::CreateDomain method [.NET Framework hosting]
ms.assetid: b96c5ef3-a9df-4c7c-9952-432d3272cb5c
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fe0adad8397f42716368691abbb1d1c303fced97
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehostcreatedomain-method"></a><span data-ttu-id="5176f-102">ICorRuntimeHost::CreateDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="5176f-102">ICorRuntimeHost::CreateDomain Method</span></span>
<span data-ttu-id="5176f-103">Vytvoří doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="5176f-103">Creates an application domain.</span></span> <span data-ttu-id="5176f-104">Volající obdrží ukazatele rozhraní typu <xref:System._AppDomain> na instanci typu <xref:System.AppDomain?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5176f-104">The caller receives an interface pointer of type <xref:System._AppDomain> to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5176f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5176f-105">Syntax</span></span>  
  
```  
HRESULT CreateDomain (  
    [in] LPWSTR    pwzFriendlyName,  
    [in] IUnknown* pIdentityArray,  
    [out] void   **pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5176f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5176f-106">Parameters</span></span>  
 `pwzFriendlyName`  
 <span data-ttu-id="5176f-107">[v] Volitelný parametr dávat popisný název domény.</span><span class="sxs-lookup"><span data-stu-id="5176f-107">[in] An optional parameter used to give a friendly name to the domain.</span></span> <span data-ttu-id="5176f-108">Tento popisný název zobrazený ve uživatelského rozhraní, jako je například ladicí programy k identifikaci domény.</span><span class="sxs-lookup"><span data-stu-id="5176f-108">This friendly name can be displayed in user interfaces such as debuggers to identify the domain.</span></span>  
  
 `pIdentityArray`  
 <span data-ttu-id="5176f-109">[v] Volitelné pole ukazatele na `IIdentity` instancí, které představují důkaz namapovat prostřednictvím zásad zabezpečení pro vytvoření sady oprávnění.</span><span class="sxs-lookup"><span data-stu-id="5176f-109">[in] An optional array of pointers to `IIdentity` instances that represent evidence mapped through security policy to establish a  permission set.</span></span> <span data-ttu-id="5176f-110">`IIdentity` Objektu je možné získat volání [createevidence –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="5176f-110">An `IIdentity` object can be obtained by calling the [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) method.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="5176f-111">[out] Ukazatele rozhraní typu <xref:System._AppDomain> na instanci <xref:System.AppDomain?displayProperty=nameWithType> který lze použít k podrobnějšímu řízení domény.</span><span class="sxs-lookup"><span data-stu-id="5176f-111">[out] An interface pointer of type <xref:System._AppDomain> to an instance of <xref:System.AppDomain?displayProperty=nameWithType> that can be used to further control the domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5176f-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5176f-112">Return Value</span></span>  
  
|<span data-ttu-id="5176f-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5176f-113">HRESULT</span></span>|<span data-ttu-id="5176f-114">Popis</span><span class="sxs-lookup"><span data-stu-id="5176f-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5176f-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="5176f-115">S_OK</span></span>|<span data-ttu-id="5176f-116">Operace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="5176f-116">The operation was successful.</span></span>|  
|<span data-ttu-id="5176f-117">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="5176f-117">S_FALSE</span></span>|<span data-ttu-id="5176f-118">Operaci se nepodařilo dokončit.</span><span class="sxs-lookup"><span data-stu-id="5176f-118">The operation failed to complete.</span></span>|  
|<span data-ttu-id="5176f-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5176f-119">E_FAIL</span></span>|<span data-ttu-id="5176f-120">Došlo k neznámé, závažnou chybu.</span><span class="sxs-lookup"><span data-stu-id="5176f-120">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="5176f-121">Pokud metoda vrátí E_FAIL, modul CLR (CLR) již není použitelné v procesu.</span><span class="sxs-lookup"><span data-stu-id="5176f-121">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="5176f-122">Následující volání žádné hostování rozhraní API vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5176f-122">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5176f-123">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5176f-123">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5176f-124">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="5176f-124">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5176f-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5176f-125">Requirements</span></span>  
 <span data-ttu-id="5176f-126">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5176f-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5176f-127">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5176f-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5176f-128">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5176f-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5176f-129">**Verze rozhraní .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="5176f-129">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5176f-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="5176f-130">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="5176f-131">ICorRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5176f-131">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
