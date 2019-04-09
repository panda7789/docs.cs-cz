---
title: ICLRRuntimeHost::GetCurrentAppDomainId – metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.GetCurrentAppDomainId
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::GetCurrentAppDomainId
helpviewer_keywords:
- ICLRRuntimeHost::GetCurrentAppDomainId method [.NET Framework hosting]
- GetCurrentAppDomainId method [.NET Framework hosting]
ms.assetid: 33800475-7815-4976-8aca-a1038761a2ef
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 28d1655bdc3746dab87acef2e2aac6758883e74a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59096209"
---
# <a name="iclrruntimehostgetcurrentappdomainid-method"></a><span data-ttu-id="f7bde-102">ICLRRuntimeHost::GetCurrentAppDomainId – metoda</span><span class="sxs-lookup"><span data-stu-id="f7bde-102">ICLRRuntimeHost::GetCurrentAppDomainId Method</span></span>
<span data-ttu-id="f7bde-103">Získá číselný identifikátor <xref:System.AppDomain> , který aktuálně spouští.</span><span class="sxs-lookup"><span data-stu-id="f7bde-103">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7bde-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7bde-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentAppDomainId(  
    [out] DWORD* pdwAppDomainId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7bde-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f7bde-105">Parameters</span></span>  
 `pdwAppDomainId`  
 <span data-ttu-id="f7bde-106">[out] Číselný identifikátor <xref:System.AppDomain> , který aktuálně spouští.</span><span class="sxs-lookup"><span data-stu-id="f7bde-106">[out] The numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f7bde-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f7bde-107">Return Value</span></span>  
  
|<span data-ttu-id="f7bde-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f7bde-108">HRESULT</span></span>|<span data-ttu-id="f7bde-109">Popis</span><span class="sxs-lookup"><span data-stu-id="f7bde-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f7bde-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f7bde-110">S_OK</span></span>|`GetCurrentAppDomainId` <span data-ttu-id="f7bde-111">bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="f7bde-111">returned successfully.</span></span>|  
|<span data-ttu-id="f7bde-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f7bde-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f7bde-113">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="f7bde-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f7bde-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f7bde-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f7bde-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="f7bde-115">The call timed out.</span></span>|  
|<span data-ttu-id="f7bde-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f7bde-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f7bde-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="f7bde-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f7bde-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f7bde-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f7bde-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="f7bde-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f7bde-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f7bde-120">E_FAIL</span></span>|<span data-ttu-id="f7bde-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="f7bde-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f7bde-122">Pokud metoda vrátí E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="f7bde-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f7bde-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f7bde-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7bde-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f7bde-124">Remarks</span></span>  
 <span data-ttu-id="f7bde-125">`pdwAppDomainId` Parametr je nastaven na hodnotu <xref:System.AppDomain.Id%2A> vlastnost <xref:System.AppDomain> ve které se provádí aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="f7bde-125">The `pdwAppDomainId` parameter is set to the value of the <xref:System.AppDomain.Id%2A> property of the <xref:System.AppDomain> in which the current thread is executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7bde-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f7bde-126">Requirements</span></span>  
 <span data-ttu-id="f7bde-127">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7bde-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7bde-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f7bde-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f7bde-129">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f7bde-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="f7bde-130">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="f7bde-130">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f7bde-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f7bde-131">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainManager>
- [<span data-ttu-id="f7bde-132">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f7bde-132">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
