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
ms.openlocfilehash: 192492c232970842270f031832d1eb46357ec07f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527169"
---
# <a name="iclrruntimehostgetcurrentappdomainid-method"></a><span data-ttu-id="f85a5-102">ICLRRuntimeHost::GetCurrentAppDomainId – metoda</span><span class="sxs-lookup"><span data-stu-id="f85a5-102">ICLRRuntimeHost::GetCurrentAppDomainId Method</span></span>
<span data-ttu-id="f85a5-103">Získá číselný identifikátor <xref:System.AppDomain> , který aktuálně spouští.</span><span class="sxs-lookup"><span data-stu-id="f85a5-103">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f85a5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f85a5-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentAppDomainId(  
    [out] DWORD* pdwAppDomainId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f85a5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f85a5-105">Parameters</span></span>  
 `pdwAppDomainId`  
 <span data-ttu-id="f85a5-106">[out] Číselný identifikátor <xref:System.AppDomain> , který aktuálně spouští.</span><span class="sxs-lookup"><span data-stu-id="f85a5-106">[out] The numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f85a5-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f85a5-107">Return Value</span></span>  
  
|<span data-ttu-id="f85a5-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f85a5-108">HRESULT</span></span>|<span data-ttu-id="f85a5-109">Popis</span><span class="sxs-lookup"><span data-stu-id="f85a5-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f85a5-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f85a5-110">S_OK</span></span>|<span data-ttu-id="f85a5-111">`GetCurrentAppDomainId` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="f85a5-111">`GetCurrentAppDomainId` returned successfully.</span></span>|  
|<span data-ttu-id="f85a5-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f85a5-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f85a5-113">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="f85a5-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f85a5-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f85a5-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f85a5-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="f85a5-115">The call timed out.</span></span>|  
|<span data-ttu-id="f85a5-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f85a5-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f85a5-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="f85a5-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f85a5-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f85a5-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f85a5-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="f85a5-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f85a5-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f85a5-120">E_FAIL</span></span>|<span data-ttu-id="f85a5-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="f85a5-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f85a5-122">Pokud metoda vrátí E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="f85a5-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f85a5-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f85a5-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f85a5-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f85a5-124">Remarks</span></span>  
 <span data-ttu-id="f85a5-125">`pdwAppDomainId` Parametr je nastaven na hodnotu <xref:System.AppDomain.Id%2A> vlastnost <xref:System.AppDomain> ve které se provádí aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="f85a5-125">The `pdwAppDomainId` parameter is set to the value of the <xref:System.AppDomain.Id%2A> property of the <xref:System.AppDomain> in which the current thread is executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f85a5-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f85a5-126">Requirements</span></span>  
 <span data-ttu-id="f85a5-127">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f85a5-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f85a5-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f85a5-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f85a5-129">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f85a5-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f85a5-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f85a5-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f85a5-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f85a5-131">See also</span></span>
- <xref:System.AppDomain>
- <xref:System.AppDomainManager>
- [<span data-ttu-id="f85a5-132">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f85a5-132">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
