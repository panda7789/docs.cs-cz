---
title: "ICLRAppDomainResourceMonitor::GetCurrentSurvived – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAppDomainResourceMonitor.GetCurrentSurvived
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAppDomainResourceMonitor::GetCurrentSurvived
helpviewer_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentSurvived method [.NET Framework hosting]
- GetCurrentSurvived method [.NET Framework hosting]
ms.assetid: 392e9009-40ef-40e3-ad4d-7ce93a989e78
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b9fe624c83be5dcf762f1c6036f8e4264f0e45c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrappdomainresourcemonitorgetcurrentsurvived-method"></a><span data-ttu-id="d4398-102">ICLRAppDomainResourceMonitor::GetCurrentSurvived – metoda</span><span class="sxs-lookup"><span data-stu-id="d4398-102">ICLRAppDomainResourceMonitor::GetCurrentSurvived Method</span></span>
<span data-ttu-id="d4398-103">Získá počet bajtů, který zůstal naživu poslední úplné, blokování uvolňování paměti a který se odkazuje aktuální doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="d4398-103">Gets the number of bytes that survived the last full, blocking garbage collection and that are referenced by the current application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4398-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4398-104">Syntax</span></span>  
  
```  
HRESULT STDMETHODCALLTYPE GetCurrentSurvived(  
             [in]  DWORD dwAppDomainId,  
             [out] ULONGLONG *pAppDomainBytesSurvived,  
             [out] ULONGLONG *pTotalBytesSurvived);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d4398-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d4398-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="d4398-106">[v] ID domény požadovaná aplikace.</span><span class="sxs-lookup"><span data-stu-id="d4398-106">[in] The ID of the requested application domain.</span></span>  
  
 `pAppDomainBytesSurvived`  
 <span data-ttu-id="d4398-107">[out] Ukazatel na počet bajtů, které zůstal naživu po poslední uvolnění paměti, které jsou uložené tato doména aplikace.</span><span class="sxs-lookup"><span data-stu-id="d4398-107">[out] A pointer to the number of bytes that survived after the last garbage collection that are held by this application domain.</span></span> <span data-ttu-id="d4398-108">Toto číslo po úplnou kolekci, je přesné a úplné.</span><span class="sxs-lookup"><span data-stu-id="d4398-108">After a full collection, this number is accurate and complete.</span></span> <span data-ttu-id="d4398-109">Toto číslo je po dočasné kolekce, potenciálně neúplné.</span><span class="sxs-lookup"><span data-stu-id="d4398-109">After an ephemeral collection, this number is potentially incomplete.</span></span> <span data-ttu-id="d4398-110">Tento parametr může být `null`.</span><span class="sxs-lookup"><span data-stu-id="d4398-110">This parameter can be `null`.</span></span>  
  
 `pRuntimeBytesSurvived`  
 <span data-ttu-id="d4398-111">[out] Ukazatel na celkový počet bajtů, které zůstal naživu z poslední uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="d4398-111">[out] A pointer to the total number of bytes that survived from the last garbage collection.</span></span> <span data-ttu-id="d4398-112">Po kompletní sadu toto číslo představuje počet bajtů, které jsou uložené ve spravovaných haldách.</span><span class="sxs-lookup"><span data-stu-id="d4398-112">After a full collection, this number represents the number of the bytes that are held in managed heaps.</span></span> <span data-ttu-id="d4398-113">Po dočasné kolekce toto číslo představuje počet bajtů, které jsou uložené v dočasných generace za provozu.</span><span class="sxs-lookup"><span data-stu-id="d4398-113">After an ephemeral collection, this number represents the number of bytes that are held live in ephemeral generations.</span></span> <span data-ttu-id="d4398-114">Tento parametr může být `null`.</span><span class="sxs-lookup"><span data-stu-id="d4398-114">This parameter can be `null`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d4398-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d4398-115">Return Value</span></span>  
 <span data-ttu-id="d4398-116">Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.</span><span class="sxs-lookup"><span data-stu-id="d4398-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="d4398-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d4398-117">HRESULT</span></span>|<span data-ttu-id="d4398-118">Popis</span><span class="sxs-lookup"><span data-stu-id="d4398-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d4398-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="d4398-119">S_OK</span></span>|<span data-ttu-id="d4398-120">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="d4398-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="d4398-121">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="d4398-121">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="d4398-122">Doména aplikace byl odpojen nebo neexistuje.</span><span class="sxs-lookup"><span data-stu-id="d4398-122">The application domain has been unloaded or does not exist.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4398-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d4398-123">Remarks</span></span>  
 <span data-ttu-id="d4398-124">Se statistika aktualizuje až po úplné, blokování uvolňování; To znamená dojde k kolekci, která obsahuje všechny generace a který ukončí aplikaci při kolekce.</span><span class="sxs-lookup"><span data-stu-id="d4398-124">Statistics are updated only after a full, blocking garbage collection; that is, a collection that includes all generations and that stops the application while collection occurs.</span></span> <span data-ttu-id="d4398-125">Například <xref:System.GC.Collect?displayProperty=nameWithType> přetížení metody provede úplnou, blokování kolekce.</span><span class="sxs-lookup"><span data-stu-id="d4398-125">For example, the <xref:System.GC.Collect?displayProperty=nameWithType> method overload performs a full, blocking collection.</span></span> <span data-ttu-id="d4398-126">Souběžné uvolňování probíhá na pozadí a neblokuje aplikace.</span><span class="sxs-lookup"><span data-stu-id="d4398-126">Concurrent garbage collection occurs in the background and does not block the application.</span></span>  
  
 <span data-ttu-id="d4398-127">`GetCurrentSurvived` Metoda je ekvivalentem nespravované spravované <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d4398-127">The `GetCurrentSurvived` method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4398-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d4398-128">Requirements</span></span>  
 <span data-ttu-id="d4398-129">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4398-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4398-130">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="d4398-130">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d4398-131">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d4398-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d4398-132">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4398-132">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4398-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="d4398-133">See Also</span></span>  
 [<span data-ttu-id="d4398-134">Iclrappdomainresourcemonitor – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d4398-134">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 [<span data-ttu-id="d4398-135">Prostředků domény aplikace monitorování</span><span class="sxs-lookup"><span data-stu-id="d4398-135">Application Domain Resource Monitoring</span></span>](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)  
 [<span data-ttu-id="d4398-136">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="d4398-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="d4398-137">Hostování</span><span class="sxs-lookup"><span data-stu-id="d4398-137">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
