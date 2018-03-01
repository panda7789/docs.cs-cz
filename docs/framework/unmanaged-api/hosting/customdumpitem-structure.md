---
title: "CustomDumpItem – struktura"
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
- CustomDumpItem
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CustomDumpItem
helpviewer_keywords:
- CustomDumpItem structure [.NET Framework hosting]
ms.assetid: fd9085ff-7beb-4c38-97f0-037cd8ba4f65
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 47fd4e1dd3889cc7eeaa37457b47d9b2fd6dd8b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="customdumpitem-structure"></a><span data-ttu-id="2c654-102">CustomDumpItem – struktura</span><span class="sxs-lookup"><span data-stu-id="2c654-102">CustomDumpItem Structure</span></span>
<span data-ttu-id="2c654-103">Popisuje položku, kterou chcete přidat do vlastní výpis v zasílání zpráv o chybách.</span><span class="sxs-lookup"><span data-stu-id="2c654-103">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c654-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2c654-104">Syntax</span></span>  
  
```  
struct {  
    ECustomDumpItemKind itemKind;   
    union {  
        UINT_PTR pReserved;  
    }  
} CustomDumpItem;  
```  
  
## <a name="members"></a><span data-ttu-id="2c654-105">Členové</span><span class="sxs-lookup"><span data-stu-id="2c654-105">Members</span></span>  
  
|<span data-ttu-id="2c654-106">Člen</span><span class="sxs-lookup"><span data-stu-id="2c654-106">Member</span></span>|<span data-ttu-id="2c654-107">Popis</span><span class="sxs-lookup"><span data-stu-id="2c654-107">Description</span></span>|  
|------------|-----------------|  
|`itemKind`|<span data-ttu-id="2c654-108">[ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) hodnotu, která určuje druh položky, které chcete přidat.</span><span class="sxs-lookup"><span data-stu-id="2c654-108">An [ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) value that indicates the kind of item to be added.</span></span>|  
|`pReserved`|<span data-ttu-id="2c654-109">Není právě používána.</span><span class="sxs-lookup"><span data-stu-id="2c654-109">Not currently used.</span></span> <span data-ttu-id="2c654-110">Všechny položky přidány do sjednocení nesmí být větší než velikost ukazatele.</span><span class="sxs-lookup"><span data-stu-id="2c654-110">Any items added to the union must be no larger than pointer size.</span></span> <span data-ttu-id="2c654-111">Pokud `struct` je potřeba, musí přidělení samostatně a přejděte k němu.</span><span class="sxs-lookup"><span data-stu-id="2c654-111">If a `struct` is required, you must allocate it separately and point to it.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c654-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2c654-112">Remarks</span></span>  
 <span data-ttu-id="2c654-113">[Iclrerrorreportingmanager::begincustomdump –](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) přebírá parametr typu `CustomDumpItem`.</span><span class="sxs-lookup"><span data-stu-id="2c654-113">[ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) takes a parameter of type `CustomDumpItem`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c654-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2c654-114">Requirements</span></span>  
 <span data-ttu-id="2c654-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c654-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c654-116">**Záhlaví:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="2c654-116">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="2c654-117">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2c654-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2c654-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c654-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c654-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="2c654-119">See Also</span></span>  
 [<span data-ttu-id="2c654-120">Struktury pro hostování</span><span class="sxs-lookup"><span data-stu-id="2c654-120">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
