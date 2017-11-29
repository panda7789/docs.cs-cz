---
title: "ICLRRuntimeHost::GetCurrentAppDomainId – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeHost.GetCurrentAppDomainId
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeHost::GetCurrentAppDomainId
helpviewer_keywords:
- ICLRRuntimeHost::GetCurrentAppDomainId method [.NET Framework hosting]
- GetCurrentAppDomainId method [.NET Framework hosting]
ms.assetid: 33800475-7815-4976-8aca-a1038761a2ef
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 001a467536c899c3849b5689e65bdaf404beab75
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimehostgetcurrentappdomainid-method"></a><span data-ttu-id="97d58-102">ICLRRuntimeHost::GetCurrentAppDomainId – metoda</span><span class="sxs-lookup"><span data-stu-id="97d58-102">ICLRRuntimeHost::GetCurrentAppDomainId Method</span></span>
<span data-ttu-id="97d58-103">Získá identifikátor číselné <xref:System.AppDomain> , právě probíhá.</span><span class="sxs-lookup"><span data-stu-id="97d58-103">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97d58-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="97d58-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentAppDomainId(  
    [out] DWORD* pdwAppDomainId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="97d58-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="97d58-105">Parameters</span></span>  
 `pdwAppDomainId`  
 <span data-ttu-id="97d58-106">[out] Číselný identifikátor <xref:System.AppDomain> , právě probíhá.</span><span class="sxs-lookup"><span data-stu-id="97d58-106">[out] The numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="97d58-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="97d58-107">Return Value</span></span>  
  
|<span data-ttu-id="97d58-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="97d58-108">HRESULT</span></span>|<span data-ttu-id="97d58-109">Popis</span><span class="sxs-lookup"><span data-stu-id="97d58-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="97d58-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="97d58-110">S_OK</span></span>|<span data-ttu-id="97d58-111">`GetCurrentAppDomainId`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="97d58-111">`GetCurrentAppDomainId` returned successfully.</span></span>|  
|<span data-ttu-id="97d58-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="97d58-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="97d58-113">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="97d58-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="97d58-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="97d58-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="97d58-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="97d58-115">The call timed out.</span></span>|  
|<span data-ttu-id="97d58-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="97d58-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="97d58-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="97d58-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="97d58-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="97d58-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="97d58-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="97d58-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="97d58-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="97d58-120">E_FAIL</span></span>|<span data-ttu-id="97d58-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="97d58-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="97d58-122">Pokud metoda vrátí E_FAIL, modul CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="97d58-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="97d58-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="97d58-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97d58-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="97d58-124">Remarks</span></span>  
 <span data-ttu-id="97d58-125">`pdwAppDomainId` Parametr je nastaven na hodnotu <xref:System.AppDomain.Id%2A> vlastnost <xref:System.AppDomain> v aktuální vlákno provádí.</span><span class="sxs-lookup"><span data-stu-id="97d58-125">The `pdwAppDomainId` parameter is set to the value of the <xref:System.AppDomain.Id%2A> property of the <xref:System.AppDomain> in which the current thread is executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97d58-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="97d58-126">Requirements</span></span>  
 <span data-ttu-id="97d58-127">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97d58-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97d58-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="97d58-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="97d58-129">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="97d58-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="97d58-130">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97d58-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97d58-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="97d58-131">See Also</span></span>  
 <xref:System.AppDomain>  
 <xref:System.AppDomainManager>  
 [<span data-ttu-id="97d58-132">Iclrruntimehost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="97d58-132">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
