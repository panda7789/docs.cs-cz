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
ms.openlocfilehash: 4c83ffaf920abe005ba987e0a744e13aa0d3c016
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615667"
---
# <a name="iclrerrorreportingmanagerbegincustomdump-method"></a><span data-ttu-id="d7000-102">ICLRErrorReportingManager::BeginCustomDump – metoda</span><span class="sxs-lookup"><span data-stu-id="d7000-102">ICLRErrorReportingManager::BeginCustomDump Method</span></span>
<span data-ttu-id="d7000-103">Určuje konfiguraci vlastních výpisů paměti haldy pro zasílání zpráv o chybách.</span><span class="sxs-lookup"><span data-stu-id="d7000-103">Specifies the configuration of custom heap dumps for error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7000-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d7000-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginCustomDump (  
    [in] ECustomDumpFlavor dwFlavor,  
    [in] DWORD dwNumItems,  
    [in, size_is(dwNumItems), length_is(dwNumItems)] CustomDumpItem items[],  
    DWORD dwReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7000-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d7000-105">Parameters</span></span>  
 `dwFlavor`  
 <span data-ttu-id="d7000-106">pro Hodnota [ECustomDumpFlavor –](ecustomdumpflavor-enumeration.md) , která indikuje druh výpisu haldy, na který se má sestavit vlastní výpis paměti.</span><span class="sxs-lookup"><span data-stu-id="d7000-106">[in] A [ECustomDumpFlavor](ecustomdumpflavor-enumeration.md) value that indicates the kind of heap dump upon which to build the custom heap dump.</span></span>  
  
 `dwNumItems`  
 <span data-ttu-id="d7000-107">pro Délka `items` pole.</span><span class="sxs-lookup"><span data-stu-id="d7000-107">[in] The length of the `items` array.</span></span> <span data-ttu-id="d7000-108">Pokud `dwFlavor` není DUMP_FLAVOR_Mini, `dwNumItems` měla by být nula.</span><span class="sxs-lookup"><span data-stu-id="d7000-108">If `dwFlavor` is not DUMP_FLAVOR_Mini, `dwNumItems` should be zero.</span></span>  
  
 `items`  
 <span data-ttu-id="d7000-109">pro Pole instancí [CustomDumpItem –](customdumpitem-structure.md) určujících položky, které se mají přidat do zkráceného výpisu.</span><span class="sxs-lookup"><span data-stu-id="d7000-109">[in] An array of [CustomDumpItem](customdumpitem-structure.md) instances, specifying the items to add to the mini-dump.</span></span> <span data-ttu-id="d7000-110">Pokud `dwFlavor` není DUMP_FLAVOR_Mini, `items` měl by mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="d7000-110">If `dwFlavor` is not DUMP_FLAVOR_Mini, `items` should be null.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="d7000-111">pro Vyhrazeno pro budoucí použití.</span><span class="sxs-lookup"><span data-stu-id="d7000-111">[in] Reserved for future use.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d7000-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d7000-112">Return Value</span></span>  
  
|<span data-ttu-id="d7000-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d7000-113">HRESULT</span></span>|<span data-ttu-id="d7000-114">Popis</span><span class="sxs-lookup"><span data-stu-id="d7000-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d7000-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="d7000-115">S_OK</span></span>|<span data-ttu-id="d7000-116">Metoda byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="d7000-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="d7000-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d7000-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d7000-118">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="d7000-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d7000-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d7000-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d7000-120">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="d7000-120">The call timed out.</span></span>|  
|<span data-ttu-id="d7000-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d7000-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d7000-122">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="d7000-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d7000-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d7000-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d7000-124">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="d7000-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d7000-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d7000-125">E_FAIL</span></span>|<span data-ttu-id="d7000-126">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="d7000-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d7000-127">Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu možné použít.</span><span class="sxs-lookup"><span data-stu-id="d7000-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d7000-128">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d7000-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7000-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d7000-129">Remarks</span></span>  
 <span data-ttu-id="d7000-130">`BeginCustomDump`Metoda nastavuje vlastní konfiguraci výpisu paměti haldy.</span><span class="sxs-lookup"><span data-stu-id="d7000-130">The `BeginCustomDump` method sets custom heap dump configuration.</span></span> <span data-ttu-id="d7000-131">Metoda [EndCustomDump –](iclrerrorreportingmanager-endcustomdump-method.md) vymaže vlastní konfiguraci výpisu paměti haldy a uvolní všechny přidružené stavy.</span><span class="sxs-lookup"><span data-stu-id="d7000-131">The [EndCustomDump](iclrerrorreportingmanager-endcustomdump-method.md) method clears the custom heap dump configuration and frees any associated state.</span></span> <span data-ttu-id="d7000-132">Tato metoda by měla být volána poté, co je dokončen vlastní výpis haldy.</span><span class="sxs-lookup"><span data-stu-id="d7000-132">It should be called after the custom heap dump is complete.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d7000-133">Selhání volání `EndCustomDump` způsobuje nevrácení paměti.</span><span class="sxs-lookup"><span data-stu-id="d7000-133">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7000-134">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d7000-134">Requirements</span></span>  
 <span data-ttu-id="d7000-135">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7000-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7000-136">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d7000-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d7000-137">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d7000-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d7000-138">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7000-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7000-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="d7000-139">See also</span></span>

- [<span data-ttu-id="d7000-140">CustomDumpItem – struktura</span><span class="sxs-lookup"><span data-stu-id="d7000-140">CustomDumpItem Structure</span></span>](customdumpitem-structure.md)
- [<span data-ttu-id="d7000-141">ECustomDumpFlavor – výčet</span><span class="sxs-lookup"><span data-stu-id="d7000-141">ECustomDumpFlavor Enumeration</span></span>](ecustomdumpflavor-enumeration.md)
- [<span data-ttu-id="d7000-142">ICLRErrorReportingManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d7000-142">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
