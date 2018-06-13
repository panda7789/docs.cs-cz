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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 54d239c3091b29424b26fbab4cb4eb9152ff9ad9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442163"
---
# <a name="corattributetargets-enumeration"></a><span data-ttu-id="75b80-102">CorAttributeTargets – výčet</span><span class="sxs-lookup"><span data-stu-id="75b80-102">CorAttributeTargets Enumeration</span></span>
<span data-ttu-id="75b80-103">Určuje prvky aplikace, na kterých je platná pro použití atributu.</span><span class="sxs-lookup"><span data-stu-id="75b80-103">Specifies the application elements on which it is valid to apply an attribute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75b80-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="75b80-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="75b80-105">Členové</span><span class="sxs-lookup"><span data-stu-id="75b80-105">Members</span></span>  
  
|<span data-ttu-id="75b80-106">Člen</span><span class="sxs-lookup"><span data-stu-id="75b80-106">Member</span></span>|<span data-ttu-id="75b80-107">Popis</span><span class="sxs-lookup"><span data-stu-id="75b80-107">Description</span></span>|  
|------------|-----------------|  
|`catAssembly`|<span data-ttu-id="75b80-108">Atribut lze použít k sestavení.</span><span class="sxs-lookup"><span data-stu-id="75b80-108">Attribute can be applied to an assembly.</span></span>|  
|`catModule`|<span data-ttu-id="75b80-109">Atribut lze použít k přenosné modulu spustitelný soubor (.exe nebo .dll).</span><span class="sxs-lookup"><span data-stu-id="75b80-109">Attribute can be applied to a portable executable (.dll or .exe) module.</span></span>|  
|`catClass`|<span data-ttu-id="75b80-110">Atribut lze použít na třídu.</span><span class="sxs-lookup"><span data-stu-id="75b80-110">Attribute can be applied to a class.</span></span>|  
|`catStruct`|<span data-ttu-id="75b80-111">Atribut lze použít pro strukturu; To znamená zadejte hodnotu.</span><span class="sxs-lookup"><span data-stu-id="75b80-111">Attribute can be applied to a structure; that is, a value type.</span></span>|  
|`catEnum`|<span data-ttu-id="75b80-112">Atribut lze použít k výčtu.</span><span class="sxs-lookup"><span data-stu-id="75b80-112">Attribute can be applied to an enumeration.</span></span>|  
|`catConstructor`|<span data-ttu-id="75b80-113">Atribut lze použít k konstruktor.</span><span class="sxs-lookup"><span data-stu-id="75b80-113">Attribute can be applied to a constructor.</span></span>|  
|`catMethod`|<span data-ttu-id="75b80-114">Atribut může být použitý na metodu.</span><span class="sxs-lookup"><span data-stu-id="75b80-114">Attribute can be applied to a method.</span></span>|  
|`catProperty`|<span data-ttu-id="75b80-115">Atribut lze použít na vlastnost.</span><span class="sxs-lookup"><span data-stu-id="75b80-115">Attribute can be applied to a property.</span></span>|  
|`catField`|<span data-ttu-id="75b80-116">Atribut lze použít pro pole.</span><span class="sxs-lookup"><span data-stu-id="75b80-116">Attribute can be applied to a field.</span></span>|  
|`catEvent`|<span data-ttu-id="75b80-117">Atribut lze použít k události.</span><span class="sxs-lookup"><span data-stu-id="75b80-117">Attribute can be applied to an event.</span></span>|  
|`catInterface`|<span data-ttu-id="75b80-118">Atribut lze použít k rozhraní.</span><span class="sxs-lookup"><span data-stu-id="75b80-118">Attribute can be applied to an interface.</span></span>|  
|`catParameter`|<span data-ttu-id="75b80-119">Atribut lze použít na parametr.</span><span class="sxs-lookup"><span data-stu-id="75b80-119">Attribute can be applied to a parameter.</span></span>|  
|`catDelegate`|<span data-ttu-id="75b80-120">Atribut lze použít s delegátem.</span><span class="sxs-lookup"><span data-stu-id="75b80-120">Attribute can be applied to a delegate.</span></span>|  
|`catGenericParameter`|<span data-ttu-id="75b80-121">Atribut lze použít pro obecný parametr.</span><span class="sxs-lookup"><span data-stu-id="75b80-121">Attribute can be applied to a generic parameter.</span></span>|  
|`catAll`|<span data-ttu-id="75b80-122">Atribut lze použít pro libovolný element, aplikace.</span><span class="sxs-lookup"><span data-stu-id="75b80-122">Attribute can be applied to any application element.</span></span>|  
|`catClassMembers`|<span data-ttu-id="75b80-123">Atribut lze použít na člena třídy.</span><span class="sxs-lookup"><span data-stu-id="75b80-123">Attribute can be applied to a member of a class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75b80-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="75b80-124">Remarks</span></span>  
 <span data-ttu-id="75b80-125">`CorAttributeTargets` Hodnot výčtu mohou být kombinovány s bitové operace OR k získání upřednostňované kombinace.</span><span class="sxs-lookup"><span data-stu-id="75b80-125">The `CorAttributeTargets` enumeration values can be combined with a bitwise OR operation to get the preferred combination.</span></span>  
  
 <span data-ttu-id="75b80-126">`CorAttributeTargets` Je paralelní spravovaný <xref:System.AttributeTargets?displayProperty=nameWithType> výčtu.</span><span class="sxs-lookup"><span data-stu-id="75b80-126">The `CorAttributeTargets` parallels the managed <xref:System.AttributeTargets?displayProperty=nameWithType> enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75b80-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="75b80-127">Requirements</span></span>  
 <span data-ttu-id="75b80-128">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75b80-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75b80-129">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="75b80-129">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="75b80-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75b80-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75b80-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="75b80-131">See Also</span></span>  
 [<span data-ttu-id="75b80-132">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="75b80-132">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
