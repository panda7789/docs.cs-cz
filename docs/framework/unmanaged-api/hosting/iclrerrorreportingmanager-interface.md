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
ms.openlocfilehash: dbe4129cf4160a1a9b31bc6f418095ea4b392d57
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616993"
---
# <a name="iclrerrorreportingmanager-interface"></a><span data-ttu-id="0921d-102">ICLRErrorReportingManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0921d-102">ICLRErrorReportingManager Interface</span></span>
<span data-ttu-id="0921d-103">Poskytuje metody, které umožňují hostiteli nakonfigurovat vlastní výpisy zásobníku pro zasílání zpráv o chybách.</span><span class="sxs-lookup"><span data-stu-id="0921d-103">Provides methods that allow the host to configure custom stack dumps for error reporting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0921d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0921d-104">Methods</span></span>  
  
|<span data-ttu-id="0921d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0921d-105">Method</span></span>|<span data-ttu-id="0921d-106">Popis</span><span class="sxs-lookup"><span data-stu-id="0921d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0921d-107">BeginCustomDump – metoda</span><span class="sxs-lookup"><span data-stu-id="0921d-107">BeginCustomDump Method</span></span>](iclrerrorreportingmanager-begincustomdump-method.md)|<span data-ttu-id="0921d-108">Určuje konfiguraci vlastních výpisů paměti zásobníku pro zasílání zpráv o chybách.</span><span class="sxs-lookup"><span data-stu-id="0921d-108">Specifies the configuration of custom stack dumps for error reporting.</span></span>|  
|[<span data-ttu-id="0921d-109">EndCustomDump – metoda</span><span class="sxs-lookup"><span data-stu-id="0921d-109">EndCustomDump Method</span></span>](iclrerrorreportingmanager-endcustomdump-method.md)|<span data-ttu-id="0921d-110">Vymaže vlastní konfiguraci výpisu zásobníku, která byla nastavena starším voláním `BeginCustomDump` .</span><span class="sxs-lookup"><span data-stu-id="0921d-110">Clears the custom stack dump configuration that was set by an earlier call to `BeginCustomDump`.</span></span>|  
|[<span data-ttu-id="0921d-111">GetBucketParametersForCurrentException – metoda</span><span class="sxs-lookup"><span data-stu-id="0921d-111">GetBucketParametersForCurrentException Method</span></span>](iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|<span data-ttu-id="0921d-112">Získá blok programu Watson pro aktuální výjimku v volajícím vlákně.</span><span class="sxs-lookup"><span data-stu-id="0921d-112">Gets the Watson bucket for the current exception on the calling thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0921d-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0921d-113">Remarks</span></span>  
 <span data-ttu-id="0921d-114">`BeginCustomDump`Metoda nastavuje vlastní konfiguraci výpisu zásobníku.</span><span class="sxs-lookup"><span data-stu-id="0921d-114">The `BeginCustomDump` method sets custom stack dump configuration.</span></span> <span data-ttu-id="0921d-115">`EndCustomDump`Metoda vymaže vlastní konfiguraci výpisu zásobníku a uvolní všechny přidružené stavy.</span><span class="sxs-lookup"><span data-stu-id="0921d-115">The `EndCustomDump` method clears the custom stack dump configuration and frees any associated state.</span></span> <span data-ttu-id="0921d-116">Tato metoda by měla být volána po dokončení vlastního výpisu paměti.</span><span class="sxs-lookup"><span data-stu-id="0921d-116">It should be called after the custom dump is complete.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0921d-117">Selhání volání `EndCustomDump` způsobuje nevrácení paměti.</span><span class="sxs-lookup"><span data-stu-id="0921d-117">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0921d-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0921d-118">Requirements</span></span>  
 <span data-ttu-id="0921d-119">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0921d-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0921d-120">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0921d-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0921d-121">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0921d-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0921d-122">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0921d-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0921d-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="0921d-123">See also</span></span>

- [<span data-ttu-id="0921d-124">ECustomDumpItemKind – výčet</span><span class="sxs-lookup"><span data-stu-id="0921d-124">ECustomDumpItemKind Enumeration</span></span>](ecustomdumpitemkind-enumeration.md)
- [<span data-ttu-id="0921d-125">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="0921d-125">Hosting Interfaces</span></span>](hosting-interfaces.md)
