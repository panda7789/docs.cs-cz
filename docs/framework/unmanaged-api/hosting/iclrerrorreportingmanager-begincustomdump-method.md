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
ms.openlocfilehash: 7153ac214ab99228ac9c59032aa8248d06d14c3b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129301"
---
# <a name="iclrerrorreportingmanagerbegincustomdump-method"></a><span data-ttu-id="1478a-102">ICLRErrorReportingManager::BeginCustomDump – metoda</span><span class="sxs-lookup"><span data-stu-id="1478a-102">ICLRErrorReportingManager::BeginCustomDump Method</span></span>
<span data-ttu-id="1478a-103">Určuje konfiguraci vlastních výpisů paměti haldy pro zasílání zpráv o chybách.</span><span class="sxs-lookup"><span data-stu-id="1478a-103">Specifies the configuration of custom heap dumps for error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1478a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1478a-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginCustomDump (  
    [in] ECustomDumpFlavor dwFlavor,  
    [in] DWORD dwNumItems,  
    [in, size_is(dwNumItems), length_is(dwNumItems)] CustomDumpItem items[],  
    DWORD dwReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1478a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1478a-105">Parameters</span></span>  
 `dwFlavor`  
 <span data-ttu-id="1478a-106">pro Hodnota [ECustomDumpFlavor –](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md) , která indikuje druh výpisu haldy, na který se má sestavit vlastní výpis paměti.</span><span class="sxs-lookup"><span data-stu-id="1478a-106">[in] A [ECustomDumpFlavor](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md) value that indicates the kind of heap dump upon which to build the custom heap dump.</span></span>  
  
 `dwNumItems`  
 <span data-ttu-id="1478a-107">pro Délka pole `items`.</span><span class="sxs-lookup"><span data-stu-id="1478a-107">[in] The length of the `items` array.</span></span> <span data-ttu-id="1478a-108">Pokud `dwFlavor` DUMP_FLAVOR_Mini není, `dwNumItems` by měla být nulová.</span><span class="sxs-lookup"><span data-stu-id="1478a-108">If `dwFlavor` is not DUMP_FLAVOR_Mini, `dwNumItems` should be zero.</span></span>  
  
 `items`  
 <span data-ttu-id="1478a-109">pro Pole instancí [CustomDumpItem –](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) určujících položky, které se mají přidat do zkráceného výpisu.</span><span class="sxs-lookup"><span data-stu-id="1478a-109">[in] An array of [CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) instances, specifying the items to add to the mini-dump.</span></span> <span data-ttu-id="1478a-110">Pokud `dwFlavor` DUMP_FLAVOR_Mini není, `items` by měla mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="1478a-110">If `dwFlavor` is not DUMP_FLAVOR_Mini, `items` should be null.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="1478a-111">pro Vyhrazeno pro budoucí použití.</span><span class="sxs-lookup"><span data-stu-id="1478a-111">[in] Reserved for future use.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1478a-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1478a-112">Return Value</span></span>  
  
|<span data-ttu-id="1478a-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1478a-113">HRESULT</span></span>|<span data-ttu-id="1478a-114">Popis</span><span class="sxs-lookup"><span data-stu-id="1478a-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1478a-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="1478a-115">S_OK</span></span>|<span data-ttu-id="1478a-116">Metoda byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="1478a-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="1478a-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1478a-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1478a-118">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="1478a-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1478a-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1478a-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1478a-120">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="1478a-120">The call timed out.</span></span>|  
|<span data-ttu-id="1478a-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1478a-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1478a-122">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="1478a-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1478a-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1478a-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1478a-124">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="1478a-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1478a-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1478a-125">E_FAIL</span></span>|<span data-ttu-id="1478a-126">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="1478a-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1478a-127">Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="1478a-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1478a-128">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1478a-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1478a-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1478a-129">Remarks</span></span>  
 <span data-ttu-id="1478a-130">Metoda `BeginCustomDump` nastaví vlastní konfiguraci výpisu paměti haldy.</span><span class="sxs-lookup"><span data-stu-id="1478a-130">The `BeginCustomDump` method sets custom heap dump configuration.</span></span> <span data-ttu-id="1478a-131">Metoda [EndCustomDump –](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md) vymaže vlastní konfiguraci výpisu paměti haldy a uvolní všechny přidružené stavy.</span><span class="sxs-lookup"><span data-stu-id="1478a-131">The [EndCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md) method clears the custom heap dump configuration and frees any associated state.</span></span> <span data-ttu-id="1478a-132">Tato metoda by měla být volána poté, co je dokončen vlastní výpis haldy.</span><span class="sxs-lookup"><span data-stu-id="1478a-132">It should be called after the custom heap dump is complete.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1478a-133">Selhání volání `EndCustomDump` způsobuje nevracení paměti.</span><span class="sxs-lookup"><span data-stu-id="1478a-133">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1478a-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1478a-134">Requirements</span></span>  
 <span data-ttu-id="1478a-135">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1478a-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1478a-136">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1478a-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1478a-137">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1478a-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1478a-138">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1478a-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1478a-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1478a-139">See also</span></span>

- [<span data-ttu-id="1478a-140">CustomDumpItem – struktura</span><span class="sxs-lookup"><span data-stu-id="1478a-140">CustomDumpItem Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)
- [<span data-ttu-id="1478a-141">ECustomDumpFlavor – výčet</span><span class="sxs-lookup"><span data-stu-id="1478a-141">ECustomDumpFlavor Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md)
- [<span data-ttu-id="1478a-142">ICLRErrorReportingManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1478a-142">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
