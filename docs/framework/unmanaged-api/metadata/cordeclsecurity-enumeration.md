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
ms.openlocfilehash: ffbc9a10ff48b3dfd59b95c0f6b9ecab80b6a49c
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007881"
---
# <a name="cordeclsecurity-enumeration"></a><span data-ttu-id="c9c4c-102">CorDeclSecurity – výčet</span><span class="sxs-lookup"><span data-stu-id="c9c4c-102">CorDeclSecurity Enumeration</span></span>
<span data-ttu-id="c9c4c-103">Určuje bezpečnostní akce, které lze provést pomocí deklarativního zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c9c4c-103">Specifies the security actions that can be performed using declarative security.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9c4c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9c4c-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="c9c4c-105">Členové</span><span class="sxs-lookup"><span data-stu-id="c9c4c-105">Members</span></span>  
  
|<span data-ttu-id="c9c4c-106">Člen</span><span class="sxs-lookup"><span data-stu-id="c9c4c-106">Member</span></span>|<span data-ttu-id="c9c4c-107">Description</span><span class="sxs-lookup"><span data-stu-id="c9c4c-107">Description</span></span>|  
|------------|-----------------|  
|`dclActionMask`|<span data-ttu-id="c9c4c-108">Vyhrazeno.</span><span class="sxs-lookup"><span data-stu-id="c9c4c-108">Reserved.</span></span>|  
|`dclActionNil`|<span data-ttu-id="c9c4c-109">Vyhrazeno.</span><span class="sxs-lookup"><span data-stu-id="c9c4c-109">Reserved.</span></span>|  
|`dclRequest`|<span data-ttu-id="c9c4c-110">Vyhrazeno.</span><span class="sxs-lookup"><span data-stu-id="c9c4c-110">Reserved.</span></span>|  
|`dclDemand`|<span data-ttu-id="c9c4c-111">Všem volajícím vyšším v zásobníku volání je nutné udělit oprávnění určené aktuálním objektem oprávnění.</span><span class="sxs-lookup"><span data-stu-id="c9c4c-111">All callers higher in the call stack are required to have been granted the permission specified by the current permission object.</span></span>|  
|`dclAssert`|<span data-ttu-id="c9c4c-112">Volající kód může přistupovat k prostředku identifikovanému aktuálním objektem oprávnění, a to i v případě, že by volajícím vyšším v zásobníku nebylo uděleno oprávnění pro přístup k prostředku.</span><span class="sxs-lookup"><span data-stu-id="c9c4c-112">The calling code can access the resource identified by the current permission object, even if callers higher in the stack have not been granted permission to access the resource</span></span>|  
|`dclDeny`|<span data-ttu-id="c9c4c-113">Možnost přístupu k prostředku určenému aktuálním objektem oprávnění je odepřena volajícím, i když jim byla udělena oprávnění k přístupu.</span><span class="sxs-lookup"><span data-stu-id="c9c4c-113">The ability to access the resource specified by the current permission object is denied to callers, even if they have been granted permission to access it.</span></span>|  
|`dclPermitOnly`|<span data-ttu-id="c9c4c-114">Přístup k prostředkům, které jsou určené tímto objektem oprávnění, lze získat i v případě, že byl kódu uděleno oprávnění k přístupu k jiným prostředkům.</span><span class="sxs-lookup"><span data-stu-id="c9c4c-114">Only the resources specified by this permission object can be accessed, even if the code has been granted permission to access other resources.</span></span>|  
|`dclLinktimeCheck`|<span data-ttu-id="c9c4c-115">Okamžitému volajícímu se musí udělit zadané oprávnění pro dané časové období.</span><span class="sxs-lookup"><span data-stu-id="c9c4c-115">The immediate caller is required to have been granted the specified permission for a given period of time.</span></span>|  
|`dclInheritanceCheck`|<span data-ttu-id="c9c4c-116">Odvozená třída, která dědí jinou třídu nebo k přepsání metody, je vyžadována pro udělení zadaného oprávnění.</span><span class="sxs-lookup"><span data-stu-id="c9c4c-116">The derived class inheriting another class or overriding a method is required to have been granted the specified permission.</span></span>|  
|`dclRequestMinimum`|<span data-ttu-id="c9c4c-117">Volající může požadovat minimální oprávnění, která jsou požadována ke spuštění kódu.</span><span class="sxs-lookup"><span data-stu-id="c9c4c-117">The caller can request for the minimum permissions required for code to run.</span></span> <span data-ttu-id="c9c4c-118">Tuto akci lze použít pouze v rámci oboru sestavení.</span><span class="sxs-lookup"><span data-stu-id="c9c4c-118">This action can only be used within the scope of the assembly.</span></span>|  
|`dclRequestOptional`|<span data-ttu-id="c9c4c-119">Volající může požádat o další oprávnění, která jsou volitelná (nevyžadují se ke spuštění).</span><span class="sxs-lookup"><span data-stu-id="c9c4c-119">The caller can request for additional permissions that are optional (not required to run).</span></span> <span data-ttu-id="c9c4c-120">Tento požadavek implicitně odmítne všechna ostatní oprávnění, která nejsou výslovně požadována.</span><span class="sxs-lookup"><span data-stu-id="c9c4c-120">This request implicitly refuses all other permissions not specifically requested.</span></span> <span data-ttu-id="c9c4c-121">Tuto akci lze použít pouze v rámci oboru sestavení.</span><span class="sxs-lookup"><span data-stu-id="c9c4c-121">This action can only be used within the scope of the assembly.</span></span>|  
|`dclRequestRefuse`|<span data-ttu-id="c9c4c-122">Žádost volajícího o oprávnění, která by mohla být nepoužitá, nebude udělena.</span><span class="sxs-lookup"><span data-stu-id="c9c4c-122">The caller's request for permissions that might be misused will not be granted.</span></span> <span data-ttu-id="c9c4c-123">Tuto akci lze použít pouze v rámci oboru sestavení.</span><span class="sxs-lookup"><span data-stu-id="c9c4c-123">This action can only be used within the scope of the assembly.</span></span>|  
|`dclPrejitGrant`|<span data-ttu-id="c9c4c-124">Vyhrazeno.</span><span class="sxs-lookup"><span data-stu-id="c9c4c-124">Reserved.</span></span>|  
|`dclPrejitDenied`|<span data-ttu-id="c9c4c-125">Vyhrazeno.</span><span class="sxs-lookup"><span data-stu-id="c9c4c-125">Reserved.</span></span>|  
|`dclNonCasDemand`|<span data-ttu-id="c9c4c-126">Vyhrazeno.</span><span class="sxs-lookup"><span data-stu-id="c9c4c-126">Reserved.</span></span>|  
|`dclNonCasLinkDemand`|<span data-ttu-id="c9c4c-127">K tomuto okamžitému volajícímu se musí udělit zadané oprávnění.</span><span class="sxs-lookup"><span data-stu-id="c9c4c-127">The immediate caller is required to have been granted the specified permission.</span></span>|  
|`dclNonCasInheritance`|<span data-ttu-id="c9c4c-128">Vyhrazeno.</span><span class="sxs-lookup"><span data-stu-id="c9c4c-128">Reserved.</span></span>|  
|`dclLinkDemandChoice`|<span data-ttu-id="c9c4c-129">Vyhrazeno.</span><span class="sxs-lookup"><span data-stu-id="c9c4c-129">Reserved.</span></span>|  
|`dclInheritanceDemandChoice`|<span data-ttu-id="c9c4c-130">Vyhrazeno.</span><span class="sxs-lookup"><span data-stu-id="c9c4c-130">Reserved.</span></span>|  
|`dclDemandChoice`|<span data-ttu-id="c9c4c-131">Vyhrazeno.</span><span class="sxs-lookup"><span data-stu-id="c9c4c-131">Reserved.</span></span>|  
|`dclMaximumValue`|<span data-ttu-id="c9c4c-132">Vyhrazeno.</span><span class="sxs-lookup"><span data-stu-id="c9c4c-132">Reserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c9c4c-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c9c4c-133">Requirements</span></span>  
 <span data-ttu-id="c9c4c-134">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9c4c-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9c4c-135">**Hlavička:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="c9c4c-135">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="c9c4c-136">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9c4c-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9c4c-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="c9c4c-137">See also</span></span>

- [<span data-ttu-id="c9c4c-138">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="c9c4c-138">Metadata Enumerations</span></span>](metadata-enumerations.md)
