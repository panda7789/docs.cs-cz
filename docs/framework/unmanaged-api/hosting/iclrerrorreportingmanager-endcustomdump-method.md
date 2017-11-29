---
title: "ICLRErrorReportingManager::EndCustomDump – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRErrorReportingManager.EndCustomDump
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRErrorReportingManager::EndCustomDump
helpviewer_keywords:
- ICLRErrorReportingManager::EndCustomDump method [.NET Framework hosting]
- EndCustomDump method [.NET Framework hosting]
ms.assetid: 88a5da04-8729-4108-82c4-af206a7d483e
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 059ab01d3cc05bac84bb1a4cd8fffc7fc259ed60
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrerrorreportingmanagerendcustomdump-method"></a><span data-ttu-id="9bff1-102">ICLRErrorReportingManager::EndCustomDump – metoda</span><span class="sxs-lookup"><span data-stu-id="9bff1-102">ICLRErrorReportingManager::EndCustomDump Method</span></span>
<span data-ttu-id="9bff1-103">Odebere konfiguraci výpisu vlastní zásobníku, která byla zadaná v dřívější volání [iclrerrorreportingmanager::begincustomdump –](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="9bff1-103">Removes the custom stack dump configuration that was specified in an earlier call to the [ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bff1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9bff1-104">Syntax</span></span>  
  
```  
HRESULT EndCustomDump ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="9bff1-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9bff1-105">Return Value</span></span>  
  
|<span data-ttu-id="9bff1-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9bff1-106">HRESULT</span></span>|<span data-ttu-id="9bff1-107">Popis</span><span class="sxs-lookup"><span data-stu-id="9bff1-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9bff1-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="9bff1-108">S_OK</span></span>|<span data-ttu-id="9bff1-109">`EndCustomDump`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="9bff1-109">`EndCustomDump` returned successfully.</span></span>|  
|<span data-ttu-id="9bff1-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9bff1-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9bff1-111">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="9bff1-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9bff1-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9bff1-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9bff1-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="9bff1-113">The call timed out.</span></span>|  
|<span data-ttu-id="9bff1-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9bff1-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9bff1-115">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="9bff1-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9bff1-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9bff1-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9bff1-117">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="9bff1-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9bff1-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9bff1-118">E_FAIL</span></span>|<span data-ttu-id="9bff1-119">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="9bff1-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9bff1-120">Po návratu metoda E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="9bff1-120">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9bff1-121">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9bff1-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9bff1-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9bff1-122">Remarks</span></span>  
 <span data-ttu-id="9bff1-123">`EndCustomDump` Metoda bude vymazána konfigurace výpisu zásobníku vlastní nastavit starší voláním `BeginCustomDump` metoda a uvolní všechny přidružený stav.</span><span class="sxs-lookup"><span data-stu-id="9bff1-123">The `EndCustomDump` method clears the custom stack dump configuration set by an earlier call to the `BeginCustomDump` method and frees any associated state.</span></span> <span data-ttu-id="9bff1-124">By měla být volána po dokončení výpis vlastní zásobníku.</span><span class="sxs-lookup"><span data-stu-id="9bff1-124">It should be called after the custom stack dump is complete.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9bff1-125">Selhání volání `EndCustomDump` způsobí, že k úniku paměti.</span><span class="sxs-lookup"><span data-stu-id="9bff1-125">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9bff1-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9bff1-126">Requirements</span></span>  
 <span data-ttu-id="9bff1-127">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9bff1-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bff1-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9bff1-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9bff1-129">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9bff1-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9bff1-130">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9bff1-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bff1-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="9bff1-131">See Also</span></span>  
 [<span data-ttu-id="9bff1-132">Customdumpitem – struktura</span><span class="sxs-lookup"><span data-stu-id="9bff1-132">CustomDumpItem Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)  
 [<span data-ttu-id="9bff1-133">ECustomDumpFlavor – výčet</span><span class="sxs-lookup"><span data-stu-id="9bff1-133">ECustomDumpFlavor Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md)  
 [<span data-ttu-id="9bff1-134">Iclrerrorreportingmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9bff1-134">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
