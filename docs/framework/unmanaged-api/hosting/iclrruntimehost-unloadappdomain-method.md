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
ms.openlocfilehash: 293c1764f4c0d857138726b8ed4855b1e3b03116
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703918"
---
# <a name="iclrruntimehostunloadappdomain-method"></a><span data-ttu-id="ddbff-102">ICLRRuntimeHost::UnloadAppDomain – metoda</span><span class="sxs-lookup"><span data-stu-id="ddbff-102">ICLRRuntimeHost::UnloadAppDomain Method</span></span>
<span data-ttu-id="ddbff-103">Uvolní spravovaný <xref:System.AppDomain> , který odpovídá zadanému numerickému identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="ddbff-103">Unloads the managed <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddbff-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ddbff-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadAppDomain(  
    [in] DWORD dwAppDomainId  
    [in] BOOL  fWaitUntilDone  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ddbff-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ddbff-105">Parameters</span></span>  
 `dwAppDomainId`  
 <span data-ttu-id="ddbff-106">pro Číselný identifikátor domény aplikace, která se má uvolnit</span><span class="sxs-lookup"><span data-stu-id="ddbff-106">[in] The numeric identifier of the application domain to unload.</span></span>  
  
 `fWaitUntilDone`  
 <span data-ttu-id="ddbff-107">[in] `true` pro indikaci, že modul CLR (Common Language Runtime) musí počkat, než dokončí provádění aktuálního vlákna aplikace před pokusem o uvolnění domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="ddbff-107">[in] `true` to indicate that the common language runtime( CLR) must wait until it has finished executing the application's current thread before attempting to unload the application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ddbff-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ddbff-108">Return Value</span></span>  
  
|<span data-ttu-id="ddbff-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ddbff-109">HRESULT</span></span>|<span data-ttu-id="ddbff-110">Popis</span><span class="sxs-lookup"><span data-stu-id="ddbff-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ddbff-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ddbff-111">S_OK</span></span>|<span data-ttu-id="ddbff-112">`UnloadAppDomain`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="ddbff-112">`UnloadAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="ddbff-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ddbff-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ddbff-114">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="ddbff-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ddbff-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ddbff-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ddbff-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="ddbff-116">The call timed out.</span></span>|  
|<span data-ttu-id="ddbff-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ddbff-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ddbff-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="ddbff-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ddbff-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ddbff-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ddbff-120">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="ddbff-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ddbff-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ddbff-121">E_FAIL</span></span>|<span data-ttu-id="ddbff-122">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="ddbff-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ddbff-123">Pokud metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="ddbff-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ddbff-124">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ddbff-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ddbff-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ddbff-125">Remarks</span></span>  
 <span data-ttu-id="ddbff-126">Můžete získat číselný identifikátor domény aplikace, ve které je aktuální vlákno spuštěno voláním [GetCurrentAppDomainId –](iclrruntimehost-getcurrentappdomainid-method.md).</span><span class="sxs-lookup"><span data-stu-id="ddbff-126">You can get the numeric identifier of the application domain in which the current thread is executing by calling [GetCurrentAppDomainId](iclrruntimehost-getcurrentappdomainid-method.md).</span></span> <span data-ttu-id="ddbff-127">Tento identifikátor odpovídá <xref:System.AppDomain.Id%2A> vlastnosti spravovaného <xref:System.AppDomain> typu.</span><span class="sxs-lookup"><span data-stu-id="ddbff-127">This identifier corresponds to the <xref:System.AppDomain.Id%2A> property of the managed <xref:System.AppDomain> type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ddbff-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ddbff-128">Requirements</span></span>  
 <span data-ttu-id="ddbff-129">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ddbff-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ddbff-130">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ddbff-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ddbff-131">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ddbff-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ddbff-132">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ddbff-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddbff-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="ddbff-133">See also</span></span>

- [<span data-ttu-id="ddbff-134">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ddbff-134">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
