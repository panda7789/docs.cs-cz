---
title: EApiCategories – výčet
ms.date: 03/30/2017
api_name:
- EApiCategories
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EApiCategories
helpviewer_keywords:
- EApiCategories enumeration [.NET Framework hosting]
ms.assetid: 3c4a8a5a-8a46-4ac9-947f-4959bc9d6ac6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3debd3f13d78841188dd8c900f51c0110e1d4c67
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59086452"
---
# <a name="eapicategories-enumeration"></a><span data-ttu-id="a40f5-102">EApiCategories – výčet</span><span class="sxs-lookup"><span data-stu-id="a40f5-102">EApiCategories Enumeration</span></span>
<span data-ttu-id="a40f5-103">Popisuje kategorie funkcí, které hostitele může blokovat spouštění v částečně důvěryhodným kódem.</span><span class="sxs-lookup"><span data-stu-id="a40f5-103">Describes the categories of capabilities that the host can block from running in partially trusted code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a40f5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a40f5-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="a40f5-105">Členové</span><span class="sxs-lookup"><span data-stu-id="a40f5-105">Members</span></span>  
  
|<span data-ttu-id="a40f5-106">Člen</span><span class="sxs-lookup"><span data-stu-id="a40f5-106">Member</span></span>|<span data-ttu-id="a40f5-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a40f5-107">Description</span></span>|  
|------------|-----------------|  
|`eAll`|<span data-ttu-id="a40f5-108">Určuje, že všechny spravované třídy a členy, které jsou zahrnuté do jiné `EApiCategories` pole zablokováno v částečně důvěryhodným kódem.</span><span class="sxs-lookup"><span data-stu-id="a40f5-108">Specifies that all managed classes and members that are covered by other `EApiCategories` fields be blocked from running in partially trusted code.</span></span>|  
|`eExternalProcessMgmt`|<span data-ttu-id="a40f5-109">Určuje, že spravované třídy a členy, které umožňují vytváření, manipulaci a zničení procesů, externím zablokováno v částečně důvěryhodným kódem.</span><span class="sxs-lookup"><span data-stu-id="a40f5-109">Specifies that managed classes and members that allow the creation, manipulation, and destruction of external processes be blocked from running in partially trusted code.</span></span>|  
|`eExternalThreading`|<span data-ttu-id="a40f5-110">Určuje, že spravované třídy a členy, které umožňují vytváření, manipulaci a zničení externí vláken zablokováno v částečně důvěryhodným kódem.</span><span class="sxs-lookup"><span data-stu-id="a40f5-110">Specifies that managed classes and members that allow the creation, manipulation, and destruction of external threads be blocked from running in partially trusted code.</span></span>|  
|`eMayLeakOnAbort`|<span data-ttu-id="a40f5-111">Určuje, že spravované typy a členy, které může potenciálně způsobit únik paměti při přerušení zablokováno v částečně důvěryhodným kódem.</span><span class="sxs-lookup"><span data-stu-id="a40f5-111">Specifies that managed types and members that could potentially leak memory on abort be blocked from running in partially trusted code.</span></span>|  
|`eNoCategory`|<span data-ttu-id="a40f5-112">Určuje, že žádný spravovaný kód kategorie zablokováno v částečně důvěryhodným kódem.</span><span class="sxs-lookup"><span data-stu-id="a40f5-112">Specifies that no managed code categories be blocked from running in partially trusted code.</span></span>|  
|`eSecurityInfrastructure`|<span data-ttu-id="a40f5-113">Určuje, že common language runtime (CLR) zabezpečení infrastructure být blokovány z používán částečně důvěryhodným kódem.</span><span class="sxs-lookup"><span data-stu-id="a40f5-113">Specifies that the common language runtime (CLR) security infrastructure be blocked from being used by partially trusted code.</span></span>|  
|`eSelfAffectingProcessMgmt`|<span data-ttu-id="a40f5-114">Určuje, že spravované třídy a členy, jejichž schopnosti může ovlivnit proces hostované zablokováno v částečně důvěryhodným kódem.</span><span class="sxs-lookup"><span data-stu-id="a40f5-114">Specifies that managed classes and members whose capabilities can affect the hosted process be blocked from running in partially trusted code.</span></span>|  
|`eSelfAffectingThreading`|<span data-ttu-id="a40f5-115">Určuje, že spravované třídy a členy, jejichž funkce může mít vliv na vlákna v procesu hostované zablokováno v částečně důvěryhodným kódem.</span><span class="sxs-lookup"><span data-stu-id="a40f5-115">Specifies that managed classes and members whose capabilities can affect threads in the hosted process be blocked from running in partially trusted code.</span></span>|  
|`eSharedState`|<span data-ttu-id="a40f5-116">Určuje, že spravované třídy a členy, které zpřístupňují sdílený stav zablokováno v částečně důvěryhodným kódem.</span><span class="sxs-lookup"><span data-stu-id="a40f5-116">Specifies that managed classes and members that expose shared state be blocked from running in partially trusted code.</span></span>|  
|`eSynchronization`|<span data-ttu-id="a40f5-117">Určuje, že common language runtime třídy a členy, které umožňují uživatelský kód pro uložení zámky zablokováno v částečně důvěryhodným kódem.</span><span class="sxs-lookup"><span data-stu-id="a40f5-117">Specifies that common language runtime classes and members that allow user code to hold locks be blocked from running in partially trusted code.</span></span>|  
|`eUI`|<span data-ttu-id="a40f5-118">Určuje, že spravovaných tříd a členů, která povolují nebo vyžadují zásahem ze strany zablokováno v částečně důvěryhodným kódem.</span><span class="sxs-lookup"><span data-stu-id="a40f5-118">Specifies that managed classes and members that allow or require human interaction be blocked from running in partially trusted code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a40f5-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a40f5-119">Remarks</span></span>  
 <span data-ttu-id="a40f5-120">[Iclrhostprotectionmanager::setprotectedcategories –](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md) metoda přijímá parametr typu `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="a40f5-120">The [ICLRHostProtectionManager::SetProtectedCategories](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md) method takes a parameter of type `EApiCategories`.</span></span>  
  
 <span data-ttu-id="a40f5-121">`EApiCategories` Výčet a `SetProtectedCategories` přímo souvisí s metoda na spravovanou <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="a40f5-121">The `EApiCategories` enumeration and the `SetProtectedCategories` method are directly related to the managed <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="a40f5-122">Spravovaná třída se používá s <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> výčtu, jehož hodnoty odpovídají přímo `EApiCategories` hodnoty k označení spravované typy a členy, které ukazují možnosti odpovídající kategorie popsal `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="a40f5-122">The managed class is used with the <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> enumeration, whose values correspond directly to the `EApiCategories` values, to mark managed types and members that expose capabilities corresponding to the categories described by `EApiCategories`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a40f5-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a40f5-123">Requirements</span></span>  
 <span data-ttu-id="a40f5-124">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a40f5-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a40f5-125">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a40f5-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a40f5-126">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a40f5-126">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="a40f5-127">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="a40f5-127">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a40f5-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a40f5-128">See also</span></span>

- [<span data-ttu-id="a40f5-129">ICLRHostProtectionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a40f5-129">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="a40f5-130">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="a40f5-130">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
