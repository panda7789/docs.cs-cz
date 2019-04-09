---
title: CorDeclSecurity – výčet
ms.date: 03/30/2017
api_name:
- CorDeclSecurity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorDeclSecurity
helpviewer_keywords:
- CorDeclSecurity enumeration [.NET Framework metadata]
ms.assetid: 864f1267-d267-4696-8df7-1f83f8444d6f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5409d1b89ba3e50c4ae17ed5aa6bf063cf6c93cb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59136965"
---
# <a name="cordeclsecurity-enumeration"></a><span data-ttu-id="3a7c8-102">CorDeclSecurity – výčet</span><span class="sxs-lookup"><span data-stu-id="3a7c8-102">CorDeclSecurity Enumeration</span></span>
<span data-ttu-id="3a7c8-103">Určuje akce zabezpečení, které je možné provádět pomocí deklarativní zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="3a7c8-103">Specifies the security actions that can be performed using declarative security.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a7c8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3a7c8-104">Syntax</span></span>  
  
```  
typedef enum CorDeclSecurity {  
  
    dclActionMask               =   0x001f,  
    dclActionNil                =   0x0000,  
    dclRequest                  =   0x0001,  
    dclDemand                   =   0x0002,  
    dclAssert                   =   0x0003,  
    dclDeny                     =   0x0004,  
    dclPermitOnly               =   0x0005,  
    dclLinktimeCheck            =   0x0006,  
    dclInheritanceCheck         =   0x0007,  
    dclRequestMinimum           =   0x0008,  
    dclRequestOptional          =   0x0009,  
    dclRequestRefuse            =   0x000a,  
    dclPrejitGrant              =   0x000b,  
    dclPrejitDenied             =   0x000c,  
    dclNonCasDemand             =   0x000d,  
    dclNonCasLinkDemand         =   0x000e,  
    dclNonCasInheritance        =   0x000f,  
    dclLinkDemandChoice         =   0x0010,  
    dclInheritanceDemandChoice  =   0x0011,  
    dclDemandChoice             =   0x0012,  
    dclMaximumValue             =   0x0012  
  
} CorDeclSecurity;  
```  
  
## <a name="members"></a><span data-ttu-id="3a7c8-105">Členové</span><span class="sxs-lookup"><span data-stu-id="3a7c8-105">Members</span></span>  
  
