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
ms.openlocfilehash: cbe6ac3c9f03de2224f933a7e44325f578ded48b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433908"
---
# <a name="iclrruntimehostgetcurrentappdomainid-method"></a><span data-ttu-id="9d4bb-102">ICLRRuntimeHost::GetCurrentAppDomainId – metoda</span><span class="sxs-lookup"><span data-stu-id="9d4bb-102">ICLRRuntimeHost::GetCurrentAppDomainId Method</span></span>
<span data-ttu-id="9d4bb-103">Získá identifikátor číselné <xref:System.AppDomain> , právě probíhá.</span><span class="sxs-lookup"><span data-stu-id="9d4bb-103">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d4bb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d4bb-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentAppDomainId(  
    [out] DWORD* pdwAppDomainId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9d4bb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9d4bb-105">Parameters</span></span>  
 `pdwAppDomainId`  
 <span data-ttu-id="9d4bb-106">[out] Číselný identifikátor <xref:System.AppDomain> , právě probíhá.</span><span class="sxs-lookup"><span data-stu-id="9d4bb-106">[out] The numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9d4bb-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9d4bb-107">Return Value</span></span>  
  
|<span data-ttu-id="9d4bb-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9d4bb-108">HRESULT</span></span>|<span data-ttu-id="9d4bb-109">Popis</span><span class="sxs-lookup"><span data-stu-id="9d4bb-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9d4bb-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9d4bb-110">S_OK</span></span>|<span data-ttu-id="9d4bb-111">`GetCurrentAppDomainId` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="9d4bb-111">`GetCurrentAppDomainId` returned successfully.</span></span>|  
|<span data-ttu-id="9d4bb-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9d4bb-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9d4bb-113">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="9d4bb-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9d4bb-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9d4bb-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9d4bb-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="9d4bb-115">The call timed out.</span></span>|  
|<span data-ttu-id="9d4bb-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9d4bb-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9d4bb-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="9d4bb-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9d4bb-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9d4bb-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9d4bb-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="9d4bb-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9d4bb-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9d4bb-120">E_FAIL</span></span>|<span data-ttu-id="9d4bb-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="9d4bb-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9d4bb-122">Pokud metoda vrátí E_FAIL, modul CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="9d4bb-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9d4bb-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9d4bb-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d4bb-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9d4bb-124">Remarks</span></span>  
 <span data-ttu-id="9d4bb-125">`pdwAppDomainId` Parametr je nastaven na hodnotu <xref:System.AppDomain.Id%2A> vlastnost <xref:System.AppDomain> v aktuální vlákno provádí.</span><span class="sxs-lookup"><span data-stu-id="9d4bb-125">The `pdwAppDomainId` parameter is set to the value of the <xref:System.AppDomain.Id%2A> property of the <xref:System.AppDomain> in which the current thread is executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d4bb-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9d4bb-126">Requirements</span></span>  
 <span data-ttu-id="9d4bb-127">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d4bb-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d4bb-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9d4bb-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9d4bb-129">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9d4bb-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9d4bb-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d4bb-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d4bb-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="9d4bb-131">See Also</span></span>  
 <xref:System.AppDomain>  
 <xref:System.AppDomainManager>  
 [<span data-ttu-id="9d4bb-132">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9d4bb-132">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
