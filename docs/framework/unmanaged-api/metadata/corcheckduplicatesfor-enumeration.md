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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074869"
---
# <a name="corcheckduplicatesfor-enumeration"></a><span data-ttu-id="cb3b4-102">CorCheckDuplicatesFor – výčet</span><span class="sxs-lookup"><span data-stu-id="cb3b4-102">CorCheckDuplicatesFor Enumeration</span></span>
<span data-ttu-id="cb3b4-103">Určuje tokeny metadat, které budou zkontrolovat duplicitu.</span><span class="sxs-lookup"><span data-stu-id="cb3b4-103">Specifies the metadata tokens that will be checked for duplicates.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb3b4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cb3b4-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="cb3b4-105">Členové</span><span class="sxs-lookup"><span data-stu-id="cb3b4-105">Members</span></span>  
  
|<span data-ttu-id="cb3b4-106">Člen</span><span class="sxs-lookup"><span data-stu-id="cb3b4-106">Member</span></span>|<span data-ttu-id="cb3b4-107">Popis</span><span class="sxs-lookup"><span data-stu-id="cb3b4-107">Description</span></span>|  
|------------|-----------------|  
|`MDDupAll`|<span data-ttu-id="cb3b4-108">Zkontrolujte všechny tokeny metadat pro duplicitní položky.</span><span class="sxs-lookup"><span data-stu-id="cb3b4-108">Check all metadata tokens for duplicates.</span></span>|  
|`MDDupENC`|<span data-ttu-id="cb3b4-109">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="cb3b4-109">Not used.</span></span>|  
|`MDNoDupChecks`|<span data-ttu-id="cb3b4-110">Nezaškrtávejte políčko tokeny metadat pro duplicitní položky.</span><span class="sxs-lookup"><span data-stu-id="cb3b4-110">Do not check metadata tokens for duplicates.</span></span>|  
|`MDDupTypeDef`|<span data-ttu-id="cb3b4-111">Zkontrolovat duplikáty `mdTypeDef` tokeny.</span><span class="sxs-lookup"><span data-stu-id="cb3b4-111">Check for duplicates of `mdTypeDef` tokens.</span></span>|  
|`MDDupInterfaceImpl`|<span data-ttu-id="cb3b4-112">Zkontrolovat duplikáty `mdInterfaceImpl` tokeny.</span><span class="sxs-lookup"><span data-stu-id="cb3b4-112">Check for duplicates of `mdInterfaceImpl` tokens.</span></span>|  
|`MDDupMethodDef`|<span data-ttu-id="cb3b4-113">Zkontrolovat duplikáty `mdMethodDef` tokeny.</span><span class="sxs-lookup"><span data-stu-id="cb3b4-113">Check for duplicates of `mdMethodDef` tokens.</span></span>|  
|`MDDupTypeRef`|<span data-ttu-id="cb3b4-114">Zkontrolovat duplikáty `mdTypeRef` tokeny.</span><span class="sxs-lookup"><span data-stu-id="cb3b4-114">Check for duplicates of `mdTypeRef` tokens.</span></span>|  
|`MDDupMemberRef`|<span data-ttu-id="cb3b4-115">Zkontrolovat duplikáty `mdMemberRef` tokeny.</span><span class="sxs-lookup"><span data-stu-id="cb3b4-115">Check for duplicates of `mdMemberRef` tokens.</span></span>|  
|`MDDupCustomAttribute`|<span data-ttu-id="cb3b4-116">Zkontrolovat duplikáty `mdCustomAttribute` tokeny.</span><span class="sxs-lookup"><span data-stu-id="cb3b4-116">Check for duplicates of `mdCustomAttribute` tokens.</span></span>|  
|`MDDupParamDef`|<span data-ttu-id="cb3b4-117">Zkontrolovat duplikáty `mdParamDef` tokeny.</span><span class="sxs-lookup"><span data-stu-id="cb3b4-117">Check for duplicates of `mdParamDef` tokens.</span></span>|  
|`MDDupPermission`|<span data-ttu-id="cb3b4-118">Zkontrolovat duplikáty `mdPermission` tokeny.</span><span class="sxs-lookup"><span data-stu-id="cb3b4-118">Check for duplicates of `mdPermission` tokens.</span></span>|  
|`MDDupProperty`|<span data-ttu-id="cb3b4-119">Zkontrolovat duplikáty `mdProperty` tokeny.</span><span class="sxs-lookup"><span data-stu-id="cb3b4-119">Check for duplicates of `mdProperty` tokens.</span></span>|  
|`MDDupEvent`|<span data-ttu-id="cb3b4-120">Zkontrolovat duplikáty `mdEvent` tokeny.</span><span class="sxs-lookup"><span data-stu-id="cb3b4-120">Check for duplicates of `mdEvent` tokens.</span></span>|  
|`MDDupFieldDef`|<span data-ttu-id="cb3b4-121">Zkontrolovat duplikáty `mdFieldDef` tokeny.</span><span class="sxs-lookup"><span data-stu-id="cb3b4-121">Check for duplicates of `mdFieldDef` tokens.</span></span>|  
|`MDDupSignature`|<span data-ttu-id="cb3b4-122">Zkontrolovat duplikáty `mdSignature` tokeny.</span><span class="sxs-lookup"><span data-stu-id="cb3b4-122">Check for duplicates of `mdSignature` tokens.</span></span>|  
|`MDDupModuleRef`|<span data-ttu-id="cb3b4-123">Zkontrolovat duplikáty `mdModuleRef` tokeny.</span><span class="sxs-lookup"><span data-stu-id="cb3b4-123">Check for duplicates of `mdModuleRef` tokens.</span></span>|  
|`MDDupTypeSpec`|<span data-ttu-id="cb3b4-124">Zkontrolovat duplikáty `mdTypeSpec` tokeny.</span><span class="sxs-lookup"><span data-stu-id="cb3b4-124">Check for duplicates of `mdTypeSpec` tokens.</span></span>|  
|`MDDupImplMap`|<span data-ttu-id="cb3b4-125">Zkontrolovat duplikáty `mdImplMap` tokeny.</span><span class="sxs-lookup"><span data-stu-id="cb3b4-125">Check for duplicates of `mdImplMap` tokens.</span></span>|  
|`MDDupAssemblyRef`|<span data-ttu-id="cb3b4-126">Zkontrolovat duplikáty `mdAssemblyRef` tokeny.</span><span class="sxs-lookup"><span data-stu-id="cb3b4-126">Check for duplicates of `mdAssemblyRef` tokens.</span></span>|  
|`MDDupFile`|<span data-ttu-id="cb3b4-127">Zkontrolovat duplikáty `mdFile` tokeny.</span><span class="sxs-lookup"><span data-stu-id="cb3b4-127">Check for duplicates of `mdFile` tokens.</span></span>|  
|`MDDupExportedType`|<span data-ttu-id="cb3b4-128">Zkontrolovat duplikáty `mdExportedType` tokeny.</span><span class="sxs-lookup"><span data-stu-id="cb3b4-128">Check for duplicates of `mdExportedType` tokens.</span></span>|  
|`MDDupManifestResource`|<span data-ttu-id="cb3b4-129">Zkontrolovat duplikáty `mdManifestResource` tokeny.</span><span class="sxs-lookup"><span data-stu-id="cb3b4-129">Check for duplicates of `mdManifestResource` tokens.</span></span>|  
|`MDDupGenericParam`|<span data-ttu-id="cb3b4-130">Zkontrolovat duplikáty `mdGenericParam` tokeny.</span><span class="sxs-lookup"><span data-stu-id="cb3b4-130">Check for duplicates of `mdGenericParam` tokens.</span></span>|  
|`MDDupMethodSpec`|<span data-ttu-id="cb3b4-131">Zkontrolovat duplikáty `mdMethodSpec` tokeny.</span><span class="sxs-lookup"><span data-stu-id="cb3b4-131">Check for duplicates of `mdMethodSpec` tokens.</span></span>|  
|`MDDupGenericParamConstraint`|<span data-ttu-id="cb3b4-132">Zkontrolovat duplikáty `mdGenericParamConstraint` tokeny.</span><span class="sxs-lookup"><span data-stu-id="cb3b4-132">Check for duplicates of `mdGenericParamConstraint` tokens.</span></span>|  
|`MDDupAssembly`|<span data-ttu-id="cb3b4-133">Zkontrolovat duplikáty `mdAssembly` tokeny.</span><span class="sxs-lookup"><span data-stu-id="cb3b4-133">Check for duplicates of `mdAssembly` tokens.</span></span>|  
|`MDDupDefault`|<span data-ttu-id="cb3b4-134">Zkontrolovat duplikáty `mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`, a `mdMethodSpec` tokeny.</span><span class="sxs-lookup"><span data-stu-id="cb3b4-134">Check for duplicates of `mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`, and `mdMethodSpec` tokens.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cb3b4-135">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cb3b4-135">Requirements</span></span>  
 <span data-ttu-id="cb3b4-136">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb3b4-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb3b4-137">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="cb3b4-137">**Header:** CorHdr.h</span></span>  
  
 **<span data-ttu-id="cb3b4-138">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="cb3b4-138">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cb3b4-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cb3b4-139">See also</span></span>

- [<span data-ttu-id="cb3b4-140">Výčty metadat</span><span class="sxs-lookup"><span data-stu-id="cb3b4-140">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
