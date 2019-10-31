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
ms.openlocfilehash: 2a6dc878f156d5d18970fed72c9722bab60f9ba8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120398"
---
# <a name="iclrruntimehostunloadappdomain-method"></a><span data-ttu-id="fdf74-102">ICLRRuntimeHost::UnloadAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="fdf74-102">ICLRRuntimeHost::UnloadAppDomain Method</span></span>
<span data-ttu-id="fdf74-103">Uvolní spravovaný <xref:System.AppDomain>, který odpovídá zadanému číselnému identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="fdf74-103">Unloads the managed <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdf74-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fdf74-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadAppDomain(  
    [in] DWORD dwAppDomainId  
    [in] BOOL  fWaitUntilDone  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fdf74-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fdf74-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="fdf74-106">pro Číselný identifikátor domény aplikace, která se má uvolnit</span><span class="sxs-lookup"><span data-stu-id="fdf74-106">[in] The numeric identifier of the application domain to unload.</span></span>  
  
 `fWaitUntilDone`  
 <span data-ttu-id="fdf74-107">[in] `true` pro indikaci, že modul CLR (Common Language Runtime) musí počkat, dokud se nedokončí spuštění aktuálního vlákna aplikace před pokusem o uvolnění domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="fdf74-107">[in] `true` to indicate that the common language runtime( CLR) must wait until it has finished executing the application's current thread before attempting to unload the application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fdf74-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="fdf74-108">Return Value</span></span>  
  
|<span data-ttu-id="fdf74-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fdf74-109">HRESULT</span></span>|<span data-ttu-id="fdf74-110">Popis</span><span class="sxs-lookup"><span data-stu-id="fdf74-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fdf74-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="fdf74-111">S_OK</span></span>|<span data-ttu-id="fdf74-112">`UnloadAppDomain` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="fdf74-112">`UnloadAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="fdf74-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fdf74-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fdf74-114">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="fdf74-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fdf74-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fdf74-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fdf74-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="fdf74-116">The call timed out.</span></span>|  
|<span data-ttu-id="fdf74-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fdf74-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fdf74-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="fdf74-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fdf74-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fdf74-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fdf74-120">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="fdf74-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fdf74-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fdf74-121">E_FAIL</span></span>|<span data-ttu-id="fdf74-122">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="fdf74-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fdf74-123">Pokud metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="fdf74-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fdf74-124">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fdf74-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fdf74-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fdf74-125">Remarks</span></span>  
 <span data-ttu-id="fdf74-126">Můžete získat číselný identifikátor domény aplikace, ve které je aktuální vlákno spuštěno voláním [GetCurrentAppDomainId –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span><span class="sxs-lookup"><span data-stu-id="fdf74-126">You can get the numeric identifier of the application domain in which the current thread is executing by calling [GetCurrentAppDomainId](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).</span></span> <span data-ttu-id="fdf74-127">Tento identifikátor odpovídá vlastnosti <xref:System.AppDomain.Id%2A> spravovaného <xref:System.AppDomain> typu.</span><span class="sxs-lookup"><span data-stu-id="fdf74-127">This identifier corresponds to the <xref:System.AppDomain.Id%2A> property of the managed <xref:System.AppDomain> type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fdf74-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fdf74-128">Requirements</span></span>  
 <span data-ttu-id="fdf74-129">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fdf74-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fdf74-130">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fdf74-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fdf74-131">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="fdf74-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fdf74-132">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fdf74-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdf74-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fdf74-133">See also</span></span>

- [<span data-ttu-id="fdf74-134">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fdf74-134">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
