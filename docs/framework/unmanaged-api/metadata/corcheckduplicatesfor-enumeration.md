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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d04f5589ecffbcde59a6ffbe4f3d6c5f0b1040cd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59074869"
---
# <a name="corcheckduplicatesfor-enumeration"></a><span data-ttu-id="372c6-102">CorCheckDuplicatesFor – výčet</span><span class="sxs-lookup"><span data-stu-id="372c6-102">CorCheckDuplicatesFor Enumeration</span></span>
<span data-ttu-id="372c6-103">Určuje tokeny metadat, které budou zkontrolovat duplicitu.</span><span class="sxs-lookup"><span data-stu-id="372c6-103">Specifies the metadata tokens that will be checked for duplicates.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="372c6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="372c6-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="372c6-105">Členové</span><span class="sxs-lookup"><span data-stu-id="372c6-105">Members</span></span>  
  
|<span data-ttu-id="372c6-106">Člen</span><span class="sxs-lookup"><span data-stu-id="372c6-106">Member</span></span>|<span data-ttu-id="372c6-107">Popis</span><span class="sxs-lookup"><span data-stu-id="372c6-107">Description</span></span>|  
|------------|-----------------|  
|`MDDupAll`|<span data-ttu-id="372c6-108">Zkontrolujte všechny tokeny metadat pro duplicitní položky.</span><span class="sxs-lookup"><span data-stu-id="372c6-108">Check all metadata tokens for duplicates.</span></span>|  
|`MDDupENC`|<span data-ttu-id="372c6-109">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="372c6-109">Not used.</span></span>|  
|`MDNoDupChecks`|<span data-ttu-id="372c6-110">Nezaškrtávejte políčko tokeny metadat pro duplicitní položky.</span><span class="sxs-lookup"><span data-stu-id="372c6-110">Do not check metadata tokens for duplicates.</span></span>|  
|`MDDupTypeDef`|<span data-ttu-id="372c6-111">Zkontrolovat duplikáty `mdTypeDef` tokeny.</span><span class="sxs-lookup"><span data-stu-id="372c6-111">Check for duplicates of `mdTypeDef` tokens.</span></span>|  
|`MDDupInterfaceImpl`|<span data-ttu-id="372c6-112">Zkontrolovat duplikáty `mdInterfaceImpl` tokeny.</span><span class="sxs-lookup"><span data-stu-id="372c6-112">Check for duplicates of `mdInterfaceImpl` tokens.</span></span>|  
|`MDDupMethodDef`|<span data-ttu-id="372c6-113">Zkontrolovat duplikáty `mdMethodDef` tokeny.</span><span class="sxs-lookup"><span data-stu-id="372c6-113">Check for duplicates of `mdMethodDef` tokens.</span></span>|  
|`MDDupTypeRef`|<span data-ttu-id="372c6-114">Zkontrolovat duplikáty `mdTypeRef` tokeny.</span><span class="sxs-lookup"><span data-stu-id="372c6-114">Check for duplicates of `mdTypeRef` tokens.</span></span>|  
|`MDDupMemberRef`|<span data-ttu-id="372c6-115">Zkontrolovat duplikáty `mdMemberRef` tokeny.</span><span class="sxs-lookup"><span data-stu-id="372c6-115">Check for duplicates of `mdMemberRef` tokens.</span></span>|  
|`MDDupCustomAttribute`|<span data-ttu-id="372c6-116">Zkontrolovat duplikáty `mdCustomAttribute` tokeny.</span><span class="sxs-lookup"><span data-stu-id="372c6-116">Check for duplicates of `mdCustomAttribute` tokens.</span></span>|  
|`MDDupParamDef`|<span data-ttu-id="372c6-117">Zkontrolovat duplikáty `mdParamDef` tokeny.</span><span class="sxs-lookup"><span data-stu-id="372c6-117">Check for duplicates of `mdParamDef` tokens.</span></span>|  
|`MDDupPermission`|<span data-ttu-id="372c6-118">Zkontrolovat duplikáty `mdPermission` tokeny.</span><span class="sxs-lookup"><span data-stu-id="372c6-118">Check for duplicates of `mdPermission` tokens.</span></span>|  
|`MDDupProperty`|<span data-ttu-id="372c6-119">Zkontrolovat duplikáty `mdProperty` tokeny.</span><span class="sxs-lookup"><span data-stu-id="372c6-119">Check for duplicates of `mdProperty` tokens.</span></span>|  
|`MDDupEvent`|<span data-ttu-id="372c6-120">Zkontrolovat duplikáty `mdEvent` tokeny.</span><span class="sxs-lookup"><span data-stu-id="372c6-120">Check for duplicates of `mdEvent` tokens.</span></span>|  
|`MDDupFieldDef`|<span data-ttu-id="372c6-121">Zkontrolovat duplikáty `mdFieldDef` tokeny.</span><span class="sxs-lookup"><span data-stu-id="372c6-121">Check for duplicates of `mdFieldDef` tokens.</span></span>|  
|`MDDupSignature`|<span data-ttu-id="372c6-122">Zkontrolovat duplikáty `mdSignature` tokeny.</span><span class="sxs-lookup"><span data-stu-id="372c6-122">Check for duplicates of `mdSignature` tokens.</span></span>|  
|`MDDupModuleRef`|<span data-ttu-id="372c6-123">Zkontrolovat duplikáty `mdModuleRef` tokeny.</span><span class="sxs-lookup"><span data-stu-id="372c6-123">Check for duplicates of `mdModuleRef` tokens.</span></span>|  
|`MDDupTypeSpec`|<span data-ttu-id="372c6-124">Zkontrolovat duplikáty `mdTypeSpec` tokeny.</span><span class="sxs-lookup"><span data-stu-id="372c6-124">Check for duplicates of `mdTypeSpec` tokens.</span></span>|  
|`MDDupImplMap`|<span data-ttu-id="372c6-125">Zkontrolovat duplikáty `mdImplMap` tokeny.</span><span class="sxs-lookup"><span data-stu-id="372c6-125">Check for duplicates of `mdImplMap` tokens.</span></span>|  
|`MDDupAssemblyRef`|<span data-ttu-id="372c6-126">Zkontrolovat duplikáty `mdAssemblyRef` tokeny.</span><span class="sxs-lookup"><span data-stu-id="372c6-126">Check for duplicates of `mdAssemblyRef` tokens.</span></span>|  
|`MDDupFile`|<span data-ttu-id="372c6-127">Zkontrolovat duplikáty `mdFile` tokeny.</span><span class="sxs-lookup"><span data-stu-id="372c6-127">Check for duplicates of `mdFile` tokens.</span></span>|  
|`MDDupExportedType`|<span data-ttu-id="372c6-128">Zkontrolovat duplikáty `mdExportedType` tokeny.</span><span class="sxs-lookup"><span data-stu-id="372c6-128">Check for duplicates of `mdExportedType` tokens.</span></span>|  
|`MDDupManifestResource`|<span data-ttu-id="372c6-129">Zkontrolovat duplikáty `mdManifestResource` tokeny.</span><span class="sxs-lookup"><span data-stu-id="372c6-129">Check for duplicates of `mdManifestResource` tokens.</span></span>|  
|`MDDupGenericParam`|<span data-ttu-id="372c6-130">Zkontrolovat duplikáty `mdGenericParam` tokeny.</span><span class="sxs-lookup"><span data-stu-id="372c6-130">Check for duplicates of `mdGenericParam` tokens.</span></span>|  
|`MDDupMethodSpec`|<span data-ttu-id="372c6-131">Zkontrolovat duplikáty `mdMethodSpec` tokeny.</span><span class="sxs-lookup"><span data-stu-id="372c6-131">Check for duplicates of `mdMethodSpec` tokens.</span></span>|  
|`MDDupGenericParamConstraint`|<span data-ttu-id="372c6-132">Zkontrolovat duplikáty `mdGenericParamConstraint` tokeny.</span><span class="sxs-lookup"><span data-stu-id="372c6-132">Check for duplicates of `mdGenericParamConstraint` tokens.</span></span>|  
|`MDDupAssembly`|<span data-ttu-id="372c6-133">Zkontrolovat duplikáty `mdAssembly` tokeny.</span><span class="sxs-lookup"><span data-stu-id="372c6-133">Check for duplicates of `mdAssembly` tokens.</span></span>|  
|`MDDupDefault`|<span data-ttu-id="372c6-134">Zkontrolovat duplikáty `mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`, a `mdMethodSpec` tokeny.</span><span class="sxs-lookup"><span data-stu-id="372c6-134">Check for duplicates of `mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`, and `mdMethodSpec` tokens.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="372c6-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="372c6-135">Requirements</span></span>  
 <span data-ttu-id="372c6-136">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="372c6-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="372c6-137">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="372c6-137">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="372c6-138">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="372c6-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="372c6-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="372c6-139">See also</span></span>

- [<span data-ttu-id="372c6-140">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="372c6-140">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
