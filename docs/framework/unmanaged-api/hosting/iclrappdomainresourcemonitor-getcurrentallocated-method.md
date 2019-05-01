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
ms.openlocfilehash: 7fcd7a3aa1a6c034985099c24071429384563700
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61985293"
---
# <a name="iclrappdomainresourcemonitorgetcurrentallocated-method"></a><span data-ttu-id="f1bb7-102">ICLRAppDomainResourceMonitor::GetCurrentAllocated – metoda</span><span class="sxs-lookup"><span data-stu-id="f1bb7-102">ICLRAppDomainResourceMonitor::GetCurrentAllocated Method</span></span>
<span data-ttu-id="f1bb7-103">Získá celková velikost v bajtech, všechna přidělení paměti, které byly provedeny podle domény aplikace protože byl vytvořen bez odečtením paměti, která byla uvolněna.</span><span class="sxs-lookup"><span data-stu-id="f1bb7-103">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1bb7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f1bb7-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentAllocated([in]  DWORD dwAppDomainId,  
                            [out] ULONGLONG* pBytesAllocated);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1bb7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f1bb7-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="f1bb7-106">[in] ID domény požadované aplikace.</span><span class="sxs-lookup"><span data-stu-id="f1bb7-106">[in] The ID of the requested application domain.</span></span>  
  
 `pBytesAllocated`  
 <span data-ttu-id="f1bb7-107">[out] Ukazatel na celkovou velikost všechna přidělení paměti.</span><span class="sxs-lookup"><span data-stu-id="f1bb7-107">[out] A pointer to the total size of all memory allocations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f1bb7-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f1bb7-108">Return Value</span></span>  
 <span data-ttu-id="f1bb7-109">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="f1bb7-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="f1bb7-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f1bb7-110">HRESULT</span></span>|<span data-ttu-id="f1bb7-111">Popis</span><span class="sxs-lookup"><span data-stu-id="f1bb7-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f1bb7-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="f1bb7-112">S_OK</span></span>|<span data-ttu-id="f1bb7-113">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="f1bb7-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="f1bb7-114">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="f1bb7-114">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="f1bb7-115">Aplikační domény byl odpojen nebo neexistuje.</span><span class="sxs-lookup"><span data-stu-id="f1bb7-115">The application domain has been unloaded or does not exist.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1bb7-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f1bb7-116">Remarks</span></span>  
 <span data-ttu-id="f1bb7-117">Tato metoda odpovídá nespravované spravované <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f1bb7-117">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1bb7-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f1bb7-118">Requirements</span></span>  
 <span data-ttu-id="f1bb7-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1bb7-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1bb7-120">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="f1bb7-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f1bb7-121">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f1bb7-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f1bb7-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1bb7-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1bb7-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f1bb7-123">See also</span></span>

- [<span data-ttu-id="f1bb7-124">ICLRAppDomainResourceMonitor – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f1bb7-124">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)
- [<span data-ttu-id="f1bb7-125">Sledování prostředků domény aplikace</span><span class="sxs-lookup"><span data-stu-id="f1bb7-125">Application Domain Resource Monitoring</span></span>](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="f1bb7-126">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="f1bb7-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="f1bb7-127">Hostování</span><span class="sxs-lookup"><span data-stu-id="f1bb7-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
