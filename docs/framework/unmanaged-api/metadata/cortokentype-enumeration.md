---
title: CorTokenType – výčet
ms.date: 03/30/2017
api_name:
- CorTokenType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorTokenType
helpviewer_keywords:
- CorTokenType enumeration [.NET Framework metadata]
ms.assetid: 93c9a369-225f-4eff-9b78-3fbee4902cf1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b4f34340c18fddc46695fe64946c3afd90ed7454
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772303"
---
# <a name="cortokentype-enumeration"></a><span data-ttu-id="743c0-102">CorTokenType – výčet</span><span class="sxs-lookup"><span data-stu-id="743c0-102">CorTokenType Enumeration</span></span>
<span data-ttu-id="743c0-103">Určuje typ tokenu metadat.</span><span class="sxs-lookup"><span data-stu-id="743c0-103">Indicates the type of a metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="743c0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="743c0-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="743c0-105">Členové</span><span class="sxs-lookup"><span data-stu-id="743c0-105">Members</span></span>  
  
|<span data-ttu-id="743c0-106">Člen</span><span class="sxs-lookup"><span data-stu-id="743c0-106">Member</span></span>|<span data-ttu-id="743c0-107">Popis</span><span class="sxs-lookup"><span data-stu-id="743c0-107">Description</span></span>|  
|------------|-----------------|  
|`mdtModule`|<span data-ttu-id="743c0-108">`mdModule` Token.</span><span class="sxs-lookup"><span data-stu-id="743c0-108">An `mdModule` token.</span></span>|  
|`mdtTypeRef`|<span data-ttu-id="743c0-109">`mdTypeRef` Token.</span><span class="sxs-lookup"><span data-stu-id="743c0-109">An `mdTypeRef` token.</span></span>|  
|`mdtTypeDef`|<span data-ttu-id="743c0-110">`mdTypeDef` Token.</span><span class="sxs-lookup"><span data-stu-id="743c0-110">An `mdTypeDef` token.</span></span>|  
|`mdtFieldDef`|<span data-ttu-id="743c0-111">`mdFieldDef` Token.</span><span class="sxs-lookup"><span data-stu-id="743c0-111">An `mdFieldDef` token.</span></span>|  
|`mdtMethodDef`|<span data-ttu-id="743c0-112">`mdMethodDef` Token.</span><span class="sxs-lookup"><span data-stu-id="743c0-112">An `mdMethodDef` token.</span></span>|  
|`mdtParamDef`|<span data-ttu-id="743c0-113">`mdParamDef` Token.</span><span class="sxs-lookup"><span data-stu-id="743c0-113">An `mdParamDef` token.</span></span>|  
|`mdtInterfaceImpl`|<span data-ttu-id="743c0-114">`mdInterfaceImpl` Token.</span><span class="sxs-lookup"><span data-stu-id="743c0-114">An `mdInterfaceImpl` token.</span></span>|  
|`mdtMemberRef`|<span data-ttu-id="743c0-115">`mdMemberRef` Token.</span><span class="sxs-lookup"><span data-stu-id="743c0-115">An `mdMemberRef` token.</span></span>|  
|`mdtCustomAttribute`|<span data-ttu-id="743c0-116">`mdCustomAttribute` Token.</span><span class="sxs-lookup"><span data-stu-id="743c0-116">An `mdCustomAttribute` token.</span></span>|  
|`mdtPermission`|<span data-ttu-id="743c0-117">`mdPermission` Token.</span><span class="sxs-lookup"><span data-stu-id="743c0-117">An `mdPermission` token.</span></span>|  
|`mdtSignature`|<span data-ttu-id="743c0-118">`mdSignature` Token.</span><span class="sxs-lookup"><span data-stu-id="743c0-118">An `mdSignature` token.</span></span>|  
|`mdtEvent`|<span data-ttu-id="743c0-119">`mdEvent` Token.</span><span class="sxs-lookup"><span data-stu-id="743c0-119">An `mdEvent` token.</span></span>|  
|`mdtProperty`|<span data-ttu-id="743c0-120">`mdProperty` Token.</span><span class="sxs-lookup"><span data-stu-id="743c0-120">An `mdProperty` token.</span></span>|  
|`mdtModuleRef`|<span data-ttu-id="743c0-121">`mdModuleRef` Token.</span><span class="sxs-lookup"><span data-stu-id="743c0-121">An `mdModuleRef` token.</span></span>|  
|`mdtTypeSpec`|<span data-ttu-id="743c0-122">`mdTypeSpec` Token.</span><span class="sxs-lookup"><span data-stu-id="743c0-122">An `mdTypeSpec` token.</span></span>|  
|`mdtAssembly`|<span data-ttu-id="743c0-123">`mdAssembly` Token.</span><span class="sxs-lookup"><span data-stu-id="743c0-123">An `mdAssembly` token.</span></span>|  
|`mdtAssemblyRef`|<span data-ttu-id="743c0-124">`mdAssemblyRef` Token.</span><span class="sxs-lookup"><span data-stu-id="743c0-124">An `mdAssemblyRef` token.</span></span>|  
|`mdtFile`|<span data-ttu-id="743c0-125">`mdFile` Token.</span><span class="sxs-lookup"><span data-stu-id="743c0-125">An `mdFile` token.</span></span>|  
|`mdtExportedType`|<span data-ttu-id="743c0-126">`mdExportedType` Token.</span><span class="sxs-lookup"><span data-stu-id="743c0-126">An `mdExportedType` token.</span></span>|  
|`mdtManifestResource`|<span data-ttu-id="743c0-127">`mdManifestResource` Token.</span><span class="sxs-lookup"><span data-stu-id="743c0-127">An `mdManifestResource` token.</span></span>|  
|`mdtGenericParam`|<span data-ttu-id="743c0-128">`mdGenericParam` Token.</span><span class="sxs-lookup"><span data-stu-id="743c0-128">An `mdGenericParam` token.</span></span>|  
|`mdtMethodSpec`|<span data-ttu-id="743c0-129">`mdMethodSpec` Token.</span><span class="sxs-lookup"><span data-stu-id="743c0-129">An `mdMethodSpec` token.</span></span>|  
|`mdtGenericParamConstraint`|<span data-ttu-id="743c0-130">`mdGenericParamConstraint` Token.</span><span class="sxs-lookup"><span data-stu-id="743c0-130">An `mdGenericParamConstraint` token.</span></span>|  
|`mdtString`|<span data-ttu-id="743c0-131">`mdString` Token.</span><span class="sxs-lookup"><span data-stu-id="743c0-131">An `mdString` token.</span></span>|  
|`mdtName`|<span data-ttu-id="743c0-132">`mdName` Token.</span><span class="sxs-lookup"><span data-stu-id="743c0-132">An `mdName` token.</span></span>|  
|`mdtBaseType`|<span data-ttu-id="743c0-133">Nepoužívá se.</span><span class="sxs-lookup"><span data-stu-id="743c0-133">Not used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="743c0-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="743c0-134">Remarks</span></span>  
 <span data-ttu-id="743c0-135">Každá hodnota je rovna hodnotě horní byte v odpovídající token metadat.</span><span class="sxs-lookup"><span data-stu-id="743c0-135">Each value is equal to the value of the top byte in the corresponding metadata token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="743c0-136">Požadavky</span><span class="sxs-lookup"><span data-stu-id="743c0-136">Requirements</span></span>  
 <span data-ttu-id="743c0-137">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="743c0-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="743c0-138">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="743c0-138">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="743c0-139">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="743c0-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="743c0-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="743c0-140">See also</span></span>

- [<span data-ttu-id="743c0-141">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="743c0-141">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
