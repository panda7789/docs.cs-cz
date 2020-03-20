---
title: CorAttributeTargets – výčet
ms.date: 03/30/2017
api_name:
- CorAttributeTargets
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorAttributeTargets
helpviewer_keywords:
- CorAttributeTargets enumeration [.NET Framework metadata]
ms.assetid: 694c0fa0-7011-41a9-9dfd-f0e16ea574b5
topic_type:
- apiref
ms.openlocfilehash: 51741aa3a6d965c1e9743081628d8ad62e8fb04e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176198"
---
# <a name="corattributetargets-enumeration"></a><span data-ttu-id="3de0d-102">CorAttributeTargets – výčet</span><span class="sxs-lookup"><span data-stu-id="3de0d-102">CorAttributeTargets Enumeration</span></span>
<span data-ttu-id="3de0d-103">Určuje prvky aplikace, na kterých je platný použít atribut.</span><span class="sxs-lookup"><span data-stu-id="3de0d-103">Specifies the application elements on which it is valid to apply an attribute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3de0d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3de0d-104">Syntax</span></span>  
  
```cpp  
typedef enum CorAttributeTargets  
{  
    catAssembly            = 0x0001,  
    catModule              = 0x0002,  
    catClass               = 0x0004,  
    catStruct              = 0x0008,  
    catEnum                = 0x0010,  
    catConstructor         = 0x0020,  
    catMethod              = 0x0040,  
    catProperty            = 0x0080,  
    catField               = 0x0100,  
    catEvent               = 0x0200,  
    catInterface           = 0x0400,  
    catParameter           = 0x0800,  
    catDelegate            = 0x1000,  
    catGenericParameter    = 0x4000,  
  
    catAll                 =
        catAssembly | catModule | catClass | catStruct |
        catEnum | catConstructor | catMethod | catProperty |
        catField | catEvent | catInterface | catParameter |
        catDelegate | catGenericParameter,  
  
    catClassMembers        =
        catClass | catStruct | catEnum | catConstructor |
        catMethod | catProperty | catField | catEvent |
        catDelegate | catInterface  
  
} CorAttributeTargets;  
```  
  
## <a name="members"></a><span data-ttu-id="3de0d-105">Členové</span><span class="sxs-lookup"><span data-stu-id="3de0d-105">Members</span></span>  
  
|<span data-ttu-id="3de0d-106">Člen</span><span class="sxs-lookup"><span data-stu-id="3de0d-106">Member</span></span>|<span data-ttu-id="3de0d-107">Popis</span><span class="sxs-lookup"><span data-stu-id="3de0d-107">Description</span></span>|  
|------------|-----------------|  
|`catAssembly`|<span data-ttu-id="3de0d-108">Atribut lze použít pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="3de0d-108">Attribute can be applied to an assembly.</span></span>|  
|`catModule`|<span data-ttu-id="3de0d-109">Atribut lze použít u přenosného spustitelného souboru (.dll nebo .exe) modulu.</span><span class="sxs-lookup"><span data-stu-id="3de0d-109">Attribute can be applied to a portable executable (.dll or .exe) module.</span></span>|  
|`catClass`|<span data-ttu-id="3de0d-110">Atribut lze použít pro třídu.</span><span class="sxs-lookup"><span data-stu-id="3de0d-110">Attribute can be applied to a class.</span></span>|  
|`catStruct`|<span data-ttu-id="3de0d-111">Atribut lze použít na strukturu; to znamená typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="3de0d-111">Attribute can be applied to a structure; that is, a value type.</span></span>|  
|`catEnum`|<span data-ttu-id="3de0d-112">Atribut lze použít pro výčet.</span><span class="sxs-lookup"><span data-stu-id="3de0d-112">Attribute can be applied to an enumeration.</span></span>|  
|`catConstructor`|<span data-ttu-id="3de0d-113">Atribut lze použít na konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="3de0d-113">Attribute can be applied to a constructor.</span></span>|  
|`catMethod`|<span data-ttu-id="3de0d-114">Atribut lze použít na metodu.</span><span class="sxs-lookup"><span data-stu-id="3de0d-114">Attribute can be applied to a method.</span></span>|  
|`catProperty`|<span data-ttu-id="3de0d-115">Atribut lze použít na vlastnost.</span><span class="sxs-lookup"><span data-stu-id="3de0d-115">Attribute can be applied to a property.</span></span>|  
|`catField`|<span data-ttu-id="3de0d-116">Atribut lze použít pro pole.</span><span class="sxs-lookup"><span data-stu-id="3de0d-116">Attribute can be applied to a field.</span></span>|  
|`catEvent`|<span data-ttu-id="3de0d-117">Atribut lze použít na událost.</span><span class="sxs-lookup"><span data-stu-id="3de0d-117">Attribute can be applied to an event.</span></span>|  
|`catInterface`|<span data-ttu-id="3de0d-118">Atribut lze použít na rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3de0d-118">Attribute can be applied to an interface.</span></span>|  
|`catParameter`|<span data-ttu-id="3de0d-119">Atribut lze použít na parametr.</span><span class="sxs-lookup"><span data-stu-id="3de0d-119">Attribute can be applied to a parameter.</span></span>|  
|`catDelegate`|<span data-ttu-id="3de0d-120">Atribut lze použít pro delegáta.</span><span class="sxs-lookup"><span data-stu-id="3de0d-120">Attribute can be applied to a delegate.</span></span>|  
|`catGenericParameter`|<span data-ttu-id="3de0d-121">Atribut lze použít na obecný parametr.</span><span class="sxs-lookup"><span data-stu-id="3de0d-121">Attribute can be applied to a generic parameter.</span></span>|  
|`catAll`|<span data-ttu-id="3de0d-122">Atribut lze použít pro libovolný prvek aplikace.</span><span class="sxs-lookup"><span data-stu-id="3de0d-122">Attribute can be applied to any application element.</span></span>|  
|`catClassMembers`|<span data-ttu-id="3de0d-123">Atribut lze použít na člena třídy.</span><span class="sxs-lookup"><span data-stu-id="3de0d-123">Attribute can be applied to a member of a class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3de0d-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3de0d-124">Remarks</span></span>  
 <span data-ttu-id="3de0d-125">Hodnoty `CorAttributeTargets` výčtu lze kombinovat s bitovou operací OR, abyste získali upřednostňovanou kombinaci.</span><span class="sxs-lookup"><span data-stu-id="3de0d-125">The `CorAttributeTargets` enumeration values can be combined with a bitwise OR operation to get the preferred combination.</span></span>  
  
 <span data-ttu-id="3de0d-126">Paralely `CorAttributeTargets` spravované <xref:System.AttributeTargets?displayProperty=nameWithType> výčtu.</span><span class="sxs-lookup"><span data-stu-id="3de0d-126">The `CorAttributeTargets` parallels the managed <xref:System.AttributeTargets?displayProperty=nameWithType> enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3de0d-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3de0d-127">Requirements</span></span>  
 <span data-ttu-id="3de0d-128">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3de0d-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3de0d-129">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="3de0d-129">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="3de0d-130">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3de0d-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3de0d-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="3de0d-131">See also</span></span>

- [<span data-ttu-id="3de0d-132">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="3de0d-132">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
