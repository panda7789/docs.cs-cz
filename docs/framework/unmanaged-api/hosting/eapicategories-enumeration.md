---
title: "EApiCategories – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EApiCategories
api_location: mscoree.dll
api_type: COM
f1_keywords: EApiCategories
helpviewer_keywords: EApiCategories enumeration [.NET Framework hosting]
ms.assetid: 3c4a8a5a-8a46-4ac9-947f-4959bc9d6ac6
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: eaff0133020fe84e58f8a130bffc8ddc2a55a19d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="eapicategories-enumeration"></a><span data-ttu-id="cf7a3-102">EApiCategories – výčet</span><span class="sxs-lookup"><span data-stu-id="cf7a3-102">EApiCategories Enumeration</span></span>
<span data-ttu-id="cf7a3-103">Popisuje kategorie funkcí, které hostitele může blokovat ve spuštění v částečně důvěryhodným kódem.</span><span class="sxs-lookup"><span data-stu-id="cf7a3-103">Describes the categories of capabilities that the host can block from running in partially trusted code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf7a3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cf7a3-104">Syntax</span></span>  
  
```  
typedef enum {  
    eNoCategory               = 0,  
    eSynchronization          = 0x1,  
    eSharedState              = 0x2,  
    eExternalProcessMgmt      = 0x4,  
    eSelfAffectingProcessMgmt = 0x8,  
    eExternalThreading        = 0x10,  
    eSelfAffectingThreading   = 0x20,  
    eSecurityInfrastructure   = 0x40,  
    eUI                       = 0x80,  
    eMayLeakOnAbort           = 0x100,  
    eAll                      = 0x1ff  
} EHostProtectionCategories;  
```  
  
## <a name="members"></a><span data-ttu-id="cf7a3-105">Členové</span><span class="sxs-lookup"><span data-stu-id="cf7a3-105">Members</span></span>  
  
