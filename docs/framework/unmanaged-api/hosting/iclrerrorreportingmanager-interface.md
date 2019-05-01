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
ms.openlocfilehash: a20b79dd5eda9c431511cc49e7e3adaa9486b2aa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61969825"
---
# <a name="iclrerrorreportingmanager-interface"></a><span data-ttu-id="028c1-102">ICLRErrorReportingManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="028c1-102">ICLRErrorReportingManager Interface</span></span>
<span data-ttu-id="028c1-103">Poskytuje metody, které umožňují hostiteli nakonfigurovat vlastní výpisy pro hlášení chyb.</span><span class="sxs-lookup"><span data-stu-id="028c1-103">Provides methods that allow the host to configure custom stack dumps for error reporting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="028c1-104">Metody</span><span class="sxs-lookup"><span data-stu-id="028c1-104">Methods</span></span>  
  
|<span data-ttu-id="028c1-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="028c1-105">Method</span></span>|<span data-ttu-id="028c1-106">Popis</span><span class="sxs-lookup"><span data-stu-id="028c1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="028c1-107">BeginCustomDump – metoda</span><span class="sxs-lookup"><span data-stu-id="028c1-107">BeginCustomDump Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md)|<span data-ttu-id="028c1-108">Určuje konfiguraci vlastních výpisy pro hlášení chyb.</span><span class="sxs-lookup"><span data-stu-id="028c1-108">Specifies the configuration of custom stack dumps for error reporting.</span></span>|  
|[<span data-ttu-id="028c1-109">EndCustomDump – metoda</span><span class="sxs-lookup"><span data-stu-id="028c1-109">EndCustomDump Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md)|<span data-ttu-id="028c1-110">Vymaže konfiguraci vlastní zásobníku s výpisem paměti, která byla nastavena v dřívějším volání `BeginCustomDump`.</span><span class="sxs-lookup"><span data-stu-id="028c1-110">Clears the custom stack dump configuration that was set by an earlier call to `BeginCustomDump`.</span></span>|  
|[<span data-ttu-id="028c1-111">GetBucketParametersForCurrentException – metoda</span><span class="sxs-lookup"><span data-stu-id="028c1-111">GetBucketParametersForCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|<span data-ttu-id="028c1-112">Získá Watson kbelíku pro aktuální výjimky na volajícím vlákně.</span><span class="sxs-lookup"><span data-stu-id="028c1-112">Gets the Watson bucket for the current exception on the calling thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="028c1-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="028c1-113">Remarks</span></span>  
 <span data-ttu-id="028c1-114">`BeginCustomDump` Metoda nastaví konfiguraci vlastní zásobníku s výpisem paměti.</span><span class="sxs-lookup"><span data-stu-id="028c1-114">The `BeginCustomDump` method sets custom stack dump configuration.</span></span> <span data-ttu-id="028c1-115">`EndCustomDump` Metoda vymaže výpisu stavu systému configuration vlastní zásobníku a uvolní všechny přidružený stav.</span><span class="sxs-lookup"><span data-stu-id="028c1-115">The `EndCustomDump` method clears the custom stack dump configuration and frees any associated state.</span></span> <span data-ttu-id="028c1-116">By měla být volána po dokončení vlastní s výpisem paměti.</span><span class="sxs-lookup"><span data-stu-id="028c1-116">It should be called after the custom dump is complete.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="028c1-117">Nepodařilo se zavolat `EndCustomDump` způsobí, že k únik paměti.</span><span class="sxs-lookup"><span data-stu-id="028c1-117">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="028c1-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="028c1-118">Requirements</span></span>  
 <span data-ttu-id="028c1-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="028c1-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="028c1-120">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="028c1-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="028c1-121">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="028c1-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="028c1-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="028c1-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="028c1-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="028c1-123">See also</span></span>

- [<span data-ttu-id="028c1-124">ECustomDumpItemKind – výčet</span><span class="sxs-lookup"><span data-stu-id="028c1-124">ECustomDumpItemKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)
- [<span data-ttu-id="028c1-125">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="028c1-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
