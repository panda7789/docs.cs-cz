---
title: ICLRErrorReportingManager::BeginCustomDump – metoda
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager.BeginCustomDump
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager::BeginCustomDump
helpviewer_keywords:
- ICLRErrorReportingManager::BeginCustomDump method [.NET Framework hosting]
- BeginCustomDump method
ms.assetid: 93424a87-ba13-4fa1-b4dc-69d44437b7ae
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8cb6cd8d31e01ea2f1749a6cb4d17173679f0c06
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59104107"
---
# <a name="iclrerrorreportingmanagerbegincustomdump-method"></a><span data-ttu-id="04e9c-102">ICLRErrorReportingManager::BeginCustomDump – metoda</span><span class="sxs-lookup"><span data-stu-id="04e9c-102">ICLRErrorReportingManager::BeginCustomDump Method</span></span>
<span data-ttu-id="04e9c-103">Určuje konfiguraci výpisů paměti haldy vlastní pro hlášení chyb.</span><span class="sxs-lookup"><span data-stu-id="04e9c-103">Specifies the configuration of custom heap dumps for error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04e9c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04e9c-104">Syntax</span></span>  
  
```  
HRESULT BeginCustomDump (  
    [in] ECustomDumpFlavor dwFlavor,  
    [in] DWORD dwNumItems,  
    [in, size_is(dwNumItems), length_is(dwNumItems)] CustomDumpItem items[],  
    DWORD dwReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04e9c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="04e9c-105">Parameters</span></span>  
 `dwFlavor`  
 <span data-ttu-id="04e9c-106">[in] A [ecustomdumpflavor –](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md) hodnotu, která označuje druh výpisu haldy paměti, na který se má sestavit vlastní haldy s výpisem paměti.</span><span class="sxs-lookup"><span data-stu-id="04e9c-106">[in] A [ECustomDumpFlavor](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md) value that indicates the kind of heap dump upon which to build the custom heap dump.</span></span>  
  
 `dwNumItems`  
 <span data-ttu-id="04e9c-107">[in] Délka `items` pole.</span><span class="sxs-lookup"><span data-stu-id="04e9c-107">[in] The length of the `items` array.</span></span> <span data-ttu-id="04e9c-108">Pokud `dwFlavor` není DUMP_FLAVOR_Mini, `dwNumItems` musí být nula.</span><span class="sxs-lookup"><span data-stu-id="04e9c-108">If `dwFlavor` is not DUMP_FLAVOR_Mini, `dwNumItems` should be zero.</span></span>  
  
 `items`  
 <span data-ttu-id="04e9c-109">[in] Pole [customdumpitem –](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) instancí položky, které chcete přidat do minivýpis zadání.</span><span class="sxs-lookup"><span data-stu-id="04e9c-109">[in] An array of [CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) instances, specifying the items to add to the mini-dump.</span></span> <span data-ttu-id="04e9c-110">Pokud `dwFlavor` není DUMP_FLAVOR_Mini, `items` by měl mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="04e9c-110">If `dwFlavor` is not DUMP_FLAVOR_Mini, `items` should be null.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="04e9c-111">[in] Vyhrazeno pro budoucí použití.</span><span class="sxs-lookup"><span data-stu-id="04e9c-111">[in] Reserved for future use.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="04e9c-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="04e9c-112">Return Value</span></span>  
  
|<span data-ttu-id="04e9c-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="04e9c-113">HRESULT</span></span>|<span data-ttu-id="04e9c-114">Popis</span><span class="sxs-lookup"><span data-stu-id="04e9c-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="04e9c-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="04e9c-115">S_OK</span></span>|<span data-ttu-id="04e9c-116">Metoda vrátila úspěšně.</span><span class="sxs-lookup"><span data-stu-id="04e9c-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="04e9c-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="04e9c-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="04e9c-118">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="04e9c-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="04e9c-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="04e9c-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="04e9c-120">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="04e9c-120">The call timed out.</span></span>|  
|<span data-ttu-id="04e9c-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="04e9c-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="04e9c-122">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="04e9c-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="04e9c-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="04e9c-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="04e9c-124">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="04e9c-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="04e9c-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="04e9c-125">E_FAIL</span></span>|<span data-ttu-id="04e9c-126">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="04e9c-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="04e9c-127">Po návratu metoda E_FAIL CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="04e9c-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="04e9c-128">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="04e9c-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04e9c-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="04e9c-129">Remarks</span></span>  
 <span data-ttu-id="04e9c-130">`BeginCustomDump` Metoda nastaví konfiguraci vlastních haldy s výpisem paměti.</span><span class="sxs-lookup"><span data-stu-id="04e9c-130">The `BeginCustomDump` method sets custom heap dump configuration.</span></span> <span data-ttu-id="04e9c-131">[Endcustomdump –](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md) metoda vymaže výpisu stavu systému configuration vlastní haldy a uvolní všechny přidružený stav.</span><span class="sxs-lookup"><span data-stu-id="04e9c-131">The [EndCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md) method clears the custom heap dump configuration and frees any associated state.</span></span> <span data-ttu-id="04e9c-132">By měla být volána po dokončení výpis paměti haldy vlastní.</span><span class="sxs-lookup"><span data-stu-id="04e9c-132">It should be called after the custom heap dump is complete.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="04e9c-133">Nepodařilo se zavolat `EndCustomDump` způsobí, že k únik paměti.</span><span class="sxs-lookup"><span data-stu-id="04e9c-133">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04e9c-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="04e9c-134">Requirements</span></span>  
 <span data-ttu-id="04e9c-135">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04e9c-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04e9c-136">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="04e9c-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="04e9c-137">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="04e9c-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="04e9c-138">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04e9c-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04e9c-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="04e9c-139">See also</span></span>

- [<span data-ttu-id="04e9c-140">CustomDumpItem – struktura</span><span class="sxs-lookup"><span data-stu-id="04e9c-140">CustomDumpItem Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)
- [<span data-ttu-id="04e9c-141">ECustomDumpFlavor – výčet</span><span class="sxs-lookup"><span data-stu-id="04e9c-141">ECustomDumpFlavor Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md)
- [<span data-ttu-id="04e9c-142">ICLRErrorReportingManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="04e9c-142">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