|<span data-ttu-id="3a7c8-106">Člen</span><span class="sxs-lookup"><span data-stu-id="3a7c8-106">Member</span></span>|<span data-ttu-id="3a7c8-107">Popis</span><span class="sxs-lookup"><span data-stu-id="3a7c8-107">Description</span></span>|  
|------------|-----------------|  
|`dclActionMask`|<span data-ttu-id="3a7c8-108">Vyhrazená.</span><span class="sxs-lookup"><span data-stu-id="3a7c8-108">Reserved.</span></span>|  
|`dclActionNil`|<span data-ttu-id="3a7c8-109">Vyhrazená.</span><span class="sxs-lookup"><span data-stu-id="3a7c8-109">Reserved.</span></span>|  
|`dclRequest`|<span data-ttu-id="3a7c8-110">Vyhrazená.</span><span class="sxs-lookup"><span data-stu-id="3a7c8-110">Reserved.</span></span>|  
|`dclDemand`|<span data-ttu-id="3a7c8-111">Všichni volající v zásobníku volání vyšší se vyžadují bylo uděleno oprávnění zadané pomocí aktuálního objektu oprávnění.</span><span class="sxs-lookup"><span data-stu-id="3a7c8-111">All callers higher in the call stack are required to have been granted the permission specified by the current permission object.</span></span>|  
|`dclAssert`|<span data-ttu-id="3a7c8-112">Volající kód může přístup k prostředku označeném identifikátorem aktuálního objektu oprávnění, i v případě, že volajících výše v zásobníku byla udělena oprávnění pro přístup k prostředku</span><span class="sxs-lookup"><span data-stu-id="3a7c8-112">The calling code can access the resource identified by the current permission object, even if callers higher in the stack have not been granted permission to access the resource</span></span>|  
|`dclDeny`|<span data-ttu-id="3a7c8-113">Možnost přístupu k prostředku zadaného parametrem aktuálního objektu oprávnění je odepřen volající, i v případě, že bylo uděleno oprávnění k přístupu.</span><span class="sxs-lookup"><span data-stu-id="3a7c8-113">The ability to access the resource specified by the current permission object is denied to callers, even if they have been granted permission to access it.</span></span>|  
|`dclPermitOnly`|<span data-ttu-id="3a7c8-114">Pouze prostředků zadaných pomocí tohoto oprávnění objektu je možný i v případě, že kód bylo uděleno oprávnění pro přístup k dalším prostředkům.</span><span class="sxs-lookup"><span data-stu-id="3a7c8-114">Only the resources specified by this permission object can be accessed, even if the code has been granted permission to access other resources.</span></span>|  
|`dclLinktimeCheck`|<span data-ttu-id="3a7c8-115">Okamžitého volajícího je nutné bylo uděleno oprávnění k zadané pro dané časové období.</span><span class="sxs-lookup"><span data-stu-id="3a7c8-115">The immediate caller is required to have been granted the specified permission for a given period of time.</span></span>|  
|`dclInheritanceCheck`|<span data-ttu-id="3a7c8-116">Odvozená třída dědí jiné třídy nebo přepsání metody je potřeba zadané oprávnění udělil.</span><span class="sxs-lookup"><span data-stu-id="3a7c8-116">The derived class inheriting another class or overriding a method is required to have been granted the specified permission.</span></span>|  
|`dclRequestMinimum`|<span data-ttu-id="3a7c8-117">Volající mohl požadovat pro minimální oprávnění potřebná pro spuštění kódu.</span><span class="sxs-lookup"><span data-stu-id="3a7c8-117">The caller can request for the minimum permissions required for code to run.</span></span> <span data-ttu-id="3a7c8-118">Tato akce jde použít jenom v rámci oboru sestavení.</span><span class="sxs-lookup"><span data-stu-id="3a7c8-118">This action can only be used within the scope of the assembly.</span></span>|  
|`dclRequestOptional`|<span data-ttu-id="3a7c8-119">Volající mohl požadovat další oprávnění, které jsou volitelné (není vyžadované ke spuštění).</span><span class="sxs-lookup"><span data-stu-id="3a7c8-119">The caller can request for additional permissions that are optional (not required to run).</span></span> <span data-ttu-id="3a7c8-120">Tento požadavek implicitně odmítá všechny další oprávnění, která nejsou výslovně požadována.</span><span class="sxs-lookup"><span data-stu-id="3a7c8-120">This request implicitly refuses all other permissions not specifically requested.</span></span> <span data-ttu-id="3a7c8-121">Tato akce jde použít jenom v rámci oboru sestavení.</span><span class="sxs-lookup"><span data-stu-id="3a7c8-121">This action can only be used within the scope of the assembly.</span></span>|  
|`dclRequestRefuse`|<span data-ttu-id="3a7c8-122">Volajícího žádost o oprávnění, která může být potenciálně nebezpečného nebudou udělena.</span><span class="sxs-lookup"><span data-stu-id="3a7c8-122">The caller's request for permissions that might be misused will not be granted.</span></span> <span data-ttu-id="3a7c8-123">Tato akce jde použít jenom v rámci oboru sestavení.</span><span class="sxs-lookup"><span data-stu-id="3a7c8-123">This action can only be used within the scope of the assembly.</span></span>|  
|`dclPrejitGrant`|<span data-ttu-id="3a7c8-124">Vyhrazená.</span><span class="sxs-lookup"><span data-stu-id="3a7c8-124">Reserved.</span></span>|  
|`dclPrejitDenied`|<span data-ttu-id="3a7c8-125">Vyhrazená.</span><span class="sxs-lookup"><span data-stu-id="3a7c8-125">Reserved.</span></span>|  
|`dclNonCasDemand`|<span data-ttu-id="3a7c8-126">Vyhrazená.</span><span class="sxs-lookup"><span data-stu-id="3a7c8-126">Reserved.</span></span>|  
|`dclNonCasLinkDemand`|<span data-ttu-id="3a7c8-127">Okamžitého volajícího je nutné k zadané oprávnění udělil.</span><span class="sxs-lookup"><span data-stu-id="3a7c8-127">The immediate caller is required to have been granted the specified permission.</span></span>|  
|`dclNonCasInheritance`|<span data-ttu-id="3a7c8-128">Vyhrazená.</span><span class="sxs-lookup"><span data-stu-id="3a7c8-128">Reserved.</span></span>|  
|`dclLinkDemandChoice`|<span data-ttu-id="3a7c8-129">Vyhrazená.</span><span class="sxs-lookup"><span data-stu-id="3a7c8-129">Reserved.</span></span>|  
|`dclInheritanceDemandChoice`|<span data-ttu-id="3a7c8-130">Vyhrazená.</span><span class="sxs-lookup"><span data-stu-id="3a7c8-130">Reserved.</span></span>|  
|`dclDemandChoice`|<span data-ttu-id="3a7c8-131">Vyhrazená.</span><span class="sxs-lookup"><span data-stu-id="3a7c8-131">Reserved.</span></span>|  
|`dclMaximumValue`|<span data-ttu-id="3a7c8-132">Vyhrazená.</span><span class="sxs-lookup"><span data-stu-id="3a7c8-132">Reserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3a7c8-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3a7c8-133">Requirements</span></span>  
 <span data-ttu-id="3a7c8-134">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a7c8-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a7c8-135">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="3a7c8-135">**Header:** CorHdr.h</span></span>  
  
 **<span data-ttu-id="3a7c8-136">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="3a7c8-136">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3a7c8-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3a7c8-137">See also</span></span>

- [<span data-ttu-id="3a7c8-138">Výčty metadat</span><span class="sxs-lookup"><span data-stu-id="3a7c8-138">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
