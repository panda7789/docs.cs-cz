---
title: CorMethodAttr – výčet
ms.date: 03/30/2017
api_name:
- CorMethodAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodAttr
helpviewer_keywords:
- CorMethodAttr enumeration [.NET Framework metadata]
ms.assetid: 4e0c3521-e54d-43c1-9857-cc76b49b8ffc
topic_type:
- apiref
ms.openlocfilehash: 779a8f88b7521aa4b0a75594552981b41714ee3f
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007673"
---
# <a name="cormethodattr-enumeration"></a><span data-ttu-id="06e22-102">CorMethodAttr – výčet</span><span class="sxs-lookup"><span data-stu-id="06e22-102">CorMethodAttr Enumeration</span></span>
<span data-ttu-id="06e22-103">Obsahuje hodnoty, které popisují funkce metody.</span><span class="sxs-lookup"><span data-stu-id="06e22-103">Contains values that describe the features of a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06e22-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="06e22-104">Syntax</span></span>  
  
```cpp  
typedef enum CorMethodAttr {  
  
    mdMemberAccessMask          =   0x0007,  
    mdPrivateScope              =   0x0000,  
    mdPrivate                   =   0x0001,  
    mdFamANDAssem               =   0x0002,  
    mdAssem                     =   0x0003,  
    mdFamily                    =   0x0004,  
    mdFamORAssem                =   0x0005,  
    mdPublic                    =   0x0006,  
  
    mdStatic                    =   0x0010,  
    mdFinal                     =   0x0020,  
    mdVirtual                   =   0x0040,  
    mdHideBySig                 =   0x0080,  
  
    mdVtableLayoutMask          =   0x0100,  
    mdReuseSlot                 =   0x0000,  
    mdNewSlot                   =   0x0100,  
  
    mdCheckAccessOnOverride     =   0x0200,  
    mdAbstract                  =   0x0400,  
    mdSpecialName               =   0x0800,  
  
    mdPinvokeImpl               =   0x2000,  
    mdUnmanagedExport           =   0x0008,  
  
    mdReservedMask              =   0xd000,  
    mdRTSpecialName             =   0x1000,  
    mdHasSecurity               =   0x4000,  
    mdRequireSecObject          =   0x8000,  
  
} CorMethodAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="06e22-105">Členové</span><span class="sxs-lookup"><span data-stu-id="06e22-105">Members</span></span>  
  
|<span data-ttu-id="06e22-106">Člen</span><span class="sxs-lookup"><span data-stu-id="06e22-106">Member</span></span>|<span data-ttu-id="06e22-107">Description</span><span class="sxs-lookup"><span data-stu-id="06e22-107">Description</span></span>|  
|------------|-----------------|  
|`mdMemberAccessMask`|<span data-ttu-id="06e22-108">Určuje přístup ke členu.</span><span class="sxs-lookup"><span data-stu-id="06e22-108">Specifies member access.</span></span>|  
|`mdPrivateScope`|<span data-ttu-id="06e22-109">Určuje, že na člena nelze odkazovat.</span><span class="sxs-lookup"><span data-stu-id="06e22-109">Specifies that the member cannot be referenced.</span></span>|  
|`mdPrivate`|<span data-ttu-id="06e22-110">Určuje, že člen je přístupný pouze nadřazenému typu.</span><span class="sxs-lookup"><span data-stu-id="06e22-110">Specifies that the member is accessible only by the parent type.</span></span>|  
|`mdFamANDAssem`|<span data-ttu-id="06e22-111">Určuje, že člen je přístupný podtypy pouze v tomto sestavení.</span><span class="sxs-lookup"><span data-stu-id="06e22-111">Specifies that the member is accessible by subtypes only in this assembly.</span></span>|  
|`mdAssem`|<span data-ttu-id="06e22-112">Určuje, že člen je accessibly kýmkoli v sestavení.</span><span class="sxs-lookup"><span data-stu-id="06e22-112">Specifies that the member is accessibly by anyone in the assembly.</span></span>|  
|`mdFamily`|<span data-ttu-id="06e22-113">Určuje, že člen je přístupný pouze pomocí typu a podtypů.</span><span class="sxs-lookup"><span data-stu-id="06e22-113">Specifies that the member is accessible only by type and subtypes.</span></span>|  
|`mdFamORAssem`|<span data-ttu-id="06e22-114">Určuje, že člen je přístupný odvozenými třídami a jinými typy v jeho sestavení.</span><span class="sxs-lookup"><span data-stu-id="06e22-114">Specifies that the member is accessible by derived classes and by other types in its assembly.</span></span>|  
|`mdPublic`|<span data-ttu-id="06e22-115">Určuje, že je člen přístupný pro všechny typy s přístupem k oboru.</span><span class="sxs-lookup"><span data-stu-id="06e22-115">Specifies that the member is accessible by all types with access to the scope.</span></span>|  
|`mdStatic`|<span data-ttu-id="06e22-116">Určuje, že je člen definován jako součást typu, nikoli jako člen instance.</span><span class="sxs-lookup"><span data-stu-id="06e22-116">Specifies that the member is defined as part of the type rather than as a member of an instance.</span></span>|  
|`mdFinal`|<span data-ttu-id="06e22-117">Určuje, že metodu nelze přepsat.</span><span class="sxs-lookup"><span data-stu-id="06e22-117">Specifies that the method cannot be overridden.</span></span>|  
|`mdVirtual`|<span data-ttu-id="06e22-118">Určuje, že metoda může být přepsána.</span><span class="sxs-lookup"><span data-stu-id="06e22-118">Specifies that the method can be overridden.</span></span>|  
|`mdHideBySig`|<span data-ttu-id="06e22-119">Určuje, že metoda bude skryta podle názvu a signatury, nikoli jenom podle názvu.</span><span class="sxs-lookup"><span data-stu-id="06e22-119">Specifies that the method hides by name and signature, rather than just by name.</span></span>|  
|`mdVtableLayoutMask`|<span data-ttu-id="06e22-120">Určuje rozložení virtuální tabulky.</span><span class="sxs-lookup"><span data-stu-id="06e22-120">Specifies virtual table layout.</span></span>|  
|`mdReuseSlot`|<span data-ttu-id="06e22-121">Určuje, že se má znovu použít slot používaný pro tuto metodu ve virtuální tabulce.</span><span class="sxs-lookup"><span data-stu-id="06e22-121">Specifies that the slot used for this method in the virtual table be reused.</span></span> <span data-ttu-id="06e22-122">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="06e22-122">This is the default.</span></span>|  
|`mdNewSlot`|<span data-ttu-id="06e22-123">Určuje, že metoda vždy získá novou pozici ve virtuální tabulce.</span><span class="sxs-lookup"><span data-stu-id="06e22-123">Specifies that the method always gets a new slot in the virtual table.</span></span>|  
|`mdCheckAccessOnOverride`|<span data-ttu-id="06e22-124">Určuje, že metodu lze přepsat stejnými typy, pro které jsou viditelné.</span><span class="sxs-lookup"><span data-stu-id="06e22-124">Specifies that the method can be overridden by the same types to which it is visible.</span></span>|  
|`mdAbstract`|<span data-ttu-id="06e22-125">Určuje, že metoda není implementována.</span><span class="sxs-lookup"><span data-stu-id="06e22-125">Specifies that the method is not implemented.</span></span>|  
|`mdSpecialName`|<span data-ttu-id="06e22-126">Určuje, že metoda je zvláštní a že její název popisuje, jak.</span><span class="sxs-lookup"><span data-stu-id="06e22-126">Specifies that the method is special, and that its name describes how.</span></span>|  
|`mdPinvokeImpl`|<span data-ttu-id="06e22-127">Určuje, že implementace metody je předána pomocí PInvoke.</span><span class="sxs-lookup"><span data-stu-id="06e22-127">Specifies that the method implementation is forwarded using PInvoke.</span></span>|  
|`mdUnmanagedExport`|<span data-ttu-id="06e22-128">Určuje, že metoda je spravovaná metoda exportovaná do nespravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="06e22-128">Specifies that the method is a managed method exported to unmanaged code.</span></span>|  
|`mdReservedMask`|<span data-ttu-id="06e22-129">Vyhrazeno pro interní použití modulem CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="06e22-129">Reserved for internal use by the common language runtime.</span></span>|  
|`mdRTSpecialName`|<span data-ttu-id="06e22-130">Určuje, že modul CLR (Common Language Runtime) by měl kontrolovat kódování názvu metody.</span><span class="sxs-lookup"><span data-stu-id="06e22-130">Specifies that the common language runtime should check the encoding of the method name.</span></span>|  
|`mdHasSecurity`|<span data-ttu-id="06e22-131">Určuje, že k metodě je přidruženo zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="06e22-131">Specifies that the method has security associated with it.</span></span>|  
|`mdRequireSecObject`|<span data-ttu-id="06e22-132">Určuje, že metoda volá jinou metodu obsahující bezpečnostní kód.</span><span class="sxs-lookup"><span data-stu-id="06e22-132">Specifies that the method calls another method containing security code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="06e22-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="06e22-133">Requirements</span></span>  
 <span data-ttu-id="06e22-134">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06e22-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06e22-135">**Hlavička:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="06e22-135">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="06e22-136">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06e22-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06e22-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="06e22-137">See also</span></span>

- [<span data-ttu-id="06e22-138">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="06e22-138">Metadata Enumerations</span></span>](metadata-enumerations.md)