|<span data-ttu-id="cf7a3-106">Člen</span><span class="sxs-lookup"><span data-stu-id="cf7a3-106">Member</span></span>|<span data-ttu-id="cf7a3-107">Popis</span><span class="sxs-lookup"><span data-stu-id="cf7a3-107">Description</span></span>|  
|------------|-----------------|  
|`eAll`|<span data-ttu-id="cf7a3-108">Určuje, že všechny spravované třídy a členové, které jsou předmětem dalších `EApiCategories` pole zablokovat spuštění v částečně důvěryhodným kódem.</span><span class="sxs-lookup"><span data-stu-id="cf7a3-108">Specifies that all managed classes and members that are covered by other `EApiCategories` fields be blocked from running in partially trusted code.</span></span>|  
|`eExternalProcessMgmt`|<span data-ttu-id="cf7a3-109">Určuje, že spravované třídy a členy, které umožňují vytváření, manipulaci a odstraňování externí procesů zablokovat spuštění v částečně důvěryhodným kódem.</span><span class="sxs-lookup"><span data-stu-id="cf7a3-109">Specifies that managed classes and members that allow the creation, manipulation, and destruction of external processes be blocked from running in partially trusted code.</span></span>|  
|`eExternalThreading`|<span data-ttu-id="cf7a3-110">Určuje, že spravované třídy a členy, které umožňují vytváření, manipulaci a odstraňování externí vláken zablokovat spuštění v částečně důvěryhodným kódem.</span><span class="sxs-lookup"><span data-stu-id="cf7a3-110">Specifies that managed classes and members that allow the creation, manipulation, and destruction of external threads be blocked from running in partially trusted code.</span></span>|  
|`eMayLeakOnAbort`|<span data-ttu-id="cf7a3-111">Určuje, že spravované typy a členy, které může potenciálně nastat únik paměti na přerušení zablokovat spuštění v částečně důvěryhodným kódem.</span><span class="sxs-lookup"><span data-stu-id="cf7a3-111">Specifies that managed types and members that could potentially leak memory on abort be blocked from running in partially trusted code.</span></span>|  
|`eNoCategory`|<span data-ttu-id="cf7a3-112">Určuje, že žádné kategorie spravovaného kódu zablokovat spuštění v částečně důvěryhodným kódem.</span><span class="sxs-lookup"><span data-stu-id="cf7a3-112">Specifies that no managed code categories be blocked from running in partially trusted code.</span></span>|  
|`eSecurityInfrastructure`|<span data-ttu-id="cf7a3-113">Určuje, že common language runtime (CLR) zabezpečení infrastructure blokovat používá částečně důvěryhodným kódem.</span><span class="sxs-lookup"><span data-stu-id="cf7a3-113">Specifies that the common language runtime (CLR) security infrastructure be blocked from being used by partially trusted code.</span></span>|  
|`eSelfAffectingProcessMgmt`|<span data-ttu-id="cf7a3-114">Určuje, že spravované třídy a členy, jejichž možnosti může ovlivnit proces hostované zablokovat spuštění v částečně důvěryhodným kódem.</span><span class="sxs-lookup"><span data-stu-id="cf7a3-114">Specifies that managed classes and members whose capabilities can affect the hosted process be blocked from running in partially trusted code.</span></span>|  
|`eSelfAffectingThreading`|<span data-ttu-id="cf7a3-115">Určuje, že spravované třídy a členy, jejichž možnosti může ovlivnit vláken v procesu hostované zablokovat spuštění v částečně důvěryhodným kódem.</span><span class="sxs-lookup"><span data-stu-id="cf7a3-115">Specifies that managed classes and members whose capabilities can affect threads in the hosted process be blocked from running in partially trusted code.</span></span>|  
|`eSharedState`|<span data-ttu-id="cf7a3-116">Určuje, že spravované třídy a členy, které zveřejňují sdíleného stavu zablokovat spuštění v částečně důvěryhodným kódem.</span><span class="sxs-lookup"><span data-stu-id="cf7a3-116">Specifies that managed classes and members that expose shared state be blocked from running in partially trusted code.</span></span>|  
|`eSynchronization`|<span data-ttu-id="cf7a3-117">Určuje, že common language runtime třídy a členů, které povolit uživatelský kód pro uložení zámky zablokovat spuštění v částečně důvěryhodným kódem.</span><span class="sxs-lookup"><span data-stu-id="cf7a3-117">Specifies that common language runtime classes and members that allow user code to hold locks be blocked from running in partially trusted code.</span></span>|  
|`eUI`|<span data-ttu-id="cf7a3-118">Určuje, že spravované třídy a členů, která povolují nebo vyžadovat zásahem ze strany zablokovat spuštění v částečně důvěryhodným kódem.</span><span class="sxs-lookup"><span data-stu-id="cf7a3-118">Specifies that managed classes and members that allow or require human interaction be blocked from running in partially trusted code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cf7a3-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cf7a3-119">Remarks</span></span>  
 <span data-ttu-id="cf7a3-120">[Iclrhostprotectionmanager::setprotectedcategories –](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md) metoda přebírá parametr typu `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="cf7a3-120">The [ICLRHostProtectionManager::SetProtectedCategories](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md) method takes a parameter of type `EApiCategories`.</span></span>  
  
 <span data-ttu-id="cf7a3-121">`EApiCategories` – Výčet a `SetProtectedCategories` přímo souvisí s metoda na spravovaný <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="cf7a3-121">The `EApiCategories` enumeration and the `SetProtectedCategories` method are directly related to the managed <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="cf7a3-122">Spravované třídy se používá s <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> výčtu, jejichž hodnoty odpovídají přímo `EApiCategories` hodnoty k označení spravované typy a členy, které zveřejňují možnosti odpovídající kategorie popsaného `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="cf7a3-122">The managed class is used with the <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> enumeration, whose values correspond directly to the `EApiCategories` values, to mark managed types and members that expose capabilities corresponding to the categories described by `EApiCategories`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf7a3-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cf7a3-123">Requirements</span></span>  
 <span data-ttu-id="cf7a3-124">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf7a3-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf7a3-125">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cf7a3-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cf7a3-126">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cf7a3-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cf7a3-127">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf7a3-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf7a3-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="cf7a3-128">See Also</span></span>  
 [<span data-ttu-id="cf7a3-129">Iclrhostprotectionmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cf7a3-129">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 [<span data-ttu-id="cf7a3-130">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="cf7a3-130">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
