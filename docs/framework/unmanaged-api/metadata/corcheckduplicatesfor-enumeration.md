---
title: CorCheckDuplicatesFor – výčet
ms.date: 03/30/2017
api_name:
- CorCheckDuplicatesFor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCheckDuplicatesFor
helpviewer_keywords:
- CorCheckDuplicatesFor enumeration [.NET Framework metadata]
ms.assetid: d8ec8d3c-70f7-4cc6-9957-68068fd8f49c
topic_type:
- apiref
ms.openlocfilehash: 2985c419b25b8bf76df8fee0f0f37ba9ebee3df7
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007895"
---
# <a name="corcheckduplicatesfor-enumeration"></a><span data-ttu-id="8ecda-102">CorCheckDuplicatesFor – výčet</span><span class="sxs-lookup"><span data-stu-id="8ecda-102">CorCheckDuplicatesFor Enumeration</span></span>
<span data-ttu-id="8ecda-103">Určuje tokeny metadat, u kterých budou kontrolovány duplicity.</span><span class="sxs-lookup"><span data-stu-id="8ecda-103">Specifies the metadata tokens that will be checked for duplicates.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ecda-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ecda-104">Syntax</span></span>  
  
```cpp  
typedef enum CorCheckDuplicatesFor {  
  
    MDDupAll                    = 0xffffffff,  
    MDDupENC                    = MDDupAll,  
    MDNoDupChecks               = 0x00000000,  
    MDDupTypeDef                = 0x00000001,  
    MDDupInterfaceImpl          = 0x00000002,  
    MDDupMethodDef              = 0x00000004,  
    MDDupTypeRef                = 0x00000008,  
    MDDupMemberRef              = 0x00000010,  
    MDDupCustomAttribute        = 0x00000020,  
    MDDupParamDef               = 0x00000040,  
    MDDupPermission             = 0x00000080,  
    MDDupProperty               = 0x00000100,  
    MDDupEvent                  = 0x00000200,  
    MDDupFieldDef               = 0x00000400,  
    MDDupSignature              = 0x00000800,  
    MDDupModuleRef              = 0x00001000,  
    MDDupTypeSpec               = 0x00002000,  
    MDDupImplMap                = 0x00004000,  
    MDDupAssemblyRef            = 0x00008000,  
    MDDupFile                   = 0x00010000,  
    MDDupExportedType           = 0x00020000,  
    MDDupManifestResource       = 0x00040000,  
    MDDupGenericParam           = 0x00080000,  
    MDDupMethodSpec             = 0x00100000,  
    MDDupGenericParamConstraint = 0x00200000,  
  
    MDDupAssembly               = 0x10000000,  
  
    MDDupDefault =
        MDNoDupChecks | MDDupTypeRef | MDDupMemberRef |
        MDDupSignature | MDDupTypeSpec | MDDupMethodSpec  
  
} CorCheckDuplicatesFor;  
```  
  
## <a name="members"></a><span data-ttu-id="8ecda-105">Členové</span><span class="sxs-lookup"><span data-stu-id="8ecda-105">Members</span></span>  
  
