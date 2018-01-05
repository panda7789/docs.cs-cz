---
title: "CorCheckDuplicatesFor – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorCheckDuplicatesFor
api_location: mscoree.dll
api_type: COM
f1_keywords: CorCheckDuplicatesFor
helpviewer_keywords: CorCheckDuplicatesFor enumeration [.NET Framework metadata]
ms.assetid: d8ec8d3c-70f7-4cc6-9957-68068fd8f49c
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0c5a9376f6d56e2a21ee474e2724ce5eff8f6f63
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corcheckduplicatesfor-enumeration"></a><span data-ttu-id="e6860-102">CorCheckDuplicatesFor – výčet</span><span class="sxs-lookup"><span data-stu-id="e6860-102">CorCheckDuplicatesFor Enumeration</span></span>
<span data-ttu-id="e6860-103">Určuje metadata tokeny, které budou sloužit k duplicitní položky.</span><span class="sxs-lookup"><span data-stu-id="e6860-103">Specifies the metadata tokens that will be checked for duplicates.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6860-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6860-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="e6860-105">Členové</span><span class="sxs-lookup"><span data-stu-id="e6860-105">Members</span></span>  
  
|<span data-ttu-id="e6860-106">Člen</span><span class="sxs-lookup"><span data-stu-id="e6860-106">Member</span></span>|<span data-ttu-id="e6860-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e6860-107">Description</span></span>|  
|------------|-----------------|  
|`MDDupAll`|<span data-ttu-id="e6860-108">Zkontrolujte všechny tokeny metadat pro duplicitní položky.</span><span class="sxs-lookup"><span data-stu-id="e6860-108">Check all metadata tokens for duplicates.</span></span>|  
|`MDDupENC`|<span data-ttu-id="e6860-109">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="e6860-109">Not used.</span></span>|  
|`MDNoDupChecks`|<span data-ttu-id="e6860-110">Neprovádět kontrolu tokenů metadat pro duplicitní položky.</span><span class="sxs-lookup"><span data-stu-id="e6860-110">Do not check metadata tokens for duplicates.</span></span>|  
|`MDDupTypeDef`|<span data-ttu-id="e6860-111">Zkontrolujte duplikáty `mdTypeDef` tokeny.</span><span class="sxs-lookup"><span data-stu-id="e6860-111">Check for duplicates of `mdTypeDef` tokens.</span></span>|  
|`MDDupInterfaceImpl`|<span data-ttu-id="e6860-112">Zkontrolujte duplikáty `mdInterfaceImpl` tokeny.</span><span class="sxs-lookup"><span data-stu-id="e6860-112">Check for duplicates of `mdInterfaceImpl` tokens.</span></span>|  
|`MDDupMethodDef`|<span data-ttu-id="e6860-113">Zkontrolujte duplikáty `mdMethodDef` tokeny.</span><span class="sxs-lookup"><span data-stu-id="e6860-113">Check for duplicates of `mdMethodDef` tokens.</span></span>|  
|`MDDupTypeRef`|<span data-ttu-id="e6860-114">Zkontrolujte duplikáty `mdTypeRef` tokeny.</span><span class="sxs-lookup"><span data-stu-id="e6860-114">Check for duplicates of `mdTypeRef` tokens.</span></span>|  
|`MDDupMemberRef`|<span data-ttu-id="e6860-115">Zkontrolujte duplikáty `mdMemberRef` tokeny.</span><span class="sxs-lookup"><span data-stu-id="e6860-115">Check for duplicates of `mdMemberRef` tokens.</span></span>|  
|`MDDupCustomAttribute`|<span data-ttu-id="e6860-116">Zkontrolujte duplikáty `mdCustomAttribute` tokeny.</span><span class="sxs-lookup"><span data-stu-id="e6860-116">Check for duplicates of `mdCustomAttribute` tokens.</span></span>|  
|`MDDupParamDef`|<span data-ttu-id="e6860-117">Zkontrolujte duplikáty `mdParamDef` tokeny.</span><span class="sxs-lookup"><span data-stu-id="e6860-117">Check for duplicates of `mdParamDef` tokens.</span></span>|  
|`MDDupPermission`|<span data-ttu-id="e6860-118">Zkontrolujte duplikáty `mdPermission` tokeny.</span><span class="sxs-lookup"><span data-stu-id="e6860-118">Check for duplicates of `mdPermission` tokens.</span></span>|  
|`MDDupProperty`|<span data-ttu-id="e6860-119">Zkontrolujte duplikáty `mdProperty` tokeny.</span><span class="sxs-lookup"><span data-stu-id="e6860-119">Check for duplicates of `mdProperty` tokens.</span></span>|  
|`MDDupEvent`|<span data-ttu-id="e6860-120">Zkontrolujte duplikáty `mdEvent` tokeny.</span><span class="sxs-lookup"><span data-stu-id="e6860-120">Check for duplicates of `mdEvent` tokens.</span></span>|  
|`MDDupFieldDef`|<span data-ttu-id="e6860-121">Zkontrolujte duplikáty `mdFieldDef` tokeny.</span><span class="sxs-lookup"><span data-stu-id="e6860-121">Check for duplicates of `mdFieldDef` tokens.</span></span>|  
|`MDDupSignature`|<span data-ttu-id="e6860-122">Zkontrolujte duplikáty `mdSignature` tokeny.</span><span class="sxs-lookup"><span data-stu-id="e6860-122">Check for duplicates of `mdSignature` tokens.</span></span>|  
|`MDDupModuleRef`|<span data-ttu-id="e6860-123">Zkontrolujte duplikáty `mdModuleRef` tokeny.</span><span class="sxs-lookup"><span data-stu-id="e6860-123">Check for duplicates of `mdModuleRef` tokens.</span></span>|  
|`MDDupTypeSpec`|<span data-ttu-id="e6860-124">Zkontrolujte duplikáty `mdTypeSpec` tokeny.</span><span class="sxs-lookup"><span data-stu-id="e6860-124">Check for duplicates of `mdTypeSpec` tokens.</span></span>|  
|`MDDupImplMap`|<span data-ttu-id="e6860-125">Zkontrolujte duplikáty `mdImplMap` tokeny.</span><span class="sxs-lookup"><span data-stu-id="e6860-125">Check for duplicates of `mdImplMap` tokens.</span></span>|  
|`MDDupAssemblyRef`|<span data-ttu-id="e6860-126">Zkontrolujte duplikáty `mdAssemblyRef` tokeny.</span><span class="sxs-lookup"><span data-stu-id="e6860-126">Check for duplicates of `mdAssemblyRef` tokens.</span></span>|  
|`MDDupFile`|<span data-ttu-id="e6860-127">Zkontrolujte duplikáty `mdFile` tokeny.</span><span class="sxs-lookup"><span data-stu-id="e6860-127">Check for duplicates of `mdFile` tokens.</span></span>|  
|`MDDupExportedType`|<span data-ttu-id="e6860-128">Zkontrolujte duplikáty `mdExportedType` tokeny.</span><span class="sxs-lookup"><span data-stu-id="e6860-128">Check for duplicates of `mdExportedType` tokens.</span></span>|  
|`MDDupManifestResource`|<span data-ttu-id="e6860-129">Zkontrolujte duplikáty `mdManifestResource` tokeny.</span><span class="sxs-lookup"><span data-stu-id="e6860-129">Check for duplicates of `mdManifestResource` tokens.</span></span>|  
|`MDDupGenericParam`|<span data-ttu-id="e6860-130">Zkontrolujte duplikáty `mdGenericParam` tokeny.</span><span class="sxs-lookup"><span data-stu-id="e6860-130">Check for duplicates of `mdGenericParam` tokens.</span></span>|  
|`MDDupMethodSpec`|<span data-ttu-id="e6860-131">Zkontrolujte duplikáty `mdMethodSpec` tokeny.</span><span class="sxs-lookup"><span data-stu-id="e6860-131">Check for duplicates of `mdMethodSpec` tokens.</span></span>|  
|`MDDupGenericParamConstraint`|<span data-ttu-id="e6860-132">Zkontrolujte duplikáty `mdGenericParamConstraint` tokeny.</span><span class="sxs-lookup"><span data-stu-id="e6860-132">Check for duplicates of `mdGenericParamConstraint` tokens.</span></span>|  
|`MDDupAssembly`|<span data-ttu-id="e6860-133">Zkontrolujte duplikáty `mdAssembly` tokeny.</span><span class="sxs-lookup"><span data-stu-id="e6860-133">Check for duplicates of `mdAssembly` tokens.</span></span>|  
|`MDDupDefault`|<span data-ttu-id="e6860-134">Zkontrolujte duplikáty `mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`, a `mdMethodSpec` tokeny.</span><span class="sxs-lookup"><span data-stu-id="e6860-134">Check for duplicates of `mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`, and `mdMethodSpec` tokens.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e6860-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e6860-135">Requirements</span></span>  
 <span data-ttu-id="e6860-136">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6860-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6860-137">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="e6860-137">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="e6860-138">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6860-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6860-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="e6860-139">See Also</span></span>  
 [<span data-ttu-id="e6860-140">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="e6860-140">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
