---
title: ICLRAppDomainResourceMonitor::GetCurrentCpuTime – metoda
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentCpuTime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentCpuTime
helpviewer_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentCpuTime method [.NET Framework hosting]
- GetCurrentCpuTime method [.NET Framework hosting]
ms.assetid: ebc9cc33-fcd6-4cae-9ecb-ea21c51874e6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8022428c7f803f96e2fa150588edf95542bf19b3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61985215"
---
# <a name="iclrappdomainresourcemonitorgetcurrentcputime-method"></a><span data-ttu-id="49236-102">ICLRAppDomainResourceMonitor::GetCurrentCpuTime – metoda</span><span class="sxs-lookup"><span data-stu-id="49236-102">ICLRAppDomainResourceMonitor::GetCurrentCpuTime Method</span></span>
<span data-ttu-id="49236-103">Získá celkový procesorový čas, který byl použit pro všemi vlákny při provádění v aktuální doméně aplikace, od vytvoření domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="49236-103">Gets the total processor time that has been used by all threads while executing in the current application domain, since the application domain was created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49236-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="49236-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentCpuTime([in]  DWORD dwAppDomainId,  
                          [out] ULONGLONG* pMilliseconds);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49236-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="49236-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="49236-106">[in] ID domény požadované aplikace.</span><span class="sxs-lookup"><span data-stu-id="49236-106">[in] The ID of the requested application domain.</span></span>  
  
 `pMilliseconds`  
 <span data-ttu-id="49236-107">[out] Ukazatel na celkový procesorový čas, který byl použit všemi vlákny při provádění v aktuální doméně aplikace, od vytvoření domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="49236-107">[out] A pointer to the total processor time that has been used by all threads while executing in the current application domain since the application domain was created.</span></span> <span data-ttu-id="49236-108">Tento parametr může být `null`.</span><span class="sxs-lookup"><span data-stu-id="49236-108">This parameter can be `null`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="49236-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="49236-109">Return Value</span></span>  
  
|<span data-ttu-id="49236-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="49236-110">HRESULT</span></span>|<span data-ttu-id="49236-111">Popis</span><span class="sxs-lookup"><span data-stu-id="49236-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="49236-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="49236-112">S_OK</span></span>|<span data-ttu-id="49236-113">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="49236-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="49236-114">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="49236-114">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="49236-115">Aplikační domény byl odpojen nebo neexistuje.</span><span class="sxs-lookup"><span data-stu-id="49236-115">The application domain has been unloaded or does not exist.</span></span>|  
|<span data-ttu-id="49236-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="49236-116">E_FAIL</span></span>|<span data-ttu-id="49236-117">Sledování prostředků domény aplikace není povoleno.</span><span class="sxs-lookup"><span data-stu-id="49236-117">Application domain resource monitoring is not enabled.</span></span><br /><br /> <span data-ttu-id="49236-118">-nebo-</span><span class="sxs-lookup"><span data-stu-id="49236-118">-or-</span></span><br /><br /> <span data-ttu-id="49236-119">Všechny ostatní chyby.</span><span class="sxs-lookup"><span data-stu-id="49236-119">All other failures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="49236-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="49236-120">Remarks</span></span>  
 <span data-ttu-id="49236-121">Tato metoda odpovídá nespravované spravované <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="49236-121">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49236-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="49236-122">Requirements</span></span>  
 <span data-ttu-id="49236-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49236-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49236-124">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="49236-124">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="49236-125">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="49236-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="49236-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49236-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49236-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="49236-127">See also</span></span>

- [<span data-ttu-id="49236-128">ICLRAppDomainResourceMonitor – rozhraní</span><span class="sxs-lookup"><span data-stu-id="49236-128">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)
- [<span data-ttu-id="49236-129">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="49236-129">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="49236-130">Sledování prostředků domény aplikace</span><span class="sxs-lookup"><span data-stu-id="49236-130">Application Domain Resource Monitoring</span></span>](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="49236-131">Hostování</span><span class="sxs-lookup"><span data-stu-id="49236-131">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
