---
title: ICLRAppDomainResourceMonitor::GetCurrentSurvived – metoda
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentSurvived
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentSurvived
helpviewer_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentSurvived method [.NET Framework hosting]
- GetCurrentSurvived method [.NET Framework hosting]
ms.assetid: 392e9009-40ef-40e3-ad4d-7ce93a989e78
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 408ef5419fbc2081d25ad442986ec8155bcb4c62
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59141541"
---
# <a name="iclrappdomainresourcemonitorgetcurrentsurvived-method"></a><span data-ttu-id="2384d-102">ICLRAppDomainResourceMonitor::GetCurrentSurvived – metoda</span><span class="sxs-lookup"><span data-stu-id="2384d-102">ICLRAppDomainResourceMonitor::GetCurrentSurvived Method</span></span>
<span data-ttu-id="2384d-103">Získá počet bajtů, které zůstat naživu při poslední úplné blokující uvolňování paměti a, který je odkazováno dle aktuální domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="2384d-103">Gets the number of bytes that survived the last full, blocking garbage collection and that are referenced by the current application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2384d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2384d-104">Syntax</span></span>  
  
```  
HRESULT STDMETHODCALLTYPE GetCurrentSurvived(  
             [in]  DWORD dwAppDomainId,  
             [out] ULONGLONG *pAppDomainBytesSurvived,  
             [out] ULONGLONG *pTotalBytesSurvived);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2384d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2384d-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="2384d-106">[in] ID domény požadované aplikace.</span><span class="sxs-lookup"><span data-stu-id="2384d-106">[in] The ID of the requested application domain.</span></span>  
  
 `pAppDomainBytesSurvived`  
 <span data-ttu-id="2384d-107">[out] Ukazatel na počet bajtů, které zůstat naživu po poslední uvolnění paměti, které jsou uloženy v této doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="2384d-107">[out] A pointer to the number of bytes that survived after the last garbage collection that are held by this application domain.</span></span> <span data-ttu-id="2384d-108">Toto číslo po celé kolekce, je přesné a úplné.</span><span class="sxs-lookup"><span data-stu-id="2384d-108">After a full collection, this number is accurate and complete.</span></span> <span data-ttu-id="2384d-109">Toto číslo je po dočasné kolekce, potenciálně neúplné.</span><span class="sxs-lookup"><span data-stu-id="2384d-109">After an ephemeral collection, this number is potentially incomplete.</span></span> <span data-ttu-id="2384d-110">Tento parametr může být `null`.</span><span class="sxs-lookup"><span data-stu-id="2384d-110">This parameter can be `null`.</span></span>  
  
 `pRuntimeBytesSurvived`  
 <span data-ttu-id="2384d-111">[out] Ukazatel na celkový počet bajtů, které zůstat naživu z posledního kolekce uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="2384d-111">[out] A pointer to the total number of bytes that survived from the last garbage collection.</span></span> <span data-ttu-id="2384d-112">Po celé kolekce toto číslo představuje počet bajtů, které jsou uloženy ve spravované haldy.</span><span class="sxs-lookup"><span data-stu-id="2384d-112">After a full collection, this number represents the number of the bytes that are held in managed heaps.</span></span> <span data-ttu-id="2384d-113">Po dočasné kolekce toto číslo představuje počet bajtů, které jsou uloženy v dočasné generace.</span><span class="sxs-lookup"><span data-stu-id="2384d-113">After an ephemeral collection, this number represents the number of bytes that are held live in ephemeral generations.</span></span> <span data-ttu-id="2384d-114">Tento parametr může být `null`.</span><span class="sxs-lookup"><span data-stu-id="2384d-114">This parameter can be `null`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2384d-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2384d-115">Return Value</span></span>  
 <span data-ttu-id="2384d-116">Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="2384d-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="2384d-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2384d-117">HRESULT</span></span>|<span data-ttu-id="2384d-118">Popis</span><span class="sxs-lookup"><span data-stu-id="2384d-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2384d-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="2384d-119">S_OK</span></span>|<span data-ttu-id="2384d-120">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="2384d-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="2384d-121">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="2384d-121">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="2384d-122">Aplikační domény byl odpojen nebo neexistuje.</span><span class="sxs-lookup"><span data-stu-id="2384d-122">The application domain has been unloaded or does not exist.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2384d-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2384d-123">Remarks</span></span>  
 <span data-ttu-id="2384d-124">Statistiky jsou aktualizovány pouze po úplné blokující uvolňování paměti; To znamená, že dojde k kolekci, která obsahuje všechny generace, která ukončí aplikaci při shromažďování.</span><span class="sxs-lookup"><span data-stu-id="2384d-124">Statistics are updated only after a full, blocking garbage collection; that is, a collection that includes all generations and that stops the application while collection occurs.</span></span> <span data-ttu-id="2384d-125">Například <xref:System.GC.Collect?displayProperty=nameWithType> přetížení metody provede úplné blokující kolekce.</span><span class="sxs-lookup"><span data-stu-id="2384d-125">For example, the <xref:System.GC.Collect?displayProperty=nameWithType> method overload performs a full, blocking collection.</span></span> <span data-ttu-id="2384d-126">Souběžné uvolňování paměti probíhá na pozadí a nedochází k blokování aplikace.</span><span class="sxs-lookup"><span data-stu-id="2384d-126">Concurrent garbage collection occurs in the background and does not block the application.</span></span>  
  
 <span data-ttu-id="2384d-127">`GetCurrentSurvived` Metoda odpovídá nespravované spravované <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2384d-127">The `GetCurrentSurvived` method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2384d-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2384d-128">Requirements</span></span>  
 <span data-ttu-id="2384d-129">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2384d-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2384d-130">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="2384d-130">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="2384d-131">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2384d-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="2384d-132">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="2384d-132">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2384d-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2384d-133">See also</span></span>

- [<span data-ttu-id="2384d-134">ICLRAppDomainResourceMonitor – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2384d-134">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)
- [<span data-ttu-id="2384d-135">Sledování prostředků domény aplikace</span><span class="sxs-lookup"><span data-stu-id="2384d-135">Application Domain Resource Monitoring</span></span>](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="2384d-136">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="2384d-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="2384d-137">Hostování</span><span class="sxs-lookup"><span data-stu-id="2384d-137">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
