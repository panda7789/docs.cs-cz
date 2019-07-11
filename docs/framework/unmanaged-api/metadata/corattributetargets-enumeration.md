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
ms.openlocfilehash: 9fb1dff80fccc920540d370797441b3a019d766c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780913"
---
# <a name="corattributetargets-enumeration"></a><span data-ttu-id="eb711-102">CorAttributeTargets – výčet</span><span class="sxs-lookup"><span data-stu-id="eb711-102">CorAttributeTargets Enumeration</span></span>
<span data-ttu-id="eb711-103">Určuje prvky aplikace, na kterých je platný pro použití atributu.</span><span class="sxs-lookup"><span data-stu-id="eb711-103">Specifies the application elements on which it is valid to apply an attribute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb711-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eb711-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="eb711-105">Členové</span><span class="sxs-lookup"><span data-stu-id="eb711-105">Members</span></span>  
  
|<span data-ttu-id="eb711-106">Člen</span><span class="sxs-lookup"><span data-stu-id="eb711-106">Member</span></span>|<span data-ttu-id="eb711-107">Popis</span><span class="sxs-lookup"><span data-stu-id="eb711-107">Description</span></span>|  
|------------|-----------------|  
|`catAssembly`|<span data-ttu-id="eb711-108">Atribut lze použít k sestavení.</span><span class="sxs-lookup"><span data-stu-id="eb711-108">Attribute can be applied to an assembly.</span></span>|  
|`catModule`|<span data-ttu-id="eb711-109">Atribut lze použít pro přenosný spustitelný soubor modulu (.dll nebo .exe).</span><span class="sxs-lookup"><span data-stu-id="eb711-109">Attribute can be applied to a portable executable (.dll or .exe) module.</span></span>|  
|`catClass`|<span data-ttu-id="eb711-110">Atribut lze použít na třídu.</span><span class="sxs-lookup"><span data-stu-id="eb711-110">Attribute can be applied to a class.</span></span>|  
|`catStruct`|<span data-ttu-id="eb711-111">Atribut lze použít pro struktury; To znamená zadejte hodnotu.</span><span class="sxs-lookup"><span data-stu-id="eb711-111">Attribute can be applied to a structure; that is, a value type.</span></span>|  
|`catEnum`|<span data-ttu-id="eb711-112">Atribut lze použít pro výčet.</span><span class="sxs-lookup"><span data-stu-id="eb711-112">Attribute can be applied to an enumeration.</span></span>|  
|`catConstructor`|<span data-ttu-id="eb711-113">Atribut lze použít pro konstruktor.</span><span class="sxs-lookup"><span data-stu-id="eb711-113">Attribute can be applied to a constructor.</span></span>|  
|`catMethod`|<span data-ttu-id="eb711-114">Atribut lze použít pro metodu.</span><span class="sxs-lookup"><span data-stu-id="eb711-114">Attribute can be applied to a method.</span></span>|  
|`catProperty`|<span data-ttu-id="eb711-115">Atribut lze použít pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="eb711-115">Attribute can be applied to a property.</span></span>|  
|`catField`|<span data-ttu-id="eb711-116">Atribut lze použít pro pole.</span><span class="sxs-lookup"><span data-stu-id="eb711-116">Attribute can be applied to a field.</span></span>|  
|`catEvent`|<span data-ttu-id="eb711-117">Atribut lze použít k události.</span><span class="sxs-lookup"><span data-stu-id="eb711-117">Attribute can be applied to an event.</span></span>|  
|`catInterface`|<span data-ttu-id="eb711-118">Atribut lze použít pro rozhraní.</span><span class="sxs-lookup"><span data-stu-id="eb711-118">Attribute can be applied to an interface.</span></span>|  
|`catParameter`|<span data-ttu-id="eb711-119">Atribut lze použít pro parametr.</span><span class="sxs-lookup"><span data-stu-id="eb711-119">Attribute can be applied to a parameter.</span></span>|  
|`catDelegate`|<span data-ttu-id="eb711-120">Atribut lze použít pro delegáta.</span><span class="sxs-lookup"><span data-stu-id="eb711-120">Attribute can be applied to a delegate.</span></span>|  
|`catGenericParameter`|<span data-ttu-id="eb711-121">Atribut lze použít pro obecný parametr.</span><span class="sxs-lookup"><span data-stu-id="eb711-121">Attribute can be applied to a generic parameter.</span></span>|  
|`catAll`|<span data-ttu-id="eb711-122">Atribut lze použít k libovolnému aplikaci prvku.</span><span class="sxs-lookup"><span data-stu-id="eb711-122">Attribute can be applied to any application element.</span></span>|  
|`catClassMembers`|<span data-ttu-id="eb711-123">Atribut lze použít pro člen třídy.</span><span class="sxs-lookup"><span data-stu-id="eb711-123">Attribute can be applied to a member of a class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb711-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eb711-124">Remarks</span></span>  
 <span data-ttu-id="eb711-125">`CorAttributeTargets` Hodnoty výčtu lze kombinovat s bitová operace OR zobrazíte upřednostňované kombinaci.</span><span class="sxs-lookup"><span data-stu-id="eb711-125">The `CorAttributeTargets` enumeration values can be combined with a bitwise OR operation to get the preferred combination.</span></span>  
  
 <span data-ttu-id="eb711-126">`CorAttributeTargets` Parallels spravovanou <xref:System.AttributeTargets?displayProperty=nameWithType> výčtu.</span><span class="sxs-lookup"><span data-stu-id="eb711-126">The `CorAttributeTargets` parallels the managed <xref:System.AttributeTargets?displayProperty=nameWithType> enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb711-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eb711-127">Requirements</span></span>  
 <span data-ttu-id="eb711-128">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb711-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb711-129">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="eb711-129">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="eb711-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb711-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb711-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eb711-131">See also</span></span>

- [<span data-ttu-id="eb711-132">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="eb711-132">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
