---
title: ECustomDumpFlavor – výčet
ms.date: 03/30/2017
api_name:
- ECustomDumpFlavor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ECustomDumpFlavor
helpviewer_keywords:
- ECustomDumpFlavor enumeration [.NET Framework hosting]
ms.assetid: b39b3320-fac7-41f1-9a03-ab6fb0cd89c7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d1e69d9cbf39049e82803d2f7bc795cc9fd0b368
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59154437"
---
# <a name="ecustomdumpflavor-enumeration"></a><span data-ttu-id="2bb2a-102">ECustomDumpFlavor – výčet</span><span class="sxs-lookup"><span data-stu-id="2bb2a-102">ECustomDumpFlavor Enumeration</span></span>
<span data-ttu-id="2bb2a-103">Obsahuje hodnoty, které označují, položky, které mají být zahrnuty podmnožinu haldu vlastní výpis paměti při hlášení chyby.</span><span class="sxs-lookup"><span data-stu-id="2bb2a-103">Contains values that indicate which items to include in a custom subset of a heap dump when reporting errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bb2a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2bb2a-104">Syntax</span></span>  
  
```  
typedef enum {  
    DUMP_FLAVOR_Mini            = 1,  
    DUMP_FLAVOR_NonHeapCLRState = 2  
} ECustomDumpFlavor;  
```  
  
## <a name="members"></a><span data-ttu-id="2bb2a-105">Členové</span><span class="sxs-lookup"><span data-stu-id="2bb2a-105">Members</span></span>  
  
|<span data-ttu-id="2bb2a-106">Člen</span><span class="sxs-lookup"><span data-stu-id="2bb2a-106">Member</span></span>|<span data-ttu-id="2bb2a-107">Popis</span><span class="sxs-lookup"><span data-stu-id="2bb2a-107">Description</span></span>|  
|------------|-----------------|  
|`DUMP_FLAVOR_Mini`|<span data-ttu-id="2bb2a-108">Určuje, že výpis paměti haldy vlastní by měl spustit jako minimální výpis a zahrnují doplňující data zadaná žádné [customdumpitem –](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) instance předána metodě stejné.</span><span class="sxs-lookup"><span data-stu-id="2bb2a-108">Specifies that the custom heap dump should start as a minidump and include extra data specified by any [CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) instances passed to the same method.</span></span>|  
|`DUMP_FLAVOR_NonHeapCLRState`|<span data-ttu-id="2bb2a-109">Určuje, že výpis paměti haldy vlastní byste měli získat všechna data o stavu za běhu, který nebyl přidělen dynamicky.</span><span class="sxs-lookup"><span data-stu-id="2bb2a-109">Specifies that the custom heap dump should gather all run-time state data that was not dynamically allocated.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2bb2a-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2bb2a-110">Remarks</span></span>  
 <span data-ttu-id="2bb2a-111">Parametr typu `ECustomDumpFlavor` je předán [iclrerrorreportingmanager::begincustomdump –](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="2bb2a-111">A parameter of type `ECustomDumpFlavor` is passed to the [ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bb2a-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2bb2a-112">Requirements</span></span>  
 <span data-ttu-id="2bb2a-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2bb2a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2bb2a-114">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2bb2a-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2bb2a-115">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2bb2a-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2bb2a-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2bb2a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bb2a-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2bb2a-117">See also</span></span>

- [<span data-ttu-id="2bb2a-118">ECustomDumpItemKind – výčet</span><span class="sxs-lookup"><span data-stu-id="2bb2a-118">ECustomDumpItemKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)
- [<span data-ttu-id="2bb2a-119">ICLRErrorReportingManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2bb2a-119">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="2bb2a-120">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="2bb2a-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
