---
title: "ICLRErrorReportingManager::BeginCustomDump – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRErrorReportingManager.BeginCustomDump
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRErrorReportingManager::BeginCustomDump
helpviewer_keywords:
- ICLRErrorReportingManager::BeginCustomDump method [.NET Framework hosting]
- BeginCustomDump method
ms.assetid: 93424a87-ba13-4fa1-b4dc-69d44437b7ae
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d09afd9fe0a2905c79ffb2d50b342041865b593b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrerrorreportingmanagerbegincustomdump-method"></a><span data-ttu-id="f44c2-102">ICLRErrorReportingManager::BeginCustomDump – metoda</span><span class="sxs-lookup"><span data-stu-id="f44c2-102">ICLRErrorReportingManager::BeginCustomDump Method</span></span>
<span data-ttu-id="f44c2-103">Určuje konfiguraci výpisy vlastní haldy pro zasílání zpráv o chybách.</span><span class="sxs-lookup"><span data-stu-id="f44c2-103">Specifies the configuration of custom heap dumps for error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f44c2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f44c2-104">Syntax</span></span>  
  
```  
HRESULT BeginCustomDump (  
    [in] ECustomDumpFlavor dwFlavor,  
    [in] DWORD dwNumItems,  
    [in, size_is(dwNumItems), length_is(dwNumItems)] CustomDumpItem items[],  
    DWORD dwReserved  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f44c2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f44c2-105">Parameters</span></span>  
 `dwFlavor`  
 <span data-ttu-id="f44c2-106">[v] A [ECustomDumpFlavor](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md) hodnotu, která určuje druh haldy výpisu němž vytvářet vlastní haldy výpis.</span><span class="sxs-lookup"><span data-stu-id="f44c2-106">[in] A [ECustomDumpFlavor](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md) value that indicates the kind of heap dump upon which to build the custom heap dump.</span></span>  
  
 `dwNumItems`  
 <span data-ttu-id="f44c2-107">[v] Délka `items` pole.</span><span class="sxs-lookup"><span data-stu-id="f44c2-107">[in] The length of the `items` array.</span></span> <span data-ttu-id="f44c2-108">Pokud `dwFlavor` není DUMP_FLAVOR_Mini, `dwNumItems` musí být nula.</span><span class="sxs-lookup"><span data-stu-id="f44c2-108">If `dwFlavor` is not DUMP_FLAVOR_Mini, `dwNumItems` should be zero.</span></span>  
  
 `items`  
 <span data-ttu-id="f44c2-109">[v] Pole [customdumpitem –](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) instancí, zadáním položky, které chcete přidat do malý výpis.</span><span class="sxs-lookup"><span data-stu-id="f44c2-109">[in] An array of [CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) instances, specifying the items to add to the mini-dump.</span></span> <span data-ttu-id="f44c2-110">Pokud `dwFlavor` není DUMP_FLAVOR_Mini, `items` by měl mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="f44c2-110">If `dwFlavor` is not DUMP_FLAVOR_Mini, `items` should be null.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="f44c2-111">[v] Vyhrazeno pro budoucí použití.</span><span class="sxs-lookup"><span data-stu-id="f44c2-111">[in] Reserved for future use.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f44c2-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f44c2-112">Return Value</span></span>  
  
|<span data-ttu-id="f44c2-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f44c2-113">HRESULT</span></span>|<span data-ttu-id="f44c2-114">Popis</span><span class="sxs-lookup"><span data-stu-id="f44c2-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f44c2-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="f44c2-115">S_OK</span></span>|<span data-ttu-id="f44c2-116">Metoda úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="f44c2-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="f44c2-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f44c2-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f44c2-118">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="f44c2-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f44c2-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f44c2-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f44c2-120">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="f44c2-120">The call timed out.</span></span>|  
|<span data-ttu-id="f44c2-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f44c2-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f44c2-122">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="f44c2-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f44c2-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f44c2-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f44c2-124">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="f44c2-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f44c2-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f44c2-125">E_FAIL</span></span>|<span data-ttu-id="f44c2-126">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="f44c2-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f44c2-127">Po návratu metoda E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="f44c2-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f44c2-128">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f44c2-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f44c2-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f44c2-129">Remarks</span></span>  
 <span data-ttu-id="f44c2-130">`BeginCustomDump` Metoda nastaví vlastní haldy výpisu konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="f44c2-130">The `BeginCustomDump` method sets custom heap dump configuration.</span></span> <span data-ttu-id="f44c2-131">[Endcustomdump –](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md) metoda bude vymazána konfigurace výpisu vlastní haldy a uvolní všechny přidružený stav.</span><span class="sxs-lookup"><span data-stu-id="f44c2-131">The [EndCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md) method clears the custom heap dump configuration and frees any associated state.</span></span> <span data-ttu-id="f44c2-132">By měla být volána po dokončení vlastní haldy výpis.</span><span class="sxs-lookup"><span data-stu-id="f44c2-132">It should be called after the custom heap dump is complete.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f44c2-133">Selhání volání `EndCustomDump` způsobí, že k úniku paměti.</span><span class="sxs-lookup"><span data-stu-id="f44c2-133">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f44c2-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f44c2-134">Requirements</span></span>  
 <span data-ttu-id="f44c2-135">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f44c2-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f44c2-136">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f44c2-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f44c2-137">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f44c2-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f44c2-138">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f44c2-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f44c2-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="f44c2-139">See Also</span></span>  
 [<span data-ttu-id="f44c2-140">CustomDumpItem – struktura</span><span class="sxs-lookup"><span data-stu-id="f44c2-140">CustomDumpItem Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)  
 [<span data-ttu-id="f44c2-141">ECustomDumpFlavor – výčet</span><span class="sxs-lookup"><span data-stu-id="f44c2-141">ECustomDumpFlavor Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md)  
 [<span data-ttu-id="f44c2-142">ICLRErrorReportingManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f44c2-142">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
