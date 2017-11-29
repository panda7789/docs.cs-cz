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
ms.openlocfilehash: 2a7317a3a12acef2a16deebab9a1e1b10205ebf6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ecustomdumpflavor-enumeration"></a><span data-ttu-id="dc47c-102">ECustomDumpFlavor – výčet</span><span class="sxs-lookup"><span data-stu-id="dc47c-102">ECustomDumpFlavor Enumeration</span></span>
<span data-ttu-id="dc47c-103">Obsahuje hodnoty, které označují, které položky, které chcete zahrnout do podmnožinu haldy vlastní dump při zasílání zpráv o chybách.</span><span class="sxs-lookup"><span data-stu-id="dc47c-103">Contains values that indicate which items to include in a custom subset of a heap dump when reporting errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc47c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc47c-104">Syntax</span></span>  
  
```  
typedef enum {  
    DUMP_FLAVOR_Mini            = 1,  
    DUMP_FLAVOR_NonHeapCLRState = 2  
} ECustomDumpFlavor;  
```  
  
## <a name="members"></a><span data-ttu-id="dc47c-105">Členové</span><span class="sxs-lookup"><span data-stu-id="dc47c-105">Members</span></span>  
  
|<span data-ttu-id="dc47c-106">Člen</span><span class="sxs-lookup"><span data-stu-id="dc47c-106">Member</span></span>|<span data-ttu-id="dc47c-107">Popis</span><span class="sxs-lookup"><span data-stu-id="dc47c-107">Description</span></span>|  
|------------|-----------------|  
|`DUMP_FLAVOR_Mini`|<span data-ttu-id="dc47c-108">Určuje, že by měl vlastní haldy výpisu spusťte jako minimální výpis a zahrnují doplňující data zadané žádné [customdumpitem –](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) instance předána metodě stejné.</span><span class="sxs-lookup"><span data-stu-id="dc47c-108">Specifies that the custom heap dump should start as a minidump and include extra data specified by any [CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) instances passed to the same method.</span></span>|  
|`DUMP_FLAVOR_NonHeapCLRState`|<span data-ttu-id="dc47c-109">Určuje, že vlastní haldy výpisu byste měli získat všechna data stavu runtime, která nebyla přidělena dynamicky.</span><span class="sxs-lookup"><span data-stu-id="dc47c-109">Specifies that the custom heap dump should gather all run-time state data that was not dynamically allocated.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc47c-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dc47c-110">Remarks</span></span>  
 <span data-ttu-id="dc47c-111">Parametr typu `ECustomDumpFlavor` je předán [iclrerrorreportingmanager::begincustomdump –](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="dc47c-111">A parameter of type `ECustomDumpFlavor` is passed to the [ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc47c-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dc47c-112">Requirements</span></span>  
 <span data-ttu-id="dc47c-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc47c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc47c-114">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dc47c-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dc47c-115">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dc47c-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dc47c-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc47c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc47c-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="dc47c-117">See Also</span></span>  
 [<span data-ttu-id="dc47c-118">ECustomDumpItemKind – výčet</span><span class="sxs-lookup"><span data-stu-id="dc47c-118">ECustomDumpItemKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)  
 [<span data-ttu-id="dc47c-119">Iclrerrorreportingmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dc47c-119">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 [<span data-ttu-id="dc47c-120">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="dc47c-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
