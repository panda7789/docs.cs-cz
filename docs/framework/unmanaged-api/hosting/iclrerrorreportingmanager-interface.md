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
ms.openlocfilehash: 49a60b6b9b076138d8ff1f8a15041e9a6bacfede
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129245"
---
# <a name="iclrerrorreportingmanager-interface"></a><span data-ttu-id="03940-102">ICLRErrorReportingManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="03940-102">ICLRErrorReportingManager Interface</span></span>
<span data-ttu-id="03940-103">Poskytuje metody, které umožňují hostiteli nakonfigurovat vlastní výpisy zásobníku pro zasílání zpráv o chybách.</span><span class="sxs-lookup"><span data-stu-id="03940-103">Provides methods that allow the host to configure custom stack dumps for error reporting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="03940-104">Metody</span><span class="sxs-lookup"><span data-stu-id="03940-104">Methods</span></span>  
  
|<span data-ttu-id="03940-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="03940-105">Method</span></span>|<span data-ttu-id="03940-106">Popis</span><span class="sxs-lookup"><span data-stu-id="03940-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="03940-107">BeginCustomDump – metoda</span><span class="sxs-lookup"><span data-stu-id="03940-107">BeginCustomDump Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md)|<span data-ttu-id="03940-108">Určuje konfiguraci vlastních výpisů paměti zásobníku pro zasílání zpráv o chybách.</span><span class="sxs-lookup"><span data-stu-id="03940-108">Specifies the configuration of custom stack dumps for error reporting.</span></span>|  
|[<span data-ttu-id="03940-109">EndCustomDump – metoda</span><span class="sxs-lookup"><span data-stu-id="03940-109">EndCustomDump Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md)|<span data-ttu-id="03940-110">Vymaže vlastní konfiguraci výpisu paměti zásobníku, která byla nastavena starším voláním `BeginCustomDump`.</span><span class="sxs-lookup"><span data-stu-id="03940-110">Clears the custom stack dump configuration that was set by an earlier call to `BeginCustomDump`.</span></span>|  
|[<span data-ttu-id="03940-111">GetBucketParametersForCurrentException – metoda</span><span class="sxs-lookup"><span data-stu-id="03940-111">GetBucketParametersForCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|<span data-ttu-id="03940-112">Získá blok programu Watson pro aktuální výjimku v volajícím vlákně.</span><span class="sxs-lookup"><span data-stu-id="03940-112">Gets the Watson bucket for the current exception on the calling thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03940-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="03940-113">Remarks</span></span>  
 <span data-ttu-id="03940-114">Metoda `BeginCustomDump` nastaví vlastní konfiguraci výpisu zásobníku.</span><span class="sxs-lookup"><span data-stu-id="03940-114">The `BeginCustomDump` method sets custom stack dump configuration.</span></span> <span data-ttu-id="03940-115">Metoda `EndCustomDump` vymaže vlastní konfiguraci výpisu zásobníku a uvolní všechny přidružené stavy.</span><span class="sxs-lookup"><span data-stu-id="03940-115">The `EndCustomDump` method clears the custom stack dump configuration and frees any associated state.</span></span> <span data-ttu-id="03940-116">Tato metoda by měla být volána po dokončení vlastního výpisu paměti.</span><span class="sxs-lookup"><span data-stu-id="03940-116">It should be called after the custom dump is complete.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="03940-117">Selhání volání `EndCustomDump` způsobuje nevracení paměti.</span><span class="sxs-lookup"><span data-stu-id="03940-117">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03940-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="03940-118">Requirements</span></span>  
 <span data-ttu-id="03940-119">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03940-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03940-120">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="03940-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="03940-121">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="03940-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="03940-122">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03940-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03940-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="03940-123">See also</span></span>

- [<span data-ttu-id="03940-124">ECustomDumpItemKind – výčet</span><span class="sxs-lookup"><span data-stu-id="03940-124">ECustomDumpItemKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)
- [<span data-ttu-id="03940-125">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="03940-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
