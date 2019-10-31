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
ms.openlocfilehash: f19ac39737d08c10c23ce0bde03131f52b660cac
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126818"
---
# <a name="iclrappdomainresourcemonitorgetcurrentallocated-method"></a><span data-ttu-id="97906-102">ICLRAppDomainResourceMonitor::GetCurrentAllocated – metoda</span><span class="sxs-lookup"><span data-stu-id="97906-102">ICLRAppDomainResourceMonitor::GetCurrentAllocated Method</span></span>
<span data-ttu-id="97906-103">Získá celkovou velikost přidělení paměti (v bajtech), která byla vytvořena aplikační doménou od jejího vytvoření, bez odčítání paměti, která byla uvolněna do paměti.</span><span class="sxs-lookup"><span data-stu-id="97906-103">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97906-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="97906-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentAllocated([in]  DWORD dwAppDomainId,  
                            [out] ULONGLONG* pBytesAllocated);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97906-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="97906-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="97906-106">pro ID požadované aplikační domény</span><span class="sxs-lookup"><span data-stu-id="97906-106">[in] The ID of the requested application domain.</span></span>  
  
 `pBytesAllocated`  
 <span data-ttu-id="97906-107">mimo Ukazatel na celkovou velikost všech přidělení paměti.</span><span class="sxs-lookup"><span data-stu-id="97906-107">[out] A pointer to the total size of all memory allocations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="97906-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="97906-108">Return Value</span></span>  
 <span data-ttu-id="97906-109">Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.</span><span class="sxs-lookup"><span data-stu-id="97906-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="97906-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="97906-110">HRESULT</span></span>|<span data-ttu-id="97906-111">Popis</span><span class="sxs-lookup"><span data-stu-id="97906-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="97906-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="97906-112">S_OK</span></span>|<span data-ttu-id="97906-113">Metoda byla úspěšně dokončena.</span><span class="sxs-lookup"><span data-stu-id="97906-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="97906-114">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="97906-114">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="97906-115">Doména aplikace byla uvolněna nebo neexistuje.</span><span class="sxs-lookup"><span data-stu-id="97906-115">The application domain has been unloaded or does not exist.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97906-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="97906-116">Remarks</span></span>  
 <span data-ttu-id="97906-117">Tato metoda je nespravovaný ekvivalent vlastnosti Managed <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="97906-117">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97906-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="97906-118">Requirements</span></span>  
 <span data-ttu-id="97906-119">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97906-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97906-120">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="97906-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="97906-121">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="97906-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="97906-122">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97906-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97906-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="97906-123">See also</span></span>

- [<span data-ttu-id="97906-124">ICLRAppDomainResourceMonitor – rozhraní</span><span class="sxs-lookup"><span data-stu-id="97906-124">ICLRAppDomainResourceMonitor Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)
- [<span data-ttu-id="97906-125">Sledování prostředků domény aplikace</span><span class="sxs-lookup"><span data-stu-id="97906-125">Application Domain Resource Monitoring</span></span>](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="97906-126">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="97906-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="97906-127">Hostování</span><span class="sxs-lookup"><span data-stu-id="97906-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
