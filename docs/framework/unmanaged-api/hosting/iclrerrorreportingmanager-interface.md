---
title: ICLRErrorReportingManager – rozhraní
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a9d9cff0360e4eb27584fe0f22c1c20396ff8f0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966246"
---
# <a name="iclrerrorreportingmanager-interface"></a><span data-ttu-id="b443c-102">ICLRErrorReportingManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b443c-102">ICLRErrorReportingManager Interface</span></span>
<span data-ttu-id="b443c-103">Poskytuje metody, které umožňují hostiteli nakonfigurovat vlastní výpisy zásobníku pro zasílání zpráv o chybách.</span><span class="sxs-lookup"><span data-stu-id="b443c-103">Provides methods that allow the host to configure custom stack dumps for error reporting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b443c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b443c-104">Methods</span></span>  
  
|<span data-ttu-id="b443c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b443c-105">Method</span></span>|<span data-ttu-id="b443c-106">Popis</span><span class="sxs-lookup"><span data-stu-id="b443c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b443c-107">BeginCustomDump – metoda</span><span class="sxs-lookup"><span data-stu-id="b443c-107">BeginCustomDump Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md)|<span data-ttu-id="b443c-108">Určuje konfiguraci vlastních výpisů paměti zásobníku pro zasílání zpráv o chybách.</span><span class="sxs-lookup"><span data-stu-id="b443c-108">Specifies the configuration of custom stack dumps for error reporting.</span></span>|  
|[<span data-ttu-id="b443c-109">EndCustomDump – metoda</span><span class="sxs-lookup"><span data-stu-id="b443c-109">EndCustomDump Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md)|<span data-ttu-id="b443c-110">Vymaže vlastní konfiguraci výpisu zásobníku, která byla nastavena starším voláním `BeginCustomDump`.</span><span class="sxs-lookup"><span data-stu-id="b443c-110">Clears the custom stack dump configuration that was set by an earlier call to `BeginCustomDump`.</span></span>|  
|[<span data-ttu-id="b443c-111">GetBucketParametersForCurrentException – metoda</span><span class="sxs-lookup"><span data-stu-id="b443c-111">GetBucketParametersForCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|<span data-ttu-id="b443c-112">Získá blok programu Watson pro aktuální výjimku v volajícím vlákně.</span><span class="sxs-lookup"><span data-stu-id="b443c-112">Gets the Watson bucket for the current exception on the calling thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b443c-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b443c-113">Remarks</span></span>  
 <span data-ttu-id="b443c-114">`BeginCustomDump` Metoda nastavuje vlastní konfiguraci výpisu zásobníku.</span><span class="sxs-lookup"><span data-stu-id="b443c-114">The `BeginCustomDump` method sets custom stack dump configuration.</span></span> <span data-ttu-id="b443c-115">`EndCustomDump` Metoda vymaže vlastní konfiguraci výpisu zásobníku a uvolní všechny přidružené stavy.</span><span class="sxs-lookup"><span data-stu-id="b443c-115">The `EndCustomDump` method clears the custom stack dump configuration and frees any associated state.</span></span> <span data-ttu-id="b443c-116">Tato metoda by měla být volána po dokončení vlastního výpisu paměti.</span><span class="sxs-lookup"><span data-stu-id="b443c-116">It should be called after the custom dump is complete.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b443c-117">Selhání volání `EndCustomDump` způsobuje nevrácení paměti.</span><span class="sxs-lookup"><span data-stu-id="b443c-117">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b443c-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b443c-118">Requirements</span></span>  
 <span data-ttu-id="b443c-119">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b443c-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b443c-120">**Hlaviček** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b443c-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b443c-121">**Knihovna** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b443c-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b443c-122">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b443c-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b443c-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b443c-123">See also</span></span>

- [<span data-ttu-id="b443c-124">ECustomDumpItemKind – výčet</span><span class="sxs-lookup"><span data-stu-id="b443c-124">ECustomDumpItemKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)
- [<span data-ttu-id="b443c-125">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="b443c-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
