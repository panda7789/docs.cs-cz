---
title: "ICLRErrorReportingManager – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRErrorReportingManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager
helpviewer_keywords:
- ICLRErrorReportingManager interface [.NET Framework hosting]
ms.assetid: ea8af0d5-4133-4472-8a1f-50570d7e85fa
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1ac362432a5d0c613f4ee1409ee15d92bfef3aeb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrerrorreportingmanager-interface"></a><span data-ttu-id="7e265-102">ICLRErrorReportingManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7e265-102">ICLRErrorReportingManager Interface</span></span>
<span data-ttu-id="7e265-103">Poskytuje metody, které umožňují hostiteli nakonfigurovat vlastní zásobník výpisy pro zasílání zpráv o chybách.</span><span class="sxs-lookup"><span data-stu-id="7e265-103">Provides methods that allow the host to configure custom stack dumps for error reporting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7e265-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7e265-104">Methods</span></span>  
  
|<span data-ttu-id="7e265-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7e265-105">Method</span></span>|<span data-ttu-id="7e265-106">Popis</span><span class="sxs-lookup"><span data-stu-id="7e265-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7e265-107">BeginCustomDump – metoda</span><span class="sxs-lookup"><span data-stu-id="7e265-107">BeginCustomDump Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md)|<span data-ttu-id="7e265-108">Určuje konfiguraci výpisy zásobníku vlastní pro zasílání zpráv o chybách.</span><span class="sxs-lookup"><span data-stu-id="7e265-108">Specifies the configuration of custom stack dumps for error reporting.</span></span>|  
|[<span data-ttu-id="7e265-109">EndCustomDump – metoda</span><span class="sxs-lookup"><span data-stu-id="7e265-109">EndCustomDump Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md)|<span data-ttu-id="7e265-110">Vymaže konfiguraci výpisu vlastní zásobníku, která byla nastavena starší voláním `BeginCustomDump`.</span><span class="sxs-lookup"><span data-stu-id="7e265-110">Clears the custom stack dump configuration that was set by an earlier call to `BeginCustomDump`.</span></span>|  
|[<span data-ttu-id="7e265-111">GetBucketParametersForCurrentException – metoda</span><span class="sxs-lookup"><span data-stu-id="7e265-111">GetBucketParametersForCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|<span data-ttu-id="7e265-112">Získá Watson sady pro aktuální výjimky na volající vlákno.</span><span class="sxs-lookup"><span data-stu-id="7e265-112">Gets the Watson bucket for the current exception on the calling thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e265-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7e265-113">Remarks</span></span>  
 <span data-ttu-id="7e265-114">`BeginCustomDump` Metoda nastaví vlastní zásobník výpisu konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="7e265-114">The `BeginCustomDump` method sets custom stack dump configuration.</span></span> <span data-ttu-id="7e265-115">`EndCustomDump` Metoda bude vymazána konfigurace výpisu vlastní zásobníku a uvolní všechny přidružený stav.</span><span class="sxs-lookup"><span data-stu-id="7e265-115">The `EndCustomDump` method clears the custom stack dump configuration and frees any associated state.</span></span> <span data-ttu-id="7e265-116">By měla být volána po dokončení vlastní výpis.</span><span class="sxs-lookup"><span data-stu-id="7e265-116">It should be called after the custom dump is complete.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7e265-117">Selhání volání `EndCustomDump` způsobí, že k úniku paměti.</span><span class="sxs-lookup"><span data-stu-id="7e265-117">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e265-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7e265-118">Requirements</span></span>  
 <span data-ttu-id="7e265-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e265-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e265-120">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7e265-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7e265-121">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7e265-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7e265-122">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e265-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e265-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="7e265-123">See Also</span></span>  
 [<span data-ttu-id="7e265-124">ECustomDumpItemKind – výčet</span><span class="sxs-lookup"><span data-stu-id="7e265-124">ECustomDumpItemKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)  
 [<span data-ttu-id="7e265-125">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="7e265-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
