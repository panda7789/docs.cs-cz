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
ms.openlocfilehash: bf285b6e1f703c8776937fa33c7ab5801f04f80f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950163"
---
# <a name="iclrappdomainresourcemonitorgetcurrentsurvived-method"></a><span data-ttu-id="4da86-102">ICLRAppDomainResourceMonitor::GetCurrentSurvived – metoda</span><span class="sxs-lookup"><span data-stu-id="4da86-102">ICLRAppDomainResourceMonitor::GetCurrentSurvived Method</span></span>
<span data-ttu-id="4da86-103">Vrátí počet bajtů, které byly zachovány při posledním plném, blokování uvolnění paměti a odkazují aktuální doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="4da86-103">Gets the number of bytes that survived the last full, blocking garbage collection and that are referenced by the current application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4da86-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4da86-104">Syntax</span></span>  
  
```cpp  
HRESULT STDMETHODCALLTYPE GetCurrentSurvived(  
             [in]  DWORD dwAppDomainId,  
             [out] ULONGLONG *pAppDomainBytesSurvived,  
             [out] ULONGLONG *pTotalBytesSurvived);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4da86-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4da86-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="4da86-106">pro ID požadované aplikační domény</span><span class="sxs-lookup"><span data-stu-id="4da86-106">[in] The ID of the requested application domain.</span></span>  
  
 `pAppDomainBytesSurvived`  
 <span data-ttu-id="4da86-107">mimo Ukazatel na počet bajtů, které byly zachovány po posledním uvolňování paměti, které jsou uloženy touto doménou aplikace.</span><span class="sxs-lookup"><span data-stu-id="4da86-107">[out] A pointer to the number of bytes that survived after the last garbage collection that are held by this application domain.</span></span> <span data-ttu-id="4da86-108">Po úplné kolekci je toto číslo přesné a úplné.</span><span class="sxs-lookup"><span data-stu-id="4da86-108">After a full collection, this number is accurate and complete.</span></span> <span data-ttu-id="4da86-109">Po dočasné kolekci je toto číslo potenciálně neúplné.</span><span class="sxs-lookup"><span data-stu-id="4da86-109">After an ephemeral collection, this number is potentially incomplete.</span></span> <span data-ttu-id="4da86-110">Tento parametr může být `null`.</span><span class="sxs-lookup"><span data-stu-id="4da86-110">This parameter can be `null`.</span></span>  
  
 `pRuntimeBytesSurvived`  
 <span data-ttu-id="4da86-111">mimo Ukazatel na celkový počet bajtů, které byly zachovány z posledního uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="4da86-111">[out] A pointer to the total number of bytes that survived from the last garbage collection.</span></span> <span data-ttu-id="4da86-112">Po úplné kolekci představuje toto číslo počet bajtů, které jsou uloženy ve spravovaných haldách.</span><span class="sxs-lookup"><span data-stu-id="4da86-112">After a full collection, this number represents the number of the bytes that are held in managed heaps.</span></span> <span data-ttu-id="4da86-113">Po dočasné kolekci představuje toto číslo počet bajtů, které jsou v dočasných generacích uloženy v reálném čase.</span><span class="sxs-lookup"><span data-stu-id="4da86-113">After an ephemeral collection, this number represents the number of bytes that are held live in ephemeral generations.</span></span> <span data-ttu-id="4da86-114">Tento parametr může být `null`.</span><span class="sxs-lookup"><span data-stu-id="4da86-114">This parameter can be `null`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4da86-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4da86-115">Return Value</span></span>  
 <span data-ttu-id="4da86-116">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="4da86-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="4da86-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4da86-117">HRESULT</span></span>|<span data-ttu-id="4da86-118">Popis</span><span class="sxs-lookup"><span data-stu-id="4da86-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4da86-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="4da86-119">S_OK</span></span>|<span data-ttu-id="4da86-120">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="4da86-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="4da86-121">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="4da86-121">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="4da86-122">Doména aplikace byla uvolněna nebo neexistuje.</span><span class="sxs-lookup"><span data-stu-id="4da86-122">The application domain has been unloaded or does not exist.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4da86-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4da86-123">Remarks</span></span>  
 <span data-ttu-id="4da86-124">Statistika se aktualizuje až po úplném a blokujícím uvolňování paměti. To znamená, že kolekce obsahující všechny generace a zastavuje aplikaci, když dojde ke shromažďování.</span><span class="sxs-lookup"><span data-stu-id="4da86-124">Statistics are updated only after a full, blocking garbage collection; that is, a collection that includes all generations and that stops the application while collection occurs.</span></span> <span data-ttu-id="4da86-125">Například <xref:System.GC.Collect?displayProperty=nameWithType> přetížení metody provádí úplnou, blokující kolekci.</span><span class="sxs-lookup"><span data-stu-id="4da86-125">For example, the <xref:System.GC.Collect?displayProperty=nameWithType> method overload performs a full, blocking collection.</span></span> <span data-ttu-id="4da86-126">Souběžné uvolňování paměti probíhá na pozadí a neblokuje aplikaci.</span><span class="sxs-lookup"><span data-stu-id="4da86-126">Concurrent garbage collection occurs in the background and does not block the application.</span></span>  
  
 <span data-ttu-id="4da86-127">Metoda je nespravovaný ekvivalent spravované <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> vlastnosti. `GetCurrentSurvived`</span><span class="sxs-lookup"><span data-stu-id="4da86-127">The `GetCurrentSurvived` method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4da86-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4da86-128">Requirements</span></span>  
 <span data-ttu-id="4da86-129">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4da86-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4da86-130">**Hlaviček** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="4da86-130">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="4da86-131">**Knihovna** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4da86-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4da86-132">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4da86-132">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4da86-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4da86-133">See also</span></span>

- [<span data-ttu-id="4da86-134">ICLRAppDomainResourceMonitor – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4da86-134">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)
- [<span data-ttu-id="4da86-135">Sledování prostředků domény aplikace</span><span class="sxs-lookup"><span data-stu-id="4da86-135">Application Domain Resource Monitoring</span></span>](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="4da86-136">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="4da86-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="4da86-137">Hostování</span><span class="sxs-lookup"><span data-stu-id="4da86-137">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
