---
title: ICLRRuntimeHost::UnloadAppDomain – metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.UnloadAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::UnloadAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::UnloadAppDomain method [.NET Framework hosting]
- UnloadAppDomain method [.NET Framework hosting]
ms.assetid: 571912bc-3429-4ff8-8eb2-ea993ffbd901
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad87599de1b6c3227f4b413ea84558ad690d250f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494386"
---
# <a name="iclrruntimehostunloadappdomain-method"></a><span data-ttu-id="a7588-102">ICLRRuntimeHost::UnloadAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="a7588-102">ICLRRuntimeHost::UnloadAppDomain Method</span></span>
<span data-ttu-id="a7588-103">Uvolní spravované <xref:System.AppDomain> , který odpovídá zadané číselný identifikátor.</span><span class="sxs-lookup"><span data-stu-id="a7588-103">Unloads the managed <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7588-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a7588-104">Syntax</span></span>  
  
```  
HRESULT UnloadAppDomain(  
    [in] DWORD dwAppDomainId  
    [in] BOOL  fWaitUntilDone  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7588-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7588-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="a7588-106">[in] Číselný identifikátor pro uvolnění domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="a7588-106">[in] The numeric identifier of the application domain to unload.</span></span>  
  
 `fWaitUntilDone`  
 <span data-ttu-id="a7588-107">[in] `true` k označení, že modul CLR (CLR) musíte počkat, až do dokončení provádění aktuálního vlákna aplikace před pokusem o uvolnění domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="a7588-107">[in] `true` to indicate that the common language runtime( CLR) must wait until it has finished executing the application's current thread before attempting to unload the application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a7588-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a7588-108">Return Value</span></span>  
  
|<span data-ttu-id="a7588-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a7588-109">HRESULT</span></span>|<span data-ttu-id="a7588-110">Popis</span><span class="sxs-lookup"><span data-stu-id="a7588-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a7588-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a7588-111">S_OK</span></span>|<span data-ttu-id="a7588-112">`UnloadAppDomain` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="a7588-112">`UnloadAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="a7588-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a7588-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a7588-114">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="a7588-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a7588-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a7588-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a7588-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="a7588-116">The call timed out.</span></span>|  
|<span data-ttu-id="a7588-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a7588-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a7588-118">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="a7588-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a7588-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a7588-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a7588-120">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="a7588-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a7588-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a7588-121">E_FAIL</span></span>|<span data-ttu-id="a7588-122">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="a7588-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a7588-123">Pokud metoda vrátí E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="a7588-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a7588-124">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a7588-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7588-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a7588-125">Remarks</span></span>  
 <span data-ttu-id="a7588-126">Můžete získat číselný identifikátor domény aplikace, ve kterém se provádí aktuální vlákno voláním [getcurrentappdomainid –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span><span class="sxs-lookup"><span data-stu-id="a7588-126">You can get the numeric identifier of the application domain in which the current thread is executing by calling [GetCurrentAppDomainId](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span></span> <span data-ttu-id="a7588-127">Tento identifikátor odpovídá <xref:System.AppDomain.Id%2A> vlastnost spravovaného <xref:System.AppDomain> typu.</span><span class="sxs-lookup"><span data-stu-id="a7588-127">This identifier corresponds to the <xref:System.AppDomain.Id%2A> property of the managed <xref:System.AppDomain> type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7588-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a7588-128">Requirements</span></span>  
 <span data-ttu-id="a7588-129">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7588-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7588-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a7588-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a7588-131">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a7588-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a7588-132">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7588-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7588-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a7588-133">See also</span></span>
- [<span data-ttu-id="a7588-134">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a7588-134">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
