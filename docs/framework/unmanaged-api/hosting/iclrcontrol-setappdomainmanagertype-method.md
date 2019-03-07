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
ms.openlocfilehash: bb1632b5d9379eb35d4188a218f3184acf8d0ed3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497103"
---
# <a name="iclrcontrolsetappdomainmanagertype-method"></a><span data-ttu-id="4c660-102">ICLRControl::SetAppDomainManagerType – metoda</span><span class="sxs-lookup"><span data-stu-id="4c660-102">ICLRControl::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="4c660-103">Nastaví typ odvozený z <xref:System.AppDomainManager> jako typ pro správce domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="4c660-103">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c660-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4c660-104">Syntax</span></span>  
  
```  
HRESULT SetAppDomainManagerType (  
    [in] LPCWSTR pwzAppDomainManagerAssembly,  
    [in] LPCWSTR pwzAppDomainManagerType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c660-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4c660-105">Parameters</span></span>  
 `pwzAppDomainManagerAssembly`  
 <span data-ttu-id="4c660-106">[in] Název sestavení, ve kterém požadovaný typ odvozený od <xref:System.AppDomainManager> je implementováno.</span><span class="sxs-lookup"><span data-stu-id="4c660-106">[in] The name of the assembly in which the requested type derived from <xref:System.AppDomainManager> is implemented.</span></span>  
  
 `pwzAppDomainManagerType`  
 <span data-ttu-id="4c660-107">[in] Název typu implementované v `pwzAppDomainManagerAssembly` parametr, který implementuje funkce <xref:System.AppDomainManager>.</span><span class="sxs-lookup"><span data-stu-id="4c660-107">[in] The name of the type implemented in the `pwzAppDomainManagerAssembly` parameter that implements the capabilities of <xref:System.AppDomainManager>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4c660-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4c660-108">Return Value</span></span>  
  
|<span data-ttu-id="4c660-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4c660-109">HRESULT</span></span>|<span data-ttu-id="4c660-110">Popis</span><span class="sxs-lookup"><span data-stu-id="4c660-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4c660-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="4c660-111">S_OK</span></span>|<span data-ttu-id="4c660-112">Metoda vrátila úspěšně.</span><span class="sxs-lookup"><span data-stu-id="4c660-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="4c660-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4c660-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4c660-114">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="4c660-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4c660-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4c660-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4c660-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="4c660-116">The call timed out.</span></span>|  
|<span data-ttu-id="4c660-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4c660-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4c660-118">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="4c660-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4c660-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4c660-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4c660-120">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="4c660-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4c660-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4c660-121">E_FAIL</span></span>|<span data-ttu-id="4c660-122">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="4c660-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4c660-123">Po návratu metoda E_FAIL CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="4c660-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4c660-124">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4c660-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4c660-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4c660-125">Requirements</span></span>  
 <span data-ttu-id="4c660-126">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c660-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c660-127">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4c660-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4c660-128">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4c660-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4c660-129">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c660-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c660-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4c660-130">See also</span></span>
- [<span data-ttu-id="4c660-131">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4c660-131">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="4c660-132">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4c660-132">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
