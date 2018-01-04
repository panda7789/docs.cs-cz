---
title: "CorDeclSecurity – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDeclSecurity
api_location: mscoree.dll
api_type: COM
f1_keywords: CorDeclSecurity
helpviewer_keywords: CorDeclSecurity enumeration [.NET Framework metadata]
ms.assetid: 864f1267-d267-4696-8df7-1f83f8444d6f
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 30fd7ca2cf7962c6cadb43d4d8e3031b59292463
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="cordeclsecurity-enumeration"></a><span data-ttu-id="b610b-102">CorDeclSecurity – výčet</span><span class="sxs-lookup"><span data-stu-id="b610b-102">CorDeclSecurity Enumeration</span></span>
<span data-ttu-id="b610b-103">Určuje akce zabezpečení, které je možné provést pomocí deklarativních zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="b610b-103">Specifies the security actions that can be performed using declarative security.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b610b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b610b-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="b610b-105">Členové</span><span class="sxs-lookup"><span data-stu-id="b610b-105">Members</span></span>  
  
|<span data-ttu-id="b610b-106">Člen</span><span class="sxs-lookup"><span data-stu-id="b610b-106">Member</span></span>|<span data-ttu-id="b610b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b610b-107">Description</span></span>|  
|------------|-----------------|  
|`dclActionMask`|<span data-ttu-id="b610b-108">Vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="b610b-108">Reserved.</span></span>|  
|`dclActionNil`|<span data-ttu-id="b610b-109">Vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="b610b-109">Reserved.</span></span>|  
|`dclRequest`|<span data-ttu-id="b610b-110">Vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="b610b-110">Reserved.</span></span>|  
|`dclDemand`|<span data-ttu-id="b610b-111">Všechny volající vyšší v zásobníku volání je potřeba bylo uděleno oprávnění určeného aktuálního objektu oprávnění.</span><span class="sxs-lookup"><span data-stu-id="b610b-111">All callers higher in the call stack are required to have been granted the permission specified by the current permission object.</span></span>|  
|`dclAssert`|<span data-ttu-id="b610b-112">Volání kódu přístup i v případě, že volající vyšší v zásobníku nebylo uděleno oprávnění pro přístup k prostředku v prostředku označeném identifikátorem aktuálního objektu oprávnění</span><span class="sxs-lookup"><span data-stu-id="b610b-112">The calling code can access the resource identified by the current permission object, even if callers higher in the stack have not been granted permission to access the resource</span></span>|  
|`dclDeny`|<span data-ttu-id="b610b-113">Umožňuje přístup k prostředku zadaného parametrem aktuální oprávnění objektu je odepřen volající, i v případě, že bylo uděleno oprávnění k přístupu.</span><span class="sxs-lookup"><span data-stu-id="b610b-113">The ability to access the resource specified by the current permission object is denied to callers, even if they have been granted permission to access it.</span></span>|  
|`dclPermitOnly`|<span data-ttu-id="b610b-114">Pouze prostředky určeného objektu toto oprávnění lze přistupovat, i v případě, že kód byla udělena oprávnění k přístupu k dalším prostředkům.</span><span class="sxs-lookup"><span data-stu-id="b610b-114">Only the resources specified by this permission object can be accessed, even if the code has been granted permission to access other resources.</span></span>|  
|`dclLinktimeCheck`|<span data-ttu-id="b610b-115">Je potřeba mít nebylo uděleno oprávnění k zadané pro dané časové období bezprostředního volajícího.</span><span class="sxs-lookup"><span data-stu-id="b610b-115">The immediate caller is required to have been granted the specified permission for a given period of time.</span></span>|  
|`dclInheritanceCheck`|<span data-ttu-id="b610b-116">Odvozené třídy dědí jiné třídy nebo přepsání metody je potřeba mít nebylo uděleno oprávnění k zadané.</span><span class="sxs-lookup"><span data-stu-id="b610b-116">The derived class inheriting another class or overriding a method is required to have been granted the specified permission.</span></span>|  
|`dclRequestMinimum`|<span data-ttu-id="b610b-117">Volající můžete žádost o minimální oprávnění potřebná pro spuštění kódu.</span><span class="sxs-lookup"><span data-stu-id="b610b-117">The caller can request for the minimum permissions required for code to run.</span></span> <span data-ttu-id="b610b-118">Tuto akci lze použít pouze v rámci oboru sestavení.</span><span class="sxs-lookup"><span data-stu-id="b610b-118">This action can only be used within the scope of the assembly.</span></span>|  
|`dclRequestOptional`|<span data-ttu-id="b610b-119">Volající může požádat o další oprávnění, které jsou volitelné (není požadováno ke spuštění).</span><span class="sxs-lookup"><span data-stu-id="b610b-119">The caller can request for additional permissions that are optional (not required to run).</span></span> <span data-ttu-id="b610b-120">Tento požadavek implicitně odmítá další oprávnění, které nejsou výslovně požadována.</span><span class="sxs-lookup"><span data-stu-id="b610b-120">This request implicitly refuses all other permissions not specifically requested.</span></span> <span data-ttu-id="b610b-121">Tuto akci lze použít pouze v rámci oboru sestavení.</span><span class="sxs-lookup"><span data-stu-id="b610b-121">This action can only be used within the scope of the assembly.</span></span>|  
|`dclRequestRefuse`|<span data-ttu-id="b610b-122">Neposkytuje volajícího žádost o oprávnění, která může došlo ke zneužití.</span><span class="sxs-lookup"><span data-stu-id="b610b-122">The caller's request for permissions that might be misused will not be granted.</span></span> <span data-ttu-id="b610b-123">Tuto akci lze použít pouze v rámci oboru sestavení.</span><span class="sxs-lookup"><span data-stu-id="b610b-123">This action can only be used within the scope of the assembly.</span></span>|  
|`dclPrejitGrant`|<span data-ttu-id="b610b-124">Vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="b610b-124">Reserved.</span></span>|  
|`dclPrejitDenied`|<span data-ttu-id="b610b-125">Vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="b610b-125">Reserved.</span></span>|  
|`dclNonCasDemand`|<span data-ttu-id="b610b-126">Vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="b610b-126">Reserved.</span></span>|  
|`dclNonCasLinkDemand`|<span data-ttu-id="b610b-127">Je potřeba mít nebylo uděleno oprávnění k zadané bezprostředního volajícího.</span><span class="sxs-lookup"><span data-stu-id="b610b-127">The immediate caller is required to have been granted the specified permission.</span></span>|  
|`dclNonCasInheritance`|<span data-ttu-id="b610b-128">Vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="b610b-128">Reserved.</span></span>|  
|`dclLinkDemandChoice`|<span data-ttu-id="b610b-129">Vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="b610b-129">Reserved.</span></span>|  
|`dclInheritanceDemandChoice`|<span data-ttu-id="b610b-130">Vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="b610b-130">Reserved.</span></span>|  
|`dclDemandChoice`|<span data-ttu-id="b610b-131">Vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="b610b-131">Reserved.</span></span>|  
|`dclMaximumValue`|<span data-ttu-id="b610b-132">Vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="b610b-132">Reserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b610b-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b610b-133">Requirements</span></span>  
 <span data-ttu-id="b610b-134">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b610b-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b610b-135">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="b610b-135">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="b610b-136">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b610b-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b610b-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="b610b-137">See Also</span></span>  
 [<span data-ttu-id="b610b-138">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="b610b-138">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
