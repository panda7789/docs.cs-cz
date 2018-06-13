---
title: ICLRAppDomainResourceMonitor::GetCurrentAllocated – metoda
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentAllocated
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentAllocated
helpviewer_keywords:
- GetCurrentAllocated method [.NET Framework hosting]
- ICLRAppDomainResourceMonitor::GetCurrentAllocated method [.NET Framework hosting]
ms.assetid: 7bab209c-efd4-44c2-af30-61abab0ae2fc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4011881e98c109458bf87efcc1b09463c064f23f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431952"
---
# <a name="iclrappdomainresourcemonitorgetcurrentallocated-method"></a><span data-ttu-id="184ea-102">ICLRAppDomainResourceMonitor::GetCurrentAllocated – metoda</span><span class="sxs-lookup"><span data-stu-id="184ea-102">ICLRAppDomainResourceMonitor::GetCurrentAllocated Method</span></span>
<span data-ttu-id="184ea-103">Získá celková velikost v bajtech přidělených paměti, které jste provedli pro doménu aplikace, protože byl vytvořen bez odečtením paměti, která byla uvolněna.</span><span class="sxs-lookup"><span data-stu-id="184ea-103">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="184ea-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="184ea-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentAllocated([in]  DWORD dwAppDomainId,  
                            [out] ULONGLONG* pBytesAllocated);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="184ea-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="184ea-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="184ea-106">[v] ID domény požadovaná aplikace.</span><span class="sxs-lookup"><span data-stu-id="184ea-106">[in] The ID of the requested application domain.</span></span>  
  
 `pBytesAllocated`  
 <span data-ttu-id="184ea-107">[out] Ukazatel na celkovou velikost všech přidělení paměti.</span><span class="sxs-lookup"><span data-stu-id="184ea-107">[out] A pointer to the total size of all memory allocations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="184ea-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="184ea-108">Return Value</span></span>  
 <span data-ttu-id="184ea-109">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="184ea-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="184ea-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="184ea-110">HRESULT</span></span>|<span data-ttu-id="184ea-111">Popis</span><span class="sxs-lookup"><span data-stu-id="184ea-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="184ea-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="184ea-112">S_OK</span></span>|<span data-ttu-id="184ea-113">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="184ea-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="184ea-114">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="184ea-114">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="184ea-115">Doména aplikace byl odpojen nebo neexistuje.</span><span class="sxs-lookup"><span data-stu-id="184ea-115">The application domain has been unloaded or does not exist.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="184ea-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="184ea-116">Remarks</span></span>  
 <span data-ttu-id="184ea-117">Tato metoda je ekvivalentem nespravované spravované <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="184ea-117">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="184ea-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="184ea-118">Requirements</span></span>  
 <span data-ttu-id="184ea-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="184ea-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="184ea-120">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="184ea-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="184ea-121">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="184ea-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="184ea-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="184ea-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="184ea-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="184ea-123">See Also</span></span>  
 [<span data-ttu-id="184ea-124">ICLRAppDomainResourceMonitor – rozhraní</span><span class="sxs-lookup"><span data-stu-id="184ea-124">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 [<span data-ttu-id="184ea-125">Sledování prostředků domény aplikace</span><span class="sxs-lookup"><span data-stu-id="184ea-125">Application Domain Resource Monitoring</span></span>](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)  
 [<span data-ttu-id="184ea-126">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="184ea-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="184ea-127">Hostování</span><span class="sxs-lookup"><span data-stu-id="184ea-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
