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
ms.openlocfilehash: f1836f26af99f91ab1765107573f6b067edd5e95
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007920"
---
# <a name="corattributetargets-enumeration"></a><span data-ttu-id="48e9a-102">CorAttributeTargets – výčet</span><span class="sxs-lookup"><span data-stu-id="48e9a-102">CorAttributeTargets Enumeration</span></span>
<span data-ttu-id="48e9a-103">Určuje prvky aplikace, na kterých je platný pro použití atributu.</span><span class="sxs-lookup"><span data-stu-id="48e9a-103">Specifies the application elements on which it is valid to apply an attribute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48e9a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="48e9a-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="48e9a-105">Členové</span><span class="sxs-lookup"><span data-stu-id="48e9a-105">Members</span></span>  
  
|<span data-ttu-id="48e9a-106">Člen</span><span class="sxs-lookup"><span data-stu-id="48e9a-106">Member</span></span>|<span data-ttu-id="48e9a-107">Description</span><span class="sxs-lookup"><span data-stu-id="48e9a-107">Description</span></span>|  
|------------|-----------------|  
|`catAssembly`|<span data-ttu-id="48e9a-108">Atribut lze použít pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="48e9a-108">Attribute can be applied to an assembly.</span></span>|  
|`catModule`|<span data-ttu-id="48e9a-109">Atribut lze použít pro přenos přenositelného spustitelného souboru (. dll nebo. exe).</span><span class="sxs-lookup"><span data-stu-id="48e9a-109">Attribute can be applied to a portable executable (.dll or .exe) module.</span></span>|  
|`catClass`|<span data-ttu-id="48e9a-110">Atribut lze použít pro třídu.</span><span class="sxs-lookup"><span data-stu-id="48e9a-110">Attribute can be applied to a class.</span></span>|  
|`catStruct`|<span data-ttu-id="48e9a-111">Atribut lze použít pro strukturu; To znamená typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="48e9a-111">Attribute can be applied to a structure; that is, a value type.</span></span>|  
|`catEnum`|<span data-ttu-id="48e9a-112">Atribut lze použít pro výčet.</span><span class="sxs-lookup"><span data-stu-id="48e9a-112">Attribute can be applied to an enumeration.</span></span>|  
|`catConstructor`|<span data-ttu-id="48e9a-113">Atribut lze použít pro konstruktor.</span><span class="sxs-lookup"><span data-stu-id="48e9a-113">Attribute can be applied to a constructor.</span></span>|  
|`catMethod`|<span data-ttu-id="48e9a-114">Atribut lze použít pro metodu.</span><span class="sxs-lookup"><span data-stu-id="48e9a-114">Attribute can be applied to a method.</span></span>|  
|`catProperty`|<span data-ttu-id="48e9a-115">Atribut lze použít pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="48e9a-115">Attribute can be applied to a property.</span></span>|  
|`catField`|<span data-ttu-id="48e9a-116">Atribut lze použít pro pole.</span><span class="sxs-lookup"><span data-stu-id="48e9a-116">Attribute can be applied to a field.</span></span>|  
|`catEvent`|<span data-ttu-id="48e9a-117">Atribut lze použít pro událost.</span><span class="sxs-lookup"><span data-stu-id="48e9a-117">Attribute can be applied to an event.</span></span>|  
|`catInterface`|<span data-ttu-id="48e9a-118">Atribut lze použít na rozhraní.</span><span class="sxs-lookup"><span data-stu-id="48e9a-118">Attribute can be applied to an interface.</span></span>|  
|`catParameter`|<span data-ttu-id="48e9a-119">Atribut lze použít pro parametr.</span><span class="sxs-lookup"><span data-stu-id="48e9a-119">Attribute can be applied to a parameter.</span></span>|  
|`catDelegate`|<span data-ttu-id="48e9a-120">Atribut lze použít pro delegáta.</span><span class="sxs-lookup"><span data-stu-id="48e9a-120">Attribute can be applied to a delegate.</span></span>|  
|`catGenericParameter`|<span data-ttu-id="48e9a-121">Atribut lze použít pro obecný parametr.</span><span class="sxs-lookup"><span data-stu-id="48e9a-121">Attribute can be applied to a generic parameter.</span></span>|  
|`catAll`|<span data-ttu-id="48e9a-122">Atribut lze použít pro libovolný element aplikace.</span><span class="sxs-lookup"><span data-stu-id="48e9a-122">Attribute can be applied to any application element.</span></span>|  
|`catClassMembers`|<span data-ttu-id="48e9a-123">Atribut lze použít pro člena třídy.</span><span class="sxs-lookup"><span data-stu-id="48e9a-123">Attribute can be applied to a member of a class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48e9a-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="48e9a-124">Remarks</span></span>  
 <span data-ttu-id="48e9a-125">`CorAttributeTargets`Hodnoty výčtu lze kombinovat s bitovým nebo operaci pro získání preferované kombinace.</span><span class="sxs-lookup"><span data-stu-id="48e9a-125">The `CorAttributeTargets` enumeration values can be combined with a bitwise OR operation to get the preferred combination.</span></span>  
  
 <span data-ttu-id="48e9a-126">`CorAttributeTargets`Paralelně spravuje <xref:System.AttributeTargets?displayProperty=nameWithType> výčet.</span><span class="sxs-lookup"><span data-stu-id="48e9a-126">The `CorAttributeTargets` parallels the managed <xref:System.AttributeTargets?displayProperty=nameWithType> enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48e9a-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="48e9a-127">Requirements</span></span>  
 <span data-ttu-id="48e9a-128">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48e9a-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48e9a-129">**Hlavička:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="48e9a-129">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="48e9a-130">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48e9a-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48e9a-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="48e9a-131">See also</span></span>

- [<span data-ttu-id="48e9a-132">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="48e9a-132">Metadata Enumerations</span></span>](metadata-enumerations.md)
