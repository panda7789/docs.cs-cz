---
title: "ICLRAppDomainResourceMonitor::GetCurrentCpuTime – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAppDomainResourceMonitor.GetCurrentCpuTime
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAppDomainResourceMonitor::GetCurrentCpuTime
helpviewer_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentCpuTime method [.NET Framework hosting]
- GetCurrentCpuTime method [.NET Framework hosting]
ms.assetid: ebc9cc33-fcd6-4cae-9ecb-ea21c51874e6
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2483165de54cd5ec76abad9d8472e0deef28f149
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrappdomainresourcemonitorgetcurrentcputime-method"></a><span data-ttu-id="b127f-102">ICLRAppDomainResourceMonitor::GetCurrentCpuTime – metoda</span><span class="sxs-lookup"><span data-stu-id="b127f-102">ICLRAppDomainResourceMonitor::GetCurrentCpuTime Method</span></span>
<span data-ttu-id="b127f-103">Získá celkový procesorového času, který byl použit pro všechna vlákna při provádění v aktuální doméně aplikace, že se od vytvoření domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="b127f-103">Gets the total processor time that has been used by all threads while executing in the current application domain, since the application domain was created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b127f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b127f-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentCpuTime([in]  DWORD dwAppDomainId,  
                          [out] ULONGLONG* pMilliseconds);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b127f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b127f-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="b127f-106">[v] ID domény požadovaná aplikace.</span><span class="sxs-lookup"><span data-stu-id="b127f-106">[in] The ID of the requested application domain.</span></span>  
  
 `pMilliseconds`  
 <span data-ttu-id="b127f-107">[out] Ukazatel na celkový procesorový čas, který byl použit pro všechna vlákna při provádění v aktuální doméně aplikace od vytvoření domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="b127f-107">[out] A pointer to the total processor time that has been used by all threads while executing in the current application domain since the application domain was created.</span></span> <span data-ttu-id="b127f-108">Tento parametr může být `null`.</span><span class="sxs-lookup"><span data-stu-id="b127f-108">This parameter can be `null`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b127f-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b127f-109">Return Value</span></span>  
  
|<span data-ttu-id="b127f-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b127f-110">HRESULT</span></span>|<span data-ttu-id="b127f-111">Popis</span><span class="sxs-lookup"><span data-stu-id="b127f-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b127f-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="b127f-112">S_OK</span></span>|<span data-ttu-id="b127f-113">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="b127f-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="b127f-114">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="b127f-114">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="b127f-115">Doména aplikace byl odpojen nebo neexistuje.</span><span class="sxs-lookup"><span data-stu-id="b127f-115">The application domain has been unloaded or does not exist.</span></span>|  
|<span data-ttu-id="b127f-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b127f-116">E_FAIL</span></span>|<span data-ttu-id="b127f-117">Sledování prostředků domény aplikace není povoleno.</span><span class="sxs-lookup"><span data-stu-id="b127f-117">Application domain resource monitoring is not enabled.</span></span><br /><br /> <span data-ttu-id="b127f-118">-nebo-</span><span class="sxs-lookup"><span data-stu-id="b127f-118">-or-</span></span><br /><br /> <span data-ttu-id="b127f-119">Jiné chyby.</span><span class="sxs-lookup"><span data-stu-id="b127f-119">All other failures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b127f-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b127f-120">Remarks</span></span>  
 <span data-ttu-id="b127f-121">Tato metoda je ekvivalentem nespravované spravované <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b127f-121">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b127f-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b127f-122">Requirements</span></span>  
 <span data-ttu-id="b127f-123">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b127f-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b127f-124">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="b127f-124">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="b127f-125">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b127f-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b127f-126">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b127f-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b127f-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="b127f-127">See Also</span></span>  
 [<span data-ttu-id="b127f-128">Iclrappdomainresourcemonitor – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b127f-128">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 [<span data-ttu-id="b127f-129">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="b127f-129">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="b127f-130">Prostředků domény aplikace monitorování</span><span class="sxs-lookup"><span data-stu-id="b127f-130">Application Domain Resource Monitoring</span></span>](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)  
 [<span data-ttu-id="b127f-131">Hostování</span><span class="sxs-lookup"><span data-stu-id="b127f-131">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
