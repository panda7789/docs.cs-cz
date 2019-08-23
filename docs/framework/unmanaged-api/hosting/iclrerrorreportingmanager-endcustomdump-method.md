---
title: ICLRErrorReportingManager::EndCustomDump – metoda
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager.EndCustomDump
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager::EndCustomDump
helpviewer_keywords:
- ICLRErrorReportingManager::EndCustomDump method [.NET Framework hosting]
- EndCustomDump method [.NET Framework hosting]
ms.assetid: 88a5da04-8729-4108-82c4-af206a7d483e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a262ab26c9bbb93e42a11217fbeea6b3c55c7eb9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966266"
---
# <a name="iclrerrorreportingmanagerendcustomdump-method"></a><span data-ttu-id="d0ff2-102">ICLRErrorReportingManager::EndCustomDump – metoda</span><span class="sxs-lookup"><span data-stu-id="d0ff2-102">ICLRErrorReportingManager::EndCustomDump Method</span></span>
<span data-ttu-id="d0ff2-103">Odstraní vlastní konfiguraci výpisu zásobníku, která byla zadána ve starším volání metody [ICLRErrorReportingManager:: BeginCustomDump –](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d0ff2-103">Removes the custom stack dump configuration that was specified in an earlier call to the [ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0ff2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d0ff2-104">Syntax</span></span>  
  
```cpp  
HRESULT EndCustomDump ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="d0ff2-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d0ff2-105">Return Value</span></span>  
  
|<span data-ttu-id="d0ff2-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d0ff2-106">HRESULT</span></span>|<span data-ttu-id="d0ff2-107">Popis</span><span class="sxs-lookup"><span data-stu-id="d0ff2-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d0ff2-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="d0ff2-108">S_OK</span></span>|<span data-ttu-id="d0ff2-109">`EndCustomDump`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="d0ff2-109">`EndCustomDump` returned successfully.</span></span>|  
|<span data-ttu-id="d0ff2-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d0ff2-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d0ff2-111">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="d0ff2-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d0ff2-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d0ff2-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d0ff2-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="d0ff2-113">The call timed out.</span></span>|  
|<span data-ttu-id="d0ff2-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d0ff2-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d0ff2-115">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="d0ff2-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d0ff2-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d0ff2-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d0ff2-117">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="d0ff2-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d0ff2-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d0ff2-118">E_FAIL</span></span>|<span data-ttu-id="d0ff2-119">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="d0ff2-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d0ff2-120">Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="d0ff2-120">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d0ff2-121">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d0ff2-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0ff2-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d0ff2-122">Remarks</span></span>  
 <span data-ttu-id="d0ff2-123">Metoda vymaže vlastní konfiguraci výpisu paměti zásobníku nastavenou dřívějším voláním `BeginCustomDump` metody a uvolní všechny přidružené stavy. `EndCustomDump`</span><span class="sxs-lookup"><span data-stu-id="d0ff2-123">The `EndCustomDump` method clears the custom stack dump configuration set by an earlier call to the `BeginCustomDump` method and frees any associated state.</span></span> <span data-ttu-id="d0ff2-124">Tato metoda by měla být volána poté, co je dokončen vlastní výpis zásobníku.</span><span class="sxs-lookup"><span data-stu-id="d0ff2-124">It should be called after the custom stack dump is complete.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d0ff2-125">Selhání volání `EndCustomDump` způsobuje nevrácení paměti.</span><span class="sxs-lookup"><span data-stu-id="d0ff2-125">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0ff2-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d0ff2-126">Requirements</span></span>  
 <span data-ttu-id="d0ff2-127">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0ff2-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0ff2-128">**Hlaviček** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d0ff2-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d0ff2-129">**Knihovna** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d0ff2-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d0ff2-130">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0ff2-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0ff2-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d0ff2-131">See also</span></span>

- [<span data-ttu-id="d0ff2-132">CustomDumpItem – struktura</span><span class="sxs-lookup"><span data-stu-id="d0ff2-132">CustomDumpItem Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)
- [<span data-ttu-id="d0ff2-133">ECustomDumpFlavor – výčet</span><span class="sxs-lookup"><span data-stu-id="d0ff2-133">ECustomDumpFlavor Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md)
- [<span data-ttu-id="d0ff2-134">ICLRErrorReportingManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d0ff2-134">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
