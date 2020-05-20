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
ms.openlocfilehash: 1c667b19ac4bfa0bea95b85cf099906e351e5b71
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703678"
---
# <a name="iclrruntimehostgetcurrentappdomainid-method"></a><span data-ttu-id="0abd9-102">ICLRRuntimeHost::GetCurrentAppDomainId – metoda</span><span class="sxs-lookup"><span data-stu-id="0abd9-102">ICLRRuntimeHost::GetCurrentAppDomainId Method</span></span>
<span data-ttu-id="0abd9-103">Získá číselný identifikátor <xref:System.AppDomain> aktuálně prováděného.</span><span class="sxs-lookup"><span data-stu-id="0abd9-103">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0abd9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0abd9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentAppDomainId(  
    [out] DWORD* pdwAppDomainId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0abd9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0abd9-105">Parameters</span></span>  
 `pdwAppDomainId`  
 <span data-ttu-id="0abd9-106">mimo Číselný identifikátor <xref:System.AppDomain> aktuálně prováděného příkazu.</span><span class="sxs-lookup"><span data-stu-id="0abd9-106">[out] The numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0abd9-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0abd9-107">Return Value</span></span>  
  
|<span data-ttu-id="0abd9-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0abd9-108">HRESULT</span></span>|<span data-ttu-id="0abd9-109">Popis</span><span class="sxs-lookup"><span data-stu-id="0abd9-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0abd9-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0abd9-110">S_OK</span></span>|<span data-ttu-id="0abd9-111">`GetCurrentAppDomainId`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="0abd9-111">`GetCurrentAppDomainId` returned successfully.</span></span>|  
|<span data-ttu-id="0abd9-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0abd9-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0abd9-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="0abd9-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0abd9-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0abd9-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0abd9-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="0abd9-115">The call timed out.</span></span>|  
|<span data-ttu-id="0abd9-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0abd9-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0abd9-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="0abd9-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0abd9-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0abd9-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0abd9-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="0abd9-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0abd9-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0abd9-120">E_FAIL</span></span>|<span data-ttu-id="0abd9-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="0abd9-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0abd9-122">Pokud metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="0abd9-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0abd9-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0abd9-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0abd9-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0abd9-124">Remarks</span></span>  
 <span data-ttu-id="0abd9-125">`pdwAppDomainId`Parametr je nastaven na hodnotu <xref:System.AppDomain.Id%2A> vlastnosti, <xref:System.AppDomain> ve které je spuštěno aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="0abd9-125">The `pdwAppDomainId` parameter is set to the value of the <xref:System.AppDomain.Id%2A> property of the <xref:System.AppDomain> in which the current thread is executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0abd9-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0abd9-126">Requirements</span></span>  
 <span data-ttu-id="0abd9-127">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0abd9-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0abd9-128">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0abd9-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0abd9-129">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0abd9-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0abd9-130">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0abd9-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0abd9-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="0abd9-131">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainManager>
- [<span data-ttu-id="0abd9-132">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0abd9-132">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
