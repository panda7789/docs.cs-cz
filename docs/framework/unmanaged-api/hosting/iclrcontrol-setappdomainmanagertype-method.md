---
title: ICLRControl::SetAppDomainManagerType – metoda
ms.date: 03/30/2017
api_name:
- ICLRControl.SetAppDomainManagerType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl::SetAppDomainManagerType
helpviewer_keywords:
- SetAppDomainManagerType method, ICLRControl interface [.NET Framework hosting]
- ICLRControl::SetAppDomainManagerType method [.NET Framework hosting]
ms.assetid: ec57828b-2aad-496d-a35a-e45d4bd7fe77
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9eacd3802c51cb6ccf3f7ba874c75a2d2774439d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59091185"
---
# <a name="iclrcontrolsetappdomainmanagertype-method"></a><span data-ttu-id="176a4-102">ICLRControl::SetAppDomainManagerType – metoda</span><span class="sxs-lookup"><span data-stu-id="176a4-102">ICLRControl::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="176a4-103">Nastaví typ odvozený z <xref:System.AppDomainManager> jako typ pro správce domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="176a4-103">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="176a4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="176a4-104">Syntax</span></span>  
  
```  
HRESULT SetAppDomainManagerType (  
    [in] LPCWSTR pwzAppDomainManagerAssembly,  
    [in] LPCWSTR pwzAppDomainManagerType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="176a4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="176a4-105">Parameters</span></span>  
 `pwzAppDomainManagerAssembly`  
 <span data-ttu-id="176a4-106">[in] Název sestavení, ve kterém požadovaný typ odvozený od <xref:System.AppDomainManager> je implementováno.</span><span class="sxs-lookup"><span data-stu-id="176a4-106">[in] The name of the assembly in which the requested type derived from <xref:System.AppDomainManager> is implemented.</span></span>  
  
 `pwzAppDomainManagerType`  
 <span data-ttu-id="176a4-107">[in] Název typu implementované v `pwzAppDomainManagerAssembly` parametr, který implementuje funkce <xref:System.AppDomainManager>.</span><span class="sxs-lookup"><span data-stu-id="176a4-107">[in] The name of the type implemented in the `pwzAppDomainManagerAssembly` parameter that implements the capabilities of <xref:System.AppDomainManager>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="176a4-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="176a4-108">Return Value</span></span>  
  
|<span data-ttu-id="176a4-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="176a4-109">HRESULT</span></span>|<span data-ttu-id="176a4-110">Popis</span><span class="sxs-lookup"><span data-stu-id="176a4-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="176a4-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="176a4-111">S_OK</span></span>|<span data-ttu-id="176a4-112">Metoda vrátila úspěšně.</span><span class="sxs-lookup"><span data-stu-id="176a4-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="176a4-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="176a4-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="176a4-114">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="176a4-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="176a4-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="176a4-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="176a4-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="176a4-116">The call timed out.</span></span>|  
|<span data-ttu-id="176a4-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="176a4-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="176a4-118">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="176a4-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="176a4-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="176a4-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="176a4-120">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="176a4-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="176a4-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="176a4-121">E_FAIL</span></span>|<span data-ttu-id="176a4-122">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="176a4-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="176a4-123">Po návratu metoda E_FAIL CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="176a4-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="176a4-124">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="176a4-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="176a4-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="176a4-125">Requirements</span></span>  
 <span data-ttu-id="176a4-126">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="176a4-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="176a4-127">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="176a4-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="176a4-128">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="176a4-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="176a4-129">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="176a4-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="176a4-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="176a4-130">See also</span></span>

- [<span data-ttu-id="176a4-131">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="176a4-131">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="176a4-132">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="176a4-132">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
