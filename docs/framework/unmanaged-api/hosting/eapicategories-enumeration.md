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
ms.openlocfilehash: 0fd9409a5157e1013365c94f01631f130a76f54b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131215"
---
# <a name="eapicategories-enumeration"></a><span data-ttu-id="20d0c-102">EApiCategories – výčet</span><span class="sxs-lookup"><span data-stu-id="20d0c-102">EApiCategories Enumeration</span></span>
<span data-ttu-id="20d0c-103">Popisuje kategorie schopností, které může hostitel zablokovat, aby běžel v částečně důvěryhodném kódu.</span><span class="sxs-lookup"><span data-stu-id="20d0c-103">Describes the categories of capabilities that the host can block from running in partially trusted code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20d0c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20d0c-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="20d0c-105">Členové</span><span class="sxs-lookup"><span data-stu-id="20d0c-105">Members</span></span>  
  
|<span data-ttu-id="20d0c-106">Člen</span><span class="sxs-lookup"><span data-stu-id="20d0c-106">Member</span></span>|<span data-ttu-id="20d0c-107">Popis</span><span class="sxs-lookup"><span data-stu-id="20d0c-107">Description</span></span>|  
|------------|-----------------|  
|`eAll`|<span data-ttu-id="20d0c-108">Určuje, že všechny spravované třídy a členy, které jsou pokryté jinými `EApiCategories` poli, se mají zablokovat spuštění v částečně důvěryhodném kódu.</span><span class="sxs-lookup"><span data-stu-id="20d0c-108">Specifies that all managed classes and members that are covered by other `EApiCategories` fields be blocked from running in partially trusted code.</span></span>|  
|`eExternalProcessMgmt`|<span data-ttu-id="20d0c-109">Určuje, že spravované třídy a členy, které umožňují vytvoření, manipulaci a zničení externích procesů, se mají zablokovat spouštění v částečně důvěryhodném kódu.</span><span class="sxs-lookup"><span data-stu-id="20d0c-109">Specifies that managed classes and members that allow the creation, manipulation, and destruction of external processes be blocked from running in partially trusted code.</span></span>|  
|`eExternalThreading`|<span data-ttu-id="20d0c-110">Určuje, že spravované třídy a členy, které umožňují vytvoření, manipulaci a zničení externích vláken, budou zablokovány spuštění v částečně důvěryhodném kódu.</span><span class="sxs-lookup"><span data-stu-id="20d0c-110">Specifies that managed classes and members that allow the creation, manipulation, and destruction of external threads be blocked from running in partially trusted code.</span></span>|  
|`eMayLeakOnAbort`|<span data-ttu-id="20d0c-111">Určuje, že spravované typy a členy, které by mohly způsobit nevracení paměti při přerušení, se zablokují pro spuštění v částečně důvěryhodném kódu.</span><span class="sxs-lookup"><span data-stu-id="20d0c-111">Specifies that managed types and members that could potentially leak memory on abort be blocked from running in partially trusted code.</span></span>|  
|`eNoCategory`|<span data-ttu-id="20d0c-112">Určuje, že žádné kategorie spravovaného kódu není možné zablokovat spuštění v částečně důvěryhodném kódu.</span><span class="sxs-lookup"><span data-stu-id="20d0c-112">Specifies that no managed code categories be blocked from running in partially trusted code.</span></span>|  
|`eSecurityInfrastructure`|<span data-ttu-id="20d0c-113">Určuje, že infrastruktura zabezpečení modulu CLR (Common Language Runtime) je zablokovaná pro použití částečně důvěryhodným kódem.</span><span class="sxs-lookup"><span data-stu-id="20d0c-113">Specifies that the common language runtime (CLR) security infrastructure be blocked from being used by partially trusted code.</span></span>|  
|`eSelfAffectingProcessMgmt`|<span data-ttu-id="20d0c-114">Určuje, že spravované třídy a členy, jejichž schopnosti mohou ovlivnit hostovaný proces, mají zablokovaný běh v částečně důvěryhodném kódu.</span><span class="sxs-lookup"><span data-stu-id="20d0c-114">Specifies that managed classes and members whose capabilities can affect the hosted process be blocked from running in partially trusted code.</span></span>|  
|`eSelfAffectingThreading`|<span data-ttu-id="20d0c-115">Určuje, že spravované třídy a členy, jejichž schopnosti mohou ovlivnit vlákna v hostovaném procesu, jsou zablokovány pro spuštění v částečně důvěryhodném kódu.</span><span class="sxs-lookup"><span data-stu-id="20d0c-115">Specifies that managed classes and members whose capabilities can affect threads in the hosted process be blocked from running in partially trusted code.</span></span>|  
|`eSharedState`|<span data-ttu-id="20d0c-116">Určuje, že spravované třídy a členy, které zveřejňují sdílený stav, budou zablokovány spuštění v částečně důvěryhodném kódu.</span><span class="sxs-lookup"><span data-stu-id="20d0c-116">Specifies that managed classes and members that expose shared state be blocked from running in partially trusted code.</span></span>|  
|`eSynchronization`|<span data-ttu-id="20d0c-117">Určuje, že se mají blokované třídy a členy společného jazykového modulu runtime, které umožňují blokovat zámkům, blokovat spuštění v částečně důvěryhodném kódu.</span><span class="sxs-lookup"><span data-stu-id="20d0c-117">Specifies that common language runtime classes and members that allow user code to hold locks be blocked from running in partially trusted code.</span></span>|  
|`eUI`|<span data-ttu-id="20d0c-118">Určuje, že spravované třídy a členy, které povolují nebo vyžadují lidskou interakci, se zablokují, aby se spustily v částečně důvěryhodném kódu.</span><span class="sxs-lookup"><span data-stu-id="20d0c-118">Specifies that managed classes and members that allow or require human interaction be blocked from running in partially trusted code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20d0c-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="20d0c-119">Remarks</span></span>  
 <span data-ttu-id="20d0c-120">Metoda [ICLRHostProtectionManager:: SetProtectedCategories –](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md) přebírá parametr typu `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="20d0c-120">The [ICLRHostProtectionManager::SetProtectedCategories](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md) method takes a parameter of type `EApiCategories`.</span></span>  
  
 <span data-ttu-id="20d0c-121">Výčet `EApiCategories` a metoda `SetProtectedCategories` přímo souvisí se spravovanou třídou <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="20d0c-121">The `EApiCategories` enumeration and the `SetProtectedCategories` method are directly related to the managed <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="20d0c-122">Spravovaná třída se používá s výčtem <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType>, jehož hodnoty odpovídají přímo `EApiCategories` hodnotám, pro označení spravovaných typů a členů, které zpřístupňují funkce odpovídající kategoriím popsaným `EApiCategories`.</span><span class="sxs-lookup"><span data-stu-id="20d0c-122">The managed class is used with the <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> enumeration, whose values correspond directly to the `EApiCategories` values, to mark managed types and members that expose capabilities corresponding to the categories described by `EApiCategories`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20d0c-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="20d0c-123">Requirements</span></span>  
 <span data-ttu-id="20d0c-124">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20d0c-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20d0c-125">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="20d0c-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="20d0c-126">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="20d0c-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="20d0c-127">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20d0c-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20d0c-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="20d0c-128">See also</span></span>

- [<span data-ttu-id="20d0c-129">ICLRHostProtectionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="20d0c-129">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="20d0c-130">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="20d0c-130">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
