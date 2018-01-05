---
title: "CorTokenType – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorTokenType
api_location: mscoree.dll
api_type: COM
f1_keywords: CorTokenType
helpviewer_keywords: CorTokenType enumeration [.NET Framework metadata]
ms.assetid: 93c9a369-225f-4eff-9b78-3fbee4902cf1
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ae9164753e919b80e635582b15da5263194e215f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="cortokentype-enumeration"></a><span data-ttu-id="88db6-102">CorTokenType – výčet</span><span class="sxs-lookup"><span data-stu-id="88db6-102">CorTokenType Enumeration</span></span>
<span data-ttu-id="88db6-103">Určuje typ tokenu metadat.</span><span class="sxs-lookup"><span data-stu-id="88db6-103">Indicates the type of a metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88db6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="88db6-104">Syntax</span></span>  
  
```  
typedef enum CorTokenType {  
  
    mdtModule                       = 0x00000000,  
    mdtTypeRef                      = 0x01000000,  
    mdtTypeDef                      = 0x02000000,  
    mdtFieldDef                     = 0x04000000,  
    mdtMethodDef                    = 0x06000000,  
    mdtParamDef                     = 0x08000000,  
    mdtInterfaceImpl                = 0x09000000,  
    mdtMemberRef                    = 0x0a000000,  
    mdtCustomAttribute              = 0x0c000000,  
    mdtPermission                   = 0x0e000000,  
    mdtSignature                    = 0x11000000,  
    mdtEvent                        = 0x14000000,  
    mdtProperty                     = 0x17000000,  
    mdtModuleRef                    = 0x1a000000,  
    mdtTypeSpec                     = 0x1b000000,  
    mdtAssembly                     = 0x20000000,  
    mdtAssemblyRef                  = 0x23000000,  
    mdtFile                         = 0x26000000,  
    mdtExportedType                 = 0x27000000,  
    mdtManifestResource             = 0x28000000,  
    mdtGenericParam                 = 0x2a000000,  
    mdtMethodSpec                   = 0x2b000000,  
    mdtGenericParamConstraint       = 0x2c000000,  
    mdtString                       = 0x70000000,  
    mdtName                         = 0x71000000,  
    mdtBaseType                     = 0x72000000  
  
} CorTokenType;  
```  
  
## <a name="members"></a><span data-ttu-id="88db6-105">Členové</span><span class="sxs-lookup"><span data-stu-id="88db6-105">Members</span></span>  
  
|<span data-ttu-id="88db6-106">Člen</span><span class="sxs-lookup"><span data-stu-id="88db6-106">Member</span></span>|<span data-ttu-id="88db6-107">Popis</span><span class="sxs-lookup"><span data-stu-id="88db6-107">Description</span></span>|  
|------------|-----------------|  
|`mdtModule`|<span data-ttu-id="88db6-108">`mdModule` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="88db6-108">An `mdModule` token.</span></span>|  
|`mdtTypeRef`|<span data-ttu-id="88db6-109">`mdTypeRef` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="88db6-109">An `mdTypeRef` token.</span></span>|  
|`mdtTypeDef`|<span data-ttu-id="88db6-110">`mdTypeDef` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="88db6-110">An `mdTypeDef` token.</span></span>|  
|`mdtFieldDef`|<span data-ttu-id="88db6-111">`mdFieldDef` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="88db6-111">An `mdFieldDef` token.</span></span>|  
|`mdtMethodDef`|<span data-ttu-id="88db6-112">`mdMethodDef` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="88db6-112">An `mdMethodDef` token.</span></span>|  
|`mdtParamDef`|<span data-ttu-id="88db6-113">`mdParamDef` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="88db6-113">An `mdParamDef` token.</span></span>|  
|`mdtInterfaceImpl`|<span data-ttu-id="88db6-114">`mdInterfaceImpl` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="88db6-114">An `mdInterfaceImpl` token.</span></span>|  
|`mdtMemberRef`|<span data-ttu-id="88db6-115">`mdMemberRef` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="88db6-115">An `mdMemberRef` token.</span></span>|  
|`mdtCustomAttribute`|<span data-ttu-id="88db6-116">`mdCustomAttribute` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="88db6-116">An `mdCustomAttribute` token.</span></span>|  
|`mdtPermission`|<span data-ttu-id="88db6-117">`mdPermission` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="88db6-117">An `mdPermission` token.</span></span>|  
|`mdtSignature`|<span data-ttu-id="88db6-118">`mdSignature` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="88db6-118">An `mdSignature` token.</span></span>|  
|`mdtEvent`|<span data-ttu-id="88db6-119">`mdEvent` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="88db6-119">An `mdEvent` token.</span></span>|  
|`mdtProperty`|<span data-ttu-id="88db6-120">`mdProperty` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="88db6-120">An `mdProperty` token.</span></span>|  
|`mdtModuleRef`|<span data-ttu-id="88db6-121">`mdModuleRef` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="88db6-121">An `mdModuleRef` token.</span></span>|  
|`mdtTypeSpec`|<span data-ttu-id="88db6-122">`mdTypeSpec` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="88db6-122">An `mdTypeSpec` token.</span></span>|  
|`mdtAssembly`|<span data-ttu-id="88db6-123">`mdAssembly` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="88db6-123">An `mdAssembly` token.</span></span>|  
|`mdtAssemblyRef`|<span data-ttu-id="88db6-124">`mdAssemblyRef` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="88db6-124">An `mdAssemblyRef` token.</span></span>|  
|`mdtFile`|<span data-ttu-id="88db6-125">`mdFile` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="88db6-125">An `mdFile` token.</span></span>|  
|`mdtExportedType`|<span data-ttu-id="88db6-126">`mdExportedType` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="88db6-126">An `mdExportedType` token.</span></span>|  
|`mdtManifestResource`|<span data-ttu-id="88db6-127">`mdManifestResource` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="88db6-127">An `mdManifestResource` token.</span></span>|  
|`mdtGenericParam`|<span data-ttu-id="88db6-128">`mdGenericParam` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="88db6-128">An `mdGenericParam` token.</span></span>|  
|`mdtMethodSpec`|<span data-ttu-id="88db6-129">`mdMethodSpec` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="88db6-129">An `mdMethodSpec` token.</span></span>|  
|`mdtGenericParamConstraint`|<span data-ttu-id="88db6-130">`mdGenericParamConstraint` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="88db6-130">An `mdGenericParamConstraint` token.</span></span>|  
|`mdtString`|<span data-ttu-id="88db6-131">`mdString` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="88db6-131">An `mdString` token.</span></span>|  
|`mdtName`|<span data-ttu-id="88db6-132">`mdName` Tokenu.</span><span class="sxs-lookup"><span data-stu-id="88db6-132">An `mdName` token.</span></span>|  
|`mdtBaseType`|<span data-ttu-id="88db6-133">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="88db6-133">Not used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="88db6-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="88db6-134">Remarks</span></span>  
 <span data-ttu-id="88db6-135">Každá hodnota se rovná hodnotě horní byte v odpovídající tokenu metadat.</span><span class="sxs-lookup"><span data-stu-id="88db6-135">Each value is equal to the value of the top byte in the corresponding metadata token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88db6-136">Požadavky</span><span class="sxs-lookup"><span data-stu-id="88db6-136">Requirements</span></span>  
 <span data-ttu-id="88db6-137">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88db6-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88db6-138">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="88db6-138">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="88db6-139">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88db6-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88db6-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="88db6-140">See Also</span></span>  
 [<span data-ttu-id="88db6-141">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="88db6-141">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
