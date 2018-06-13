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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8f144426996583d5058f70daed99d8a37cfb6bfb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444663"
---
# <a name="cormethodattr-enumeration"></a><span data-ttu-id="21e59-102">CorMethodAttr – výčet</span><span class="sxs-lookup"><span data-stu-id="21e59-102">CorMethodAttr Enumeration</span></span>
<span data-ttu-id="21e59-103">Obsahuje hodnoty, které popisují funkce metody.</span><span class="sxs-lookup"><span data-stu-id="21e59-103">Contains values that describe the features of a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21e59-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21e59-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="21e59-105">Členové</span><span class="sxs-lookup"><span data-stu-id="21e59-105">Members</span></span>  
  
|<span data-ttu-id="21e59-106">Člen</span><span class="sxs-lookup"><span data-stu-id="21e59-106">Member</span></span>|<span data-ttu-id="21e59-107">Popis</span><span class="sxs-lookup"><span data-stu-id="21e59-107">Description</span></span>|  
|------------|-----------------|  
|`mdMemberAccessMask`|<span data-ttu-id="21e59-108">Určuje přístup ke členu.</span><span class="sxs-lookup"><span data-stu-id="21e59-108">Specifies member access.</span></span>|  
|`mdPrivateScope`|<span data-ttu-id="21e59-109">Určuje, že člena nelze odkazovat.</span><span class="sxs-lookup"><span data-stu-id="21e59-109">Specifies that the member cannot be referenced.</span></span>|  
|`mdPrivate`|<span data-ttu-id="21e59-110">Určuje, že je přístupná jenom pro nadřazený typ člena.</span><span class="sxs-lookup"><span data-stu-id="21e59-110">Specifies that the member is accessible only by the parent type.</span></span>|  
|`mdFamANDAssem`|<span data-ttu-id="21e59-111">Určuje, že je člen přístupný podtypů pouze v tomto sestavení.</span><span class="sxs-lookup"><span data-stu-id="21e59-111">Specifies that the member is accessible by subtypes only in this assembly.</span></span>|  
|`mdAssem`|<span data-ttu-id="21e59-112">Určuje, že je člen v accessibly každému uživateli v sestavení.</span><span class="sxs-lookup"><span data-stu-id="21e59-112">Specifies that the member is accessibly by anyone in the assembly.</span></span>|  
|`mdFamily`|<span data-ttu-id="21e59-113">Určuje, že je dostupný pouze podle typu a podtypů člena.</span><span class="sxs-lookup"><span data-stu-id="21e59-113">Specifies that the member is accessible only by type and subtypes.</span></span>|  
|`mdFamORAssem`|<span data-ttu-id="21e59-114">Určuje, že je člen přístupný odvozené třídy a dalších typů v jeho sestavení.</span><span class="sxs-lookup"><span data-stu-id="21e59-114">Specifies that the member is accessible by derived classes and by other types in its assembly.</span></span>|  
|`mdPublic`|<span data-ttu-id="21e59-115">Určuje, že je člen přístupné všechny typy s přístupem k oboru.</span><span class="sxs-lookup"><span data-stu-id="21e59-115">Specifies that the member is accessible by all types with access to the scope.</span></span>|  
|`mdStatic`|<span data-ttu-id="21e59-116">Určuje, zda člen je definován v rámci typu, nikoli jako člen instance.</span><span class="sxs-lookup"><span data-stu-id="21e59-116">Specifies that the member is defined as part of the type rather than as a member of an instance.</span></span>|  
|`mdFinal`|<span data-ttu-id="21e59-117">Určuje, že metoda nelze přepsat.</span><span class="sxs-lookup"><span data-stu-id="21e59-117">Specifies that the method cannot be overridden.</span></span>|  
|`mdVirtual`|<span data-ttu-id="21e59-118">Určuje, zda lze přepsat metodu.</span><span class="sxs-lookup"><span data-stu-id="21e59-118">Specifies that the method can be overridden.</span></span>|  
|`mdHideBySig`|<span data-ttu-id="21e59-119">Určuje, že metoda skryje podle názvu a podpis, nikoli jen název.</span><span class="sxs-lookup"><span data-stu-id="21e59-119">Specifies that the method hides by name and signature, rather than just by name.</span></span>|  
|`mdVtableLayoutMask`|<span data-ttu-id="21e59-120">Určuje rozložení virtuální tabulky.</span><span class="sxs-lookup"><span data-stu-id="21e59-120">Specifies virtual table layout.</span></span>|  
|`mdReuseSlot`|<span data-ttu-id="21e59-121">Určuje, že slotu použít pro tuto metodu v tabulce virtuální znovu použít.</span><span class="sxs-lookup"><span data-stu-id="21e59-121">Specifies that the slot used for this method in the virtual table be reused.</span></span> <span data-ttu-id="21e59-122">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="21e59-122">This is the default.</span></span>|  
|`mdNewSlot`|<span data-ttu-id="21e59-123">Určuje, že metoda vždy získá nový slot v tabulce virtuálních.</span><span class="sxs-lookup"><span data-stu-id="21e59-123">Specifies that the method always gets a new slot in the virtual table.</span></span>|  
|`mdCheckAccessOnOverride`|<span data-ttu-id="21e59-124">Určuje, že metoda se dá přepsat stejné typy, pro které je viditelná.</span><span class="sxs-lookup"><span data-stu-id="21e59-124">Specifies that the method can be overridden by the same types to which it is visible.</span></span>|  
|`mdAbstract`|<span data-ttu-id="21e59-125">Určuje, že metoda není implementována.</span><span class="sxs-lookup"><span data-stu-id="21e59-125">Specifies that the method is not implemented.</span></span>|  
|`mdSpecialName`|<span data-ttu-id="21e59-126">Určuje, že metoda je speciální a že její název popisuje jak.</span><span class="sxs-lookup"><span data-stu-id="21e59-126">Specifies that the method is special, and that its name describes how.</span></span>|  
|`mdPinvokeImpl`|<span data-ttu-id="21e59-127">Určuje, že metoda implementace je dál pomocí služby PInvoke.</span><span class="sxs-lookup"><span data-stu-id="21e59-127">Specifies that the method implementation is forwarded using PInvoke.</span></span>|  
|`mdUnmanagedExport`|<span data-ttu-id="21e59-128">Určuje, že metoda je spravovaný metoda exportovat na nespravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="21e59-128">Specifies that the method is a managed method exported to unmanaged code.</span></span>|  
|`mdReservedMask`|<span data-ttu-id="21e59-129">Modul common language runtime vyhrazené pro interní použití.</span><span class="sxs-lookup"><span data-stu-id="21e59-129">Reserved for internal use by the common language runtime.</span></span>|  
|`mdRTSpecialName`|<span data-ttu-id="21e59-130">Určuje, že by měl modul common language runtime kontrolovat kódování název metody.</span><span class="sxs-lookup"><span data-stu-id="21e59-130">Specifies that the common language runtime should check the encoding of the method name.</span></span>|  
|`mdHasSecurity`|<span data-ttu-id="21e59-131">Určuje, že metoda má zabezpečení s ním spojená.</span><span class="sxs-lookup"><span data-stu-id="21e59-131">Specifies that the method has security associated with it.</span></span>|  
|`mdRequireSecObject`|<span data-ttu-id="21e59-132">Určuje, že metoda volá jinou metodu obsahující zabezpečovací kód.</span><span class="sxs-lookup"><span data-stu-id="21e59-132">Specifies that the method calls another method containing security code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="21e59-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="21e59-133">Requirements</span></span>  
 <span data-ttu-id="21e59-134">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21e59-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21e59-135">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="21e59-135">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="21e59-136">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21e59-136">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21e59-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="21e59-137">See Also</span></span>  
 [<span data-ttu-id="21e59-138">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="21e59-138">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
