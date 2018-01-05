---
title: "ECustomDumpFlavor – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ECustomDumpFlavor
api_location: mscoree.dll
api_type: COM
f1_keywords: ECustomDumpFlavor
helpviewer_keywords: ECustomDumpFlavor enumeration [.NET Framework hosting]
ms.assetid: b39b3320-fac7-41f1-9a03-ab6fb0cd89c7
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a063dd6b50566d0bff393853015efc6a15f8cee1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ecustomdumpflavor-enumeration"></a><span data-ttu-id="af8ad-102">ECustomDumpFlavor – výčet</span><span class="sxs-lookup"><span data-stu-id="af8ad-102">ECustomDumpFlavor Enumeration</span></span>
<span data-ttu-id="af8ad-103">Obsahuje hodnoty, které označují, které položky, které chcete zahrnout do podmnožinu haldy vlastní dump při zasílání zpráv o chybách.</span><span class="sxs-lookup"><span data-stu-id="af8ad-103">Contains values that indicate which items to include in a custom subset of a heap dump when reporting errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af8ad-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af8ad-104">Syntax</span></span>  
  
```  
typedef enum {  
    DUMP_FLAVOR_Mini            = 1,  
    DUMP_FLAVOR_NonHeapCLRState = 2  
} ECustomDumpFlavor;  
```  
  
## <a name="members"></a><span data-ttu-id="af8ad-105">Členové</span><span class="sxs-lookup"><span data-stu-id="af8ad-105">Members</span></span>  
  
|<span data-ttu-id="af8ad-106">Člen</span><span class="sxs-lookup"><span data-stu-id="af8ad-106">Member</span></span>|<span data-ttu-id="af8ad-107">Popis</span><span class="sxs-lookup"><span data-stu-id="af8ad-107">Description</span></span>|  
|------------|-----------------|  
|`DUMP_FLAVOR_Mini`|<span data-ttu-id="af8ad-108">Určuje, že by měl vlastní haldy výpisu spusťte jako minimální výpis a zahrnují doplňující data zadané žádné [customdumpitem –](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) instance předána metodě stejné.</span><span class="sxs-lookup"><span data-stu-id="af8ad-108">Specifies that the custom heap dump should start as a minidump and include extra data specified by any [CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) instances passed to the same method.</span></span>|  
|`DUMP_FLAVOR_NonHeapCLRState`|<span data-ttu-id="af8ad-109">Určuje, že vlastní haldy výpisu byste měli získat všechna data stavu runtime, která nebyla přidělena dynamicky.</span><span class="sxs-lookup"><span data-stu-id="af8ad-109">Specifies that the custom heap dump should gather all run-time state data that was not dynamically allocated.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af8ad-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="af8ad-110">Remarks</span></span>  
 <span data-ttu-id="af8ad-111">Parametr typu `ECustomDumpFlavor` je předán [iclrerrorreportingmanager::begincustomdump –](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="af8ad-111">A parameter of type `ECustomDumpFlavor` is passed to the [ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af8ad-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="af8ad-112">Requirements</span></span>  
 <span data-ttu-id="af8ad-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af8ad-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af8ad-114">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="af8ad-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="af8ad-115">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="af8ad-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="af8ad-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af8ad-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af8ad-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="af8ad-117">See Also</span></span>  
 [<span data-ttu-id="af8ad-118">ECustomDumpItemKind – výčet</span><span class="sxs-lookup"><span data-stu-id="af8ad-118">ECustomDumpItemKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)  
 [<span data-ttu-id="af8ad-119">ICLRErrorReportingManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="af8ad-119">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 [<span data-ttu-id="af8ad-120">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="af8ad-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
