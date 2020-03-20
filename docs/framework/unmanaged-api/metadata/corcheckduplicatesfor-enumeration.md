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
ms.openlocfilehash: 04dc12ab4d7d178ebf1575a3260f9f4981972782
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176185"
---
# <a name="corcheckduplicatesfor-enumeration"></a><span data-ttu-id="8743d-102">CorCheckDuplicatesFor – výčet</span><span class="sxs-lookup"><span data-stu-id="8743d-102">CorCheckDuplicatesFor Enumeration</span></span>
<span data-ttu-id="8743d-103">Určuje tokeny metadat, které budou zkontrolovány na duplikáty.</span><span class="sxs-lookup"><span data-stu-id="8743d-103">Specifies the metadata tokens that will be checked for duplicates.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8743d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8743d-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="8743d-105">Členové</span><span class="sxs-lookup"><span data-stu-id="8743d-105">Members</span></span>  
  
|<span data-ttu-id="8743d-106">Člen</span><span class="sxs-lookup"><span data-stu-id="8743d-106">Member</span></span>|<span data-ttu-id="8743d-107">Popis</span><span class="sxs-lookup"><span data-stu-id="8743d-107">Description</span></span>|  
|------------|-----------------|  
|`MDDupAll`|<span data-ttu-id="8743d-108">Zkontrolujte, zda všechny tokeny metadat neobsahují duplicity.</span><span class="sxs-lookup"><span data-stu-id="8743d-108">Check all metadata tokens for duplicates.</span></span>|  
|`MDDupENC`|<span data-ttu-id="8743d-109">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="8743d-109">Not used.</span></span>|  
|`MDNoDupChecks`|<span data-ttu-id="8743d-110">Nekontrolujte tokeny metadat pro duplicity.</span><span class="sxs-lookup"><span data-stu-id="8743d-110">Do not check metadata tokens for duplicates.</span></span>|  
|`MDDupTypeDef`|<span data-ttu-id="8743d-111">Zkontrolujte duplicity `mdTypeDef` tokenů.</span><span class="sxs-lookup"><span data-stu-id="8743d-111">Check for duplicates of `mdTypeDef` tokens.</span></span>|  
|`MDDupInterfaceImpl`|<span data-ttu-id="8743d-112">Zkontrolujte duplicity `mdInterfaceImpl` tokenů.</span><span class="sxs-lookup"><span data-stu-id="8743d-112">Check for duplicates of `mdInterfaceImpl` tokens.</span></span>|  
|`MDDupMethodDef`|<span data-ttu-id="8743d-113">Zkontrolujte duplicity `mdMethodDef` tokenů.</span><span class="sxs-lookup"><span data-stu-id="8743d-113">Check for duplicates of `mdMethodDef` tokens.</span></span>|  
|`MDDupTypeRef`|<span data-ttu-id="8743d-114">Zkontrolujte duplicity `mdTypeRef` tokenů.</span><span class="sxs-lookup"><span data-stu-id="8743d-114">Check for duplicates of `mdTypeRef` tokens.</span></span>|  
|`MDDupMemberRef`|<span data-ttu-id="8743d-115">Zkontrolujte duplicity `mdMemberRef` tokenů.</span><span class="sxs-lookup"><span data-stu-id="8743d-115">Check for duplicates of `mdMemberRef` tokens.</span></span>|  
|`MDDupCustomAttribute`|<span data-ttu-id="8743d-116">Zkontrolujte duplicity `mdCustomAttribute` tokenů.</span><span class="sxs-lookup"><span data-stu-id="8743d-116">Check for duplicates of `mdCustomAttribute` tokens.</span></span>|  
|`MDDupParamDef`|<span data-ttu-id="8743d-117">Zkontrolujte duplicity `mdParamDef` tokenů.</span><span class="sxs-lookup"><span data-stu-id="8743d-117">Check for duplicates of `mdParamDef` tokens.</span></span>|  
|`MDDupPermission`|<span data-ttu-id="8743d-118">Zkontrolujte duplicity `mdPermission` tokenů.</span><span class="sxs-lookup"><span data-stu-id="8743d-118">Check for duplicates of `mdPermission` tokens.</span></span>|  
|`MDDupProperty`|<span data-ttu-id="8743d-119">Zkontrolujte duplicity `mdProperty` tokenů.</span><span class="sxs-lookup"><span data-stu-id="8743d-119">Check for duplicates of `mdProperty` tokens.</span></span>|  
|`MDDupEvent`|<span data-ttu-id="8743d-120">Zkontrolujte duplicity `mdEvent` tokenů.</span><span class="sxs-lookup"><span data-stu-id="8743d-120">Check for duplicates of `mdEvent` tokens.</span></span>|  
|`MDDupFieldDef`|<span data-ttu-id="8743d-121">Zkontrolujte duplicity `mdFieldDef` tokenů.</span><span class="sxs-lookup"><span data-stu-id="8743d-121">Check for duplicates of `mdFieldDef` tokens.</span></span>|  
|`MDDupSignature`|<span data-ttu-id="8743d-122">Zkontrolujte duplicity `mdSignature` tokenů.</span><span class="sxs-lookup"><span data-stu-id="8743d-122">Check for duplicates of `mdSignature` tokens.</span></span>|  
|`MDDupModuleRef`|<span data-ttu-id="8743d-123">Zkontrolujte duplicity `mdModuleRef` tokenů.</span><span class="sxs-lookup"><span data-stu-id="8743d-123">Check for duplicates of `mdModuleRef` tokens.</span></span>|  
|`MDDupTypeSpec`|<span data-ttu-id="8743d-124">Zkontrolujte duplicity `mdTypeSpec` tokenů.</span><span class="sxs-lookup"><span data-stu-id="8743d-124">Check for duplicates of `mdTypeSpec` tokens.</span></span>|  
|`MDDupImplMap`|<span data-ttu-id="8743d-125">Zkontrolujte duplicity `mdImplMap` tokenů.</span><span class="sxs-lookup"><span data-stu-id="8743d-125">Check for duplicates of `mdImplMap` tokens.</span></span>|  
|`MDDupAssemblyRef`|<span data-ttu-id="8743d-126">Zkontrolujte duplicity `mdAssemblyRef` tokenů.</span><span class="sxs-lookup"><span data-stu-id="8743d-126">Check for duplicates of `mdAssemblyRef` tokens.</span></span>|  
|`MDDupFile`|<span data-ttu-id="8743d-127">Zkontrolujte duplicity `mdFile` tokenů.</span><span class="sxs-lookup"><span data-stu-id="8743d-127">Check for duplicates of `mdFile` tokens.</span></span>|  
|`MDDupExportedType`|<span data-ttu-id="8743d-128">Zkontrolujte duplicity `mdExportedType` tokenů.</span><span class="sxs-lookup"><span data-stu-id="8743d-128">Check for duplicates of `mdExportedType` tokens.</span></span>|  
|`MDDupManifestResource`|<span data-ttu-id="8743d-129">Zkontrolujte duplicity `mdManifestResource` tokenů.</span><span class="sxs-lookup"><span data-stu-id="8743d-129">Check for duplicates of `mdManifestResource` tokens.</span></span>|  
|`MDDupGenericParam`|<span data-ttu-id="8743d-130">Zkontrolujte duplicity `mdGenericParam` tokenů.</span><span class="sxs-lookup"><span data-stu-id="8743d-130">Check for duplicates of `mdGenericParam` tokens.</span></span>|  
|`MDDupMethodSpec`|<span data-ttu-id="8743d-131">Zkontrolujte duplicity `mdMethodSpec` tokenů.</span><span class="sxs-lookup"><span data-stu-id="8743d-131">Check for duplicates of `mdMethodSpec` tokens.</span></span>|  
|`MDDupGenericParamConstraint`|<span data-ttu-id="8743d-132">Zkontrolujte duplicity `mdGenericParamConstraint` tokenů.</span><span class="sxs-lookup"><span data-stu-id="8743d-132">Check for duplicates of `mdGenericParamConstraint` tokens.</span></span>|  
|`MDDupAssembly`|<span data-ttu-id="8743d-133">Zkontrolujte duplicity `mdAssembly` tokenů.</span><span class="sxs-lookup"><span data-stu-id="8743d-133">Check for duplicates of `mdAssembly` tokens.</span></span>|  
|`MDDupDefault`|<span data-ttu-id="8743d-134">Zkontrolujte duplicity `mdMemberRef` `mdTypeRef`, `mdSignature` `mdTypeSpec`, `mdMethodSpec` , a tokeny.</span><span class="sxs-lookup"><span data-stu-id="8743d-134">Check for duplicates of `mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`, and `mdMethodSpec` tokens.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8743d-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8743d-135">Requirements</span></span>  
 <span data-ttu-id="8743d-136">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8743d-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8743d-137">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="8743d-137">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="8743d-138">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8743d-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8743d-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="8743d-139">See also</span></span>

- [<span data-ttu-id="8743d-140">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="8743d-140">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
