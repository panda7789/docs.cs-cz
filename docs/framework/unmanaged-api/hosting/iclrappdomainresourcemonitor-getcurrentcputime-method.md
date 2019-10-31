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
ms.openlocfilehash: de57fec05c338e51d0691ccfa0d0bffb334848de
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126789"
---
# <a name="iclrappdomainresourcemonitorgetcurrentcputime-method"></a><span data-ttu-id="a7b57-102">ICLRAppDomainResourceMonitor::GetCurrentCpuTime – metoda</span><span class="sxs-lookup"><span data-stu-id="a7b57-102">ICLRAppDomainResourceMonitor::GetCurrentCpuTime Method</span></span>
<span data-ttu-id="a7b57-103">Získá celkový čas procesoru používaný všemi vlákny při spuštění v aktuální doméně aplikace, protože byla vytvořena doména aplikace.</span><span class="sxs-lookup"><span data-stu-id="a7b57-103">Gets the total processor time that has been used by all threads while executing in the current application domain, since the application domain was created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7b57-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a7b57-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentCpuTime([in]  DWORD dwAppDomainId,  
                          [out] ULONGLONG* pMilliseconds);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7b57-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7b57-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="a7b57-106">pro ID požadované aplikační domény</span><span class="sxs-lookup"><span data-stu-id="a7b57-106">[in] The ID of the requested application domain.</span></span>  
  
 `pMilliseconds`  
 <span data-ttu-id="a7b57-107">mimo Ukazatel na celkový čas procesoru, který byl použit všemi vlákny při spuštění v aktuální doméně aplikace od vytvoření domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="a7b57-107">[out] A pointer to the total processor time that has been used by all threads while executing in the current application domain since the application domain was created.</span></span> <span data-ttu-id="a7b57-108">Tento parametr může být `null`.</span><span class="sxs-lookup"><span data-stu-id="a7b57-108">This parameter can be `null`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a7b57-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a7b57-109">Return Value</span></span>  
  
|<span data-ttu-id="a7b57-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a7b57-110">HRESULT</span></span>|<span data-ttu-id="a7b57-111">Popis</span><span class="sxs-lookup"><span data-stu-id="a7b57-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a7b57-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="a7b57-112">S_OK</span></span>|<span data-ttu-id="a7b57-113">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="a7b57-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="a7b57-114">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="a7b57-114">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="a7b57-115">Doména aplikace byla uvolněna nebo neexistuje.</span><span class="sxs-lookup"><span data-stu-id="a7b57-115">The application domain has been unloaded or does not exist.</span></span>|  
|<span data-ttu-id="a7b57-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a7b57-116">E_FAIL</span></span>|<span data-ttu-id="a7b57-117">Monitorování prostředků domény aplikace není povoleno.</span><span class="sxs-lookup"><span data-stu-id="a7b57-117">Application domain resource monitoring is not enabled.</span></span><br /><br /> <span data-ttu-id="a7b57-118">-nebo-</span><span class="sxs-lookup"><span data-stu-id="a7b57-118">-or-</span></span><br /><br /> <span data-ttu-id="a7b57-119">Všechny ostatní chyby.</span><span class="sxs-lookup"><span data-stu-id="a7b57-119">All other failures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7b57-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a7b57-120">Remarks</span></span>  
 <span data-ttu-id="a7b57-121">Tato metoda je nespravovaný ekvivalent vlastnosti Managed <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a7b57-121">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7b57-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a7b57-122">Requirements</span></span>  
 <span data-ttu-id="a7b57-123">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7b57-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7b57-124">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="a7b57-124">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a7b57-125">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a7b57-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a7b57-126">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7b57-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7b57-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a7b57-127">See also</span></span>

- [<span data-ttu-id="a7b57-128">ICLRAppDomainResourceMonitor – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a7b57-128">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)
- [<span data-ttu-id="a7b57-129">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="a7b57-129">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="a7b57-130">Sledování prostředků domény aplikace</span><span class="sxs-lookup"><span data-stu-id="a7b57-130">Application Domain Resource Monitoring</span></span>](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="a7b57-131">Hostování</span><span class="sxs-lookup"><span data-stu-id="a7b57-131">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