|<span data-ttu-id="8ecda-106">Člen</span><span class="sxs-lookup"><span data-stu-id="8ecda-106">Member</span></span>|<span data-ttu-id="8ecda-107">Description</span><span class="sxs-lookup"><span data-stu-id="8ecda-107">Description</span></span>|  
|------------|-----------------|  
|`MDDupAll`|<span data-ttu-id="8ecda-108">Zkontroluje všechny tokeny metadat pro duplicity.</span><span class="sxs-lookup"><span data-stu-id="8ecda-108">Check all metadata tokens for duplicates.</span></span>|  
|`MDDupENC`|<span data-ttu-id="8ecda-109">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="8ecda-109">Not used.</span></span>|  
|`MDNoDupChecks`|<span data-ttu-id="8ecda-110">Nekontrolujte tokeny metadat pro duplicity.</span><span class="sxs-lookup"><span data-stu-id="8ecda-110">Do not check metadata tokens for duplicates.</span></span>|  
|`MDDupTypeDef`|<span data-ttu-id="8ecda-111">Zkontroluje duplicity `mdTypeDef` tokenů.</span><span class="sxs-lookup"><span data-stu-id="8ecda-111">Check for duplicates of `mdTypeDef` tokens.</span></span>|  
|`MDDupInterfaceImpl`|<span data-ttu-id="8ecda-112">Zkontroluje duplicity `mdInterfaceImpl` tokenů.</span><span class="sxs-lookup"><span data-stu-id="8ecda-112">Check for duplicates of `mdInterfaceImpl` tokens.</span></span>|  
|`MDDupMethodDef`|<span data-ttu-id="8ecda-113">Zkontroluje duplicity `mdMethodDef` tokenů.</span><span class="sxs-lookup"><span data-stu-id="8ecda-113">Check for duplicates of `mdMethodDef` tokens.</span></span>|  
|`MDDupTypeRef`|<span data-ttu-id="8ecda-114">Zkontroluje duplicity `mdTypeRef` tokenů.</span><span class="sxs-lookup"><span data-stu-id="8ecda-114">Check for duplicates of `mdTypeRef` tokens.</span></span>|  
|`MDDupMemberRef`|<span data-ttu-id="8ecda-115">Zkontroluje duplicity `mdMemberRef` tokenů.</span><span class="sxs-lookup"><span data-stu-id="8ecda-115">Check for duplicates of `mdMemberRef` tokens.</span></span>|  
|`MDDupCustomAttribute`|<span data-ttu-id="8ecda-116">Zkontroluje duplicity `mdCustomAttribute` tokenů.</span><span class="sxs-lookup"><span data-stu-id="8ecda-116">Check for duplicates of `mdCustomAttribute` tokens.</span></span>|  
|`MDDupParamDef`|<span data-ttu-id="8ecda-117">Zkontroluje duplicity `mdParamDef` tokenů.</span><span class="sxs-lookup"><span data-stu-id="8ecda-117">Check for duplicates of `mdParamDef` tokens.</span></span>|  
|`MDDupPermission`|<span data-ttu-id="8ecda-118">Zkontroluje duplicity `mdPermission` tokenů.</span><span class="sxs-lookup"><span data-stu-id="8ecda-118">Check for duplicates of `mdPermission` tokens.</span></span>|  
|`MDDupProperty`|<span data-ttu-id="8ecda-119">Zkontroluje duplicity `mdProperty` tokenů.</span><span class="sxs-lookup"><span data-stu-id="8ecda-119">Check for duplicates of `mdProperty` tokens.</span></span>|  
|`MDDupEvent`|<span data-ttu-id="8ecda-120">Zkontroluje duplicity `mdEvent` tokenů.</span><span class="sxs-lookup"><span data-stu-id="8ecda-120">Check for duplicates of `mdEvent` tokens.</span></span>|  
|`MDDupFieldDef`|<span data-ttu-id="8ecda-121">Zkontroluje duplicity `mdFieldDef` tokenů.</span><span class="sxs-lookup"><span data-stu-id="8ecda-121">Check for duplicates of `mdFieldDef` tokens.</span></span>|  
|`MDDupSignature`|<span data-ttu-id="8ecda-122">Zkontroluje duplicity `mdSignature` tokenů.</span><span class="sxs-lookup"><span data-stu-id="8ecda-122">Check for duplicates of `mdSignature` tokens.</span></span>|  
|`MDDupModuleRef`|<span data-ttu-id="8ecda-123">Zkontroluje duplicity `mdModuleRef` tokenů.</span><span class="sxs-lookup"><span data-stu-id="8ecda-123">Check for duplicates of `mdModuleRef` tokens.</span></span>|  
|`MDDupTypeSpec`|<span data-ttu-id="8ecda-124">Zkontroluje duplicity `mdTypeSpec` tokenů.</span><span class="sxs-lookup"><span data-stu-id="8ecda-124">Check for duplicates of `mdTypeSpec` tokens.</span></span>|  
|`MDDupImplMap`|<span data-ttu-id="8ecda-125">Zkontroluje duplicity `mdImplMap` tokenů.</span><span class="sxs-lookup"><span data-stu-id="8ecda-125">Check for duplicates of `mdImplMap` tokens.</span></span>|  
|`MDDupAssemblyRef`|<span data-ttu-id="8ecda-126">Zkontroluje duplicity `mdAssemblyRef` tokenů.</span><span class="sxs-lookup"><span data-stu-id="8ecda-126">Check for duplicates of `mdAssemblyRef` tokens.</span></span>|  
|`MDDupFile`|<span data-ttu-id="8ecda-127">Zkontroluje duplicity `mdFile` tokenů.</span><span class="sxs-lookup"><span data-stu-id="8ecda-127">Check for duplicates of `mdFile` tokens.</span></span>|  
|`MDDupExportedType`|<span data-ttu-id="8ecda-128">Zkontroluje duplicity `mdExportedType` tokenů.</span><span class="sxs-lookup"><span data-stu-id="8ecda-128">Check for duplicates of `mdExportedType` tokens.</span></span>|  
|`MDDupManifestResource`|<span data-ttu-id="8ecda-129">Zkontroluje duplicity `mdManifestResource` tokenů.</span><span class="sxs-lookup"><span data-stu-id="8ecda-129">Check for duplicates of `mdManifestResource` tokens.</span></span>|  
|`MDDupGenericParam`|<span data-ttu-id="8ecda-130">Zkontroluje duplicity `mdGenericParam` tokenů.</span><span class="sxs-lookup"><span data-stu-id="8ecda-130">Check for duplicates of `mdGenericParam` tokens.</span></span>|  
|`MDDupMethodSpec`|<span data-ttu-id="8ecda-131">Zkontroluje duplicity `mdMethodSpec` tokenů.</span><span class="sxs-lookup"><span data-stu-id="8ecda-131">Check for duplicates of `mdMethodSpec` tokens.</span></span>|  
|`MDDupGenericParamConstraint`|<span data-ttu-id="8ecda-132">Zkontroluje duplicity `mdGenericParamConstraint` tokenů.</span><span class="sxs-lookup"><span data-stu-id="8ecda-132">Check for duplicates of `mdGenericParamConstraint` tokens.</span></span>|  
|`MDDupAssembly`|<span data-ttu-id="8ecda-133">Zkontroluje duplicity `mdAssembly` tokenů.</span><span class="sxs-lookup"><span data-stu-id="8ecda-133">Check for duplicates of `mdAssembly` tokens.</span></span>|  
|`MDDupDefault`|<span data-ttu-id="8ecda-134">Kontrolovat duplicity `mdMemberRef` `mdTypeRef` tokenů,,, `mdSignature` `mdTypeSpec` a `mdMethodSpec` .</span><span class="sxs-lookup"><span data-stu-id="8ecda-134">Check for duplicates of `mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`, and `mdMethodSpec` tokens.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8ecda-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8ecda-135">Requirements</span></span>  
 <span data-ttu-id="8ecda-136">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ecda-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ecda-137">**Hlavička:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="8ecda-137">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="8ecda-138">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ecda-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ecda-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="8ecda-139">See also</span></span>

- [<span data-ttu-id="8ecda-140">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="8ecda-140">Metadata Enumerations</span></span>](metadata-enumerations.md)
