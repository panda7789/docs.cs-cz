---
title: "CorAttributeTargets – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorAttributeTargets
api_location: mscoree.dll
api_type: COM
f1_keywords: CorAttributeTargets
helpviewer_keywords: CorAttributeTargets enumeration [.NET Framework metadata]
ms.assetid: 694c0fa0-7011-41a9-9dfd-f0e16ea574b5
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ce783c790eeb15c60d8e7699396755a560df7c9c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="corattributetargets-enumeration"></a><span data-ttu-id="4c577-102">CorAttributeTargets – výčet</span><span class="sxs-lookup"><span data-stu-id="4c577-102">CorAttributeTargets Enumeration</span></span>
<span data-ttu-id="4c577-103">Určuje prvky aplikace, na kterých je platná pro použití atributu.</span><span class="sxs-lookup"><span data-stu-id="4c577-103">Specifies the application elements on which it is valid to apply an attribute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c577-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4c577-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="4c577-105">Členové</span><span class="sxs-lookup"><span data-stu-id="4c577-105">Members</span></span>  
  
|<span data-ttu-id="4c577-106">Člen</span><span class="sxs-lookup"><span data-stu-id="4c577-106">Member</span></span>|<span data-ttu-id="4c577-107">Popis</span><span class="sxs-lookup"><span data-stu-id="4c577-107">Description</span></span>|  
|------------|-----------------|  
|`catAssembly`|<span data-ttu-id="4c577-108">Atribut lze použít k sestavení.</span><span class="sxs-lookup"><span data-stu-id="4c577-108">Attribute can be applied to an assembly.</span></span>|  
|`catModule`|<span data-ttu-id="4c577-109">Atribut lze použít k přenosné modulu spustitelný soubor (.exe nebo .dll).</span><span class="sxs-lookup"><span data-stu-id="4c577-109">Attribute can be applied to a portable executable (.dll or .exe) module.</span></span>|  
|`catClass`|<span data-ttu-id="4c577-110">Atribut lze použít na třídu.</span><span class="sxs-lookup"><span data-stu-id="4c577-110">Attribute can be applied to a class.</span></span>|  
|`catStruct`|<span data-ttu-id="4c577-111">Atribut lze použít pro strukturu; To znamená zadejte hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4c577-111">Attribute can be applied to a structure; that is, a value type.</span></span>|  
|`catEnum`|<span data-ttu-id="4c577-112">Atribut lze použít k výčtu.</span><span class="sxs-lookup"><span data-stu-id="4c577-112">Attribute can be applied to an enumeration.</span></span>|  
|`catConstructor`|<span data-ttu-id="4c577-113">Atribut lze použít k konstruktor.</span><span class="sxs-lookup"><span data-stu-id="4c577-113">Attribute can be applied to a constructor.</span></span>|  
|`catMethod`|<span data-ttu-id="4c577-114">Atribut může být použitý na metodu.</span><span class="sxs-lookup"><span data-stu-id="4c577-114">Attribute can be applied to a method.</span></span>|  
|`catProperty`|<span data-ttu-id="4c577-115">Atribut lze použít na vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4c577-115">Attribute can be applied to a property.</span></span>|  
|`catField`|<span data-ttu-id="4c577-116">Atribut lze použít pro pole.</span><span class="sxs-lookup"><span data-stu-id="4c577-116">Attribute can be applied to a field.</span></span>|  
|`catEvent`|<span data-ttu-id="4c577-117">Atribut lze použít k události.</span><span class="sxs-lookup"><span data-stu-id="4c577-117">Attribute can be applied to an event.</span></span>|  
|`catInterface`|<span data-ttu-id="4c577-118">Atribut lze použít k rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4c577-118">Attribute can be applied to an interface.</span></span>|  
|`catParameter`|<span data-ttu-id="4c577-119">Atribut lze použít na parametr.</span><span class="sxs-lookup"><span data-stu-id="4c577-119">Attribute can be applied to a parameter.</span></span>|  
|`catDelegate`|<span data-ttu-id="4c577-120">Atribut lze použít s delegátem.</span><span class="sxs-lookup"><span data-stu-id="4c577-120">Attribute can be applied to a delegate.</span></span>|  
|`catGenericParameter`|<span data-ttu-id="4c577-121">Atribut lze použít pro obecný parametr.</span><span class="sxs-lookup"><span data-stu-id="4c577-121">Attribute can be applied to a generic parameter.</span></span>|  
|`catAll`|<span data-ttu-id="4c577-122">Atribut lze použít pro libovolný element, aplikace.</span><span class="sxs-lookup"><span data-stu-id="4c577-122">Attribute can be applied to any application element.</span></span>|  
|`catClassMembers`|<span data-ttu-id="4c577-123">Atribut lze použít na člena třídy.</span><span class="sxs-lookup"><span data-stu-id="4c577-123">Attribute can be applied to a member of a class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c577-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4c577-124">Remarks</span></span>  
 <span data-ttu-id="4c577-125">`CorAttributeTargets` Hodnot výčtu mohou být kombinovány s bitové operace OR k získání upřednostňované kombinace.</span><span class="sxs-lookup"><span data-stu-id="4c577-125">The `CorAttributeTargets` enumeration values can be combined with a bitwise OR operation to get the preferred combination.</span></span>  
  
 <span data-ttu-id="4c577-126">`CorAttributeTargets` Je paralelní spravovaný <xref:System.AttributeTargets?displayProperty=nameWithType> výčtu.</span><span class="sxs-lookup"><span data-stu-id="4c577-126">The `CorAttributeTargets` parallels the managed <xref:System.AttributeTargets?displayProperty=nameWithType> enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c577-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4c577-127">Requirements</span></span>  
 <span data-ttu-id="4c577-128">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c577-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c577-129">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="4c577-129">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="4c577-130">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c577-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c577-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="4c577-131">See Also</span></span>  
 [<span data-ttu-id="4c577-132">Výčty metadat</span><span class="sxs-lookup"><span data-stu-id="4c577-132">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
