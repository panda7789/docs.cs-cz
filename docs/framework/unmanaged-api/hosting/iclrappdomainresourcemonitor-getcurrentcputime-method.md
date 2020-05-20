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
ms.openlocfilehash: b411190ff36410c1d293f1e48b31975be8a13aee
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616031"
---
# <a name="iclrappdomainresourcemonitorgetcurrentcputime-method"></a><span data-ttu-id="e411a-102">ICLRAppDomainResourceMonitor::GetCurrentCpuTime – metoda</span><span class="sxs-lookup"><span data-stu-id="e411a-102">ICLRAppDomainResourceMonitor::GetCurrentCpuTime Method</span></span>
<span data-ttu-id="e411a-103">Získá celkový čas procesoru používaný všemi vlákny při spuštění v aktuální doméně aplikace, protože byla vytvořena doména aplikace.</span><span class="sxs-lookup"><span data-stu-id="e411a-103">Gets the total processor time that has been used by all threads while executing in the current application domain, since the application domain was created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e411a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e411a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentCpuTime([in]  DWORD dwAppDomainId,  
                          [out] ULONGLONG* pMilliseconds);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e411a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e411a-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="e411a-106">pro ID požadované aplikační domény</span><span class="sxs-lookup"><span data-stu-id="e411a-106">[in] The ID of the requested application domain.</span></span>  
  
 `pMilliseconds`  
 <span data-ttu-id="e411a-107">mimo Ukazatel na celkový čas procesoru, který byl použit všemi vlákny při spuštění v aktuální doméně aplikace od vytvoření domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="e411a-107">[out] A pointer to the total processor time that has been used by all threads while executing in the current application domain since the application domain was created.</span></span> <span data-ttu-id="e411a-108">Tento parametr může být `null` .</span><span class="sxs-lookup"><span data-stu-id="e411a-108">This parameter can be `null`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e411a-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e411a-109">Return Value</span></span>  
  
|<span data-ttu-id="e411a-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e411a-110">HRESULT</span></span>|<span data-ttu-id="e411a-111">Popis</span><span class="sxs-lookup"><span data-stu-id="e411a-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e411a-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="e411a-112">S_OK</span></span>|<span data-ttu-id="e411a-113">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="e411a-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="e411a-114">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="e411a-114">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="e411a-115">Doména aplikace byla uvolněna nebo neexistuje.</span><span class="sxs-lookup"><span data-stu-id="e411a-115">The application domain has been unloaded or does not exist.</span></span>|  
|<span data-ttu-id="e411a-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e411a-116">E_FAIL</span></span>|<span data-ttu-id="e411a-117">Monitorování prostředků domény aplikace není povoleno.</span><span class="sxs-lookup"><span data-stu-id="e411a-117">Application domain resource monitoring is not enabled.</span></span><br /><br /> <span data-ttu-id="e411a-118">-nebo-</span><span class="sxs-lookup"><span data-stu-id="e411a-118">-or-</span></span><br /><br /> <span data-ttu-id="e411a-119">Všechny ostatní chyby.</span><span class="sxs-lookup"><span data-stu-id="e411a-119">All other failures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e411a-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e411a-120">Remarks</span></span>  
 <span data-ttu-id="e411a-121">Tato metoda je nespravovaný ekvivalent spravované <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e411a-121">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e411a-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e411a-122">Requirements</span></span>  
 <span data-ttu-id="e411a-123">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e411a-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e411a-124">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="e411a-124">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e411a-125">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e411a-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e411a-126">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e411a-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e411a-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="e411a-127">See also</span></span>

- [<span data-ttu-id="e411a-128">ICLRAppDomainResourceMonitor – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e411a-128">ICLRAppDomainResourceMonitor Interface</span></span>](iclrappdomainresourcemonitor-interface.md)
- [<span data-ttu-id="e411a-129">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="e411a-129">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="e411a-130">Monitorování prostředků domény aplikace</span><span class="sxs-lookup"><span data-stu-id="e411a-130">Application Domain Resource Monitoring</span></span>](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="e411a-131">Hostování</span><span class="sxs-lookup"><span data-stu-id="e411a-131">Hosting</span></span>](index.md)
