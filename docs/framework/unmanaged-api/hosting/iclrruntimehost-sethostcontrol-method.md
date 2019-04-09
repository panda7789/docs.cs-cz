---
title: ICLRRuntimeHost::SetHostControl – metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.SetHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::SetHostControl
helpviewer_keywords:
- SetHostControl method [.NET Framework hosting]
- ICLRRuntimeHost::SetHostControl method [.NET Framework hosting]
ms.assetid: 6136be87-e631-4756-81ed-74b66581bad4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6817a2154e876dfa83540e3496f42acdcdb25a83
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59198762"
---
# <a name="iclrruntimehostsethostcontrol-method"></a><span data-ttu-id="f49e3-102">ICLRRuntimeHost::SetHostControl – metoda</span><span class="sxs-lookup"><span data-stu-id="f49e3-102">ICLRRuntimeHost::SetHostControl Method</span></span>
<span data-ttu-id="f49e3-103">Nastaví ukazatel rozhraní, modul CLR (CLR) můžete použít k získání hostitele provádění [ihostcontrol – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span><span class="sxs-lookup"><span data-stu-id="f49e3-103">Sets the interface pointer that the common language runtime (CLR) can use to get the host's implementation of [IHostControl Interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f49e3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f49e3-104">Syntax</span></span>  
  
```  
HRESULT SetHostControl(  
    [in] IHostControl* pHostControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f49e3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f49e3-105">Parameters</span></span>  
 `pHostControl`  
 <span data-ttu-id="f49e3-106">[in] Ukazatel rozhraní k implementaci hostitele [ihostcontrol – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span><span class="sxs-lookup"><span data-stu-id="f49e3-106">[in] An interface pointer to the host's implementation of [IHostControl Interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f49e3-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f49e3-107">Return Value</span></span>  
  
|<span data-ttu-id="f49e3-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f49e3-108">HRESULT</span></span>|<span data-ttu-id="f49e3-109">Popis</span><span class="sxs-lookup"><span data-stu-id="f49e3-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f49e3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f49e3-110">S_OK</span></span>|`SetHostControl` <span data-ttu-id="f49e3-111">bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="f49e3-111">returned successfully.</span></span>|  
|<span data-ttu-id="f49e3-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f49e3-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f49e3-113">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="f49e3-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f49e3-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f49e3-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f49e3-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="f49e3-115">The call timed out.</span></span>|  
|<span data-ttu-id="f49e3-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f49e3-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f49e3-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="f49e3-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f49e3-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f49e3-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f49e3-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="f49e3-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f49e3-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f49e3-120">E_FAIL</span></span>|<span data-ttu-id="f49e3-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="f49e3-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f49e3-122">Pokud metoda vrátí E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="f49e3-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f49e3-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f49e3-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f49e3-124">E_CLR_ALREADY_STARTED</span><span class="sxs-lookup"><span data-stu-id="f49e3-124">E_CLR_ALREADY_STARTED</span></span>|<span data-ttu-id="f49e3-125">Modul CLR již byl inicializován.</span><span class="sxs-lookup"><span data-stu-id="f49e3-125">The CLR has already been initialized.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f49e3-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f49e3-126">Remarks</span></span>  
 <span data-ttu-id="f49e3-127">Je nutné volat `SetHostControl` předtím, než CLR je inicializována, tedy před voláním [metoda Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) nebo využívají [metadat rozhraní](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="f49e3-127">You must call `SetHostControl` before the CLR is initialized, that is, before you call [Start Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) or use any of the [Metadata Interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span> <span data-ttu-id="f49e3-128">Doporučuje se, že zavoláte `SetHostControl` ihned po volání [corbindtocurrentruntime – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md) nebo [CorBindToRuntimeEx – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md).</span><span class="sxs-lookup"><span data-stu-id="f49e3-128">It is recommended that you call `SetHostControl` immediately after calling [CorBindToCurrentRuntime Function](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md) or [CorBindToRuntimeEx Function](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f49e3-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f49e3-129">Requirements</span></span>  
 <span data-ttu-id="f49e3-130">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f49e3-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f49e3-131">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f49e3-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f49e3-132">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f49e3-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="f49e3-133">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="f49e3-133">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f49e3-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f49e3-134">See also</span></span>

- [<span data-ttu-id="f49e3-135">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f49e3-135">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [<span data-ttu-id="f49e3-136">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f49e3-136">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
