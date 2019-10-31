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
ms.openlocfilehash: 1b7d321eec2bbc2beb47c5de034bb4ef5d534c9d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120472"
---
# <a name="iclrruntimehostgetcurrentappdomainid-method"></a><span data-ttu-id="7f149-102">ICLRRuntimeHost::GetCurrentAppDomainId – metoda</span><span class="sxs-lookup"><span data-stu-id="7f149-102">ICLRRuntimeHost::GetCurrentAppDomainId Method</span></span>
<span data-ttu-id="7f149-103">Získá číselný identifikátor <xref:System.AppDomain>, který se právě provádí.</span><span class="sxs-lookup"><span data-stu-id="7f149-103">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f149-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f149-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentAppDomainId(  
    [out] DWORD* pdwAppDomainId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f149-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7f149-105">Parameters</span></span>  
 `pdwAppDomainId`  
 <span data-ttu-id="7f149-106">mimo Číselný identifikátor <xref:System.AppDomain>, který je právě prováděn.</span><span class="sxs-lookup"><span data-stu-id="7f149-106">[out] The numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7f149-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7f149-107">Return Value</span></span>  
  
|<span data-ttu-id="7f149-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7f149-108">HRESULT</span></span>|<span data-ttu-id="7f149-109">Popis</span><span class="sxs-lookup"><span data-stu-id="7f149-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7f149-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7f149-110">S_OK</span></span>|<span data-ttu-id="7f149-111">`GetCurrentAppDomainId` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="7f149-111">`GetCurrentAppDomainId` returned successfully.</span></span>|  
|<span data-ttu-id="7f149-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7f149-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7f149-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="7f149-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7f149-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7f149-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7f149-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="7f149-115">The call timed out.</span></span>|  
|<span data-ttu-id="7f149-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7f149-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7f149-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="7f149-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7f149-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7f149-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7f149-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="7f149-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7f149-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7f149-120">E_FAIL</span></span>|<span data-ttu-id="7f149-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="7f149-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7f149-122">Pokud metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="7f149-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7f149-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7f149-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f149-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7f149-124">Remarks</span></span>  
 <span data-ttu-id="7f149-125">Parametr `pdwAppDomainId` je nastaven na hodnotu vlastnosti <xref:System.AppDomain.Id%2A> <xref:System.AppDomain>, ve kterém je spuštěno aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="7f149-125">The `pdwAppDomainId` parameter is set to the value of the <xref:System.AppDomain.Id%2A> property of the <xref:System.AppDomain> in which the current thread is executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f149-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7f149-126">Requirements</span></span>  
 <span data-ttu-id="7f149-127">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f149-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f149-128">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7f149-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7f149-129">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7f149-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7f149-130">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f149-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f149-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7f149-131">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainManager>
- [<span data-ttu-id="7f149-132">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7f149-132">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
