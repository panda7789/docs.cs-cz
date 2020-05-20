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
ms.openlocfilehash: d31b0190ef9a697fb27c849db080bec6c57618ae
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616382"
---
# <a name="eapicategories-enumeration"></a><span data-ttu-id="25dd9-102">EApiCategories – výčet</span><span class="sxs-lookup"><span data-stu-id="25dd9-102">EApiCategories Enumeration</span></span>
<span data-ttu-id="25dd9-103">Popisuje kategorie schopností, které může hostitel zablokovat, aby běžel v částečně důvěryhodném kódu.</span><span class="sxs-lookup"><span data-stu-id="25dd9-103">Describes the categories of capabilities that the host can block from running in partially trusted code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25dd9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25dd9-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="25dd9-105">Členové</span><span class="sxs-lookup"><span data-stu-id="25dd9-105">Members</span></span>  
  
|<span data-ttu-id="25dd9-106">Člen</span><span class="sxs-lookup"><span data-stu-id="25dd9-106">Member</span></span>|<span data-ttu-id="25dd9-107">Popis</span><span class="sxs-lookup"><span data-stu-id="25dd9-107">Description</span></span>|  
|------------|-----------------|  
|`eAll`|<span data-ttu-id="25dd9-108">Určuje, že všechny spravované třídy a členy, které jsou pokryté ostatními `EApiCategories` poli, se mají zablokovat spouštění v částečně důvěryhodném kódu.</span><span class="sxs-lookup"><span data-stu-id="25dd9-108">Specifies that all managed classes and members that are covered by other `EApiCategories` fields be blocked from running in partially trusted code.</span></span>|  
|`eExternalProcessMgmt`|<span data-ttu-id="25dd9-109">Určuje, že spravované třídy a členy, které umožňují vytvoření, manipulaci a zničení externích procesů, se mají zablokovat spouštění v částečně důvěryhodném kódu.</span><span class="sxs-lookup"><span data-stu-id="25dd9-109">Specifies that managed classes and members that allow the creation, manipulation, and destruction of external processes be blocked from running in partially trusted code.</span></span>|  
|`eExternalThreading`|<span data-ttu-id="25dd9-110">Určuje, že spravované třídy a členy, které umožňují vytvoření, manipulaci a zničení externích vláken, budou zablokovány spuštění v částečně důvěryhodném kódu.</span><span class="sxs-lookup"><span data-stu-id="25dd9-110">Specifies that managed classes and members that allow the creation, manipulation, and destruction of external threads be blocked from running in partially trusted code.</span></span>|  
|`eMayLeakOnAbort`|<span data-ttu-id="25dd9-111">Určuje, že spravované typy a členy, které by mohly způsobit nevracení paměti při přerušení, se zablokují pro spuštění v částečně důvěryhodném kódu.</span><span class="sxs-lookup"><span data-stu-id="25dd9-111">Specifies that managed types and members that could potentially leak memory on abort be blocked from running in partially trusted code.</span></span>|  
|`eNoCategory`|<span data-ttu-id="25dd9-112">Určuje, že žádné kategorie spravovaného kódu není možné zablokovat spuštění v částečně důvěryhodném kódu.</span><span class="sxs-lookup"><span data-stu-id="25dd9-112">Specifies that no managed code categories be blocked from running in partially trusted code.</span></span>|  
|`eSecurityInfrastructure`|<span data-ttu-id="25dd9-113">Určuje, že infrastruktura zabezpečení modulu CLR (Common Language Runtime) je zablokovaná pro použití částečně důvěryhodným kódem.</span><span class="sxs-lookup"><span data-stu-id="25dd9-113">Specifies that the common language runtime (CLR) security infrastructure be blocked from being used by partially trusted code.</span></span>|  
|`eSelfAffectingProcessMgmt`|<span data-ttu-id="25dd9-114">Určuje, že spravované třídy a členy, jejichž schopnosti mohou ovlivnit hostovaný proces, mají zablokovaný běh v částečně důvěryhodném kódu.</span><span class="sxs-lookup"><span data-stu-id="25dd9-114">Specifies that managed classes and members whose capabilities can affect the hosted process be blocked from running in partially trusted code.</span></span>|  
|`eSelfAffectingThreading`|<span data-ttu-id="25dd9-115">Určuje, že spravované třídy a členy, jejichž schopnosti mohou ovlivnit vlákna v hostovaném procesu, jsou zablokovány pro spuštění v částečně důvěryhodném kódu.</span><span class="sxs-lookup"><span data-stu-id="25dd9-115">Specifies that managed classes and members whose capabilities can affect threads in the hosted process be blocked from running in partially trusted code.</span></span>|  
|`eSharedState`|<span data-ttu-id="25dd9-116">Určuje, že spravované třídy a členy, které zveřejňují sdílený stav, budou zablokovány spuštění v částečně důvěryhodném kódu.</span><span class="sxs-lookup"><span data-stu-id="25dd9-116">Specifies that managed classes and members that expose shared state be blocked from running in partially trusted code.</span></span>|  
|`eSynchronization`|<span data-ttu-id="25dd9-117">Určuje, že se mají blokované třídy a členy společného jazykového modulu runtime, které umožňují blokovat zámkům, blokovat spuštění v částečně důvěryhodném kódu.</span><span class="sxs-lookup"><span data-stu-id="25dd9-117">Specifies that common language runtime classes and members that allow user code to hold locks be blocked from running in partially trusted code.</span></span>|  
|`eUI`|<span data-ttu-id="25dd9-118">Určuje, že spravované třídy a členy, které povolují nebo vyžadují lidskou interakci, se zablokují, aby se spustily v částečně důvěryhodném kódu.</span><span class="sxs-lookup"><span data-stu-id="25dd9-118">Specifies that managed classes and members that allow or require human interaction be blocked from running in partially trusted code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25dd9-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="25dd9-119">Remarks</span></span>  
 <span data-ttu-id="25dd9-120">Metoda [ICLRHostProtectionManager:: SetProtectedCategories –](iclrhostprotectionmanager-setprotectedcategories-method.md) přebírá parametr typu `EApiCategories` .</span><span class="sxs-lookup"><span data-stu-id="25dd9-120">The [ICLRHostProtectionManager::SetProtectedCategories](iclrhostprotectionmanager-setprotectedcategories-method.md) method takes a parameter of type `EApiCategories`.</span></span>  
  
 <span data-ttu-id="25dd9-121">`EApiCategories`Výčet a `SetProtectedCategories` Metoda přímo souvisí se spravovanou <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> třídou.</span><span class="sxs-lookup"><span data-stu-id="25dd9-121">The `EApiCategories` enumeration and the `SetProtectedCategories` method are directly related to the managed <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="25dd9-122">Spravovaná třída se používá společně s <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> výčtem, jejichž hodnoty odpovídají přímo `EApiCategories` hodnotám, pro označení spravovaných typů a členů, které zpřístupňují funkce odpovídající kategoriím popsaným v `EApiCategories` .</span><span class="sxs-lookup"><span data-stu-id="25dd9-122">The managed class is used with the <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> enumeration, whose values correspond directly to the `EApiCategories` values, to mark managed types and members that expose capabilities corresponding to the categories described by `EApiCategories`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25dd9-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="25dd9-123">Requirements</span></span>  
 <span data-ttu-id="25dd9-124">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25dd9-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25dd9-125">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="25dd9-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="25dd9-126">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="25dd9-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="25dd9-127">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25dd9-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25dd9-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="25dd9-128">See also</span></span>

- [<span data-ttu-id="25dd9-129">ICLRHostProtectionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="25dd9-129">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="25dd9-130">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="25dd9-130">Hosting Enumerations</span></span>](hosting-enumerations.md)
