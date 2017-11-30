---
title: "COR_FIELD_OFFSET – struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_FIELD_OFFSET
api_location: mscoree.dll
api_type: COM
f1_keywords: COR_FIELD_OFFSET
helpviewer_keywords: COR_FIELD_OFFSET structure [.NET Framework metadata]
ms.assetid: cced5298-277f-4a5a-8ecf-a0050c1096ea
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8e821a9d4ffa5054f687eff7360bc8d7cefb9f09
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="corfieldoffset-structure"></a><span data-ttu-id="f9db2-102">COR_FIELD_OFFSET – struktura</span><span class="sxs-lookup"><span data-stu-id="f9db2-102">COR_FIELD_OFFSET Structure</span></span>
<span data-ttu-id="f9db2-103">Ukládá posun v rámci třídy, zadaného pole.</span><span class="sxs-lookup"><span data-stu-id="f9db2-103">Stores the offset, within a class, of the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9db2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f9db2-104">Syntax</span></span>  
  
```  
typedef struct COR_FIELD_OFFSET {  
    mdFieldDef  ridOfField;  
    ULONG       ulOffset;  
} COR_FIELD_OFFSET;  
```  
  
## <a name="members"></a><span data-ttu-id="f9db2-105">Členové</span><span class="sxs-lookup"><span data-stu-id="f9db2-105">Members</span></span>  
  
|<span data-ttu-id="f9db2-106">Člen</span><span class="sxs-lookup"><span data-stu-id="f9db2-106">Member</span></span>|<span data-ttu-id="f9db2-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f9db2-107">Description</span></span>|  
|------------|-----------------|  
|`ridOfField`|<span data-ttu-id="f9db2-108">`mdFieldDef` Metadata token, který představuje pole.</span><span class="sxs-lookup"><span data-stu-id="f9db2-108">An `mdFieldDef` metadata token that represents the field.</span></span>|  
|`ulOffset`|<span data-ttu-id="f9db2-109">Pole Posun v rámci své třídy.</span><span class="sxs-lookup"><span data-stu-id="f9db2-109">The field's offset within its class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9db2-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f9db2-110">Remarks</span></span>  
 <span data-ttu-id="f9db2-111">[Imetadataimport::getclasslayout –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) a [imetadataemit::setclasslayout –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md) metody přijímají parametr typu `COR_FIELD_OFFSET`.</span><span class="sxs-lookup"><span data-stu-id="f9db2-111">[IMetaDataImport::GetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) and [IMetaDataEmit::SetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md) methods take a parameter of type `COR_FIELD_OFFSET`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9db2-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f9db2-112">Requirements</span></span>  
 <span data-ttu-id="f9db2-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9db2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9db2-114">**Záhlaví:** CorHdr.h, CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="f9db2-114">**Header:** CorHdr.h, CorProf.idl</span></span>  
  
 <span data-ttu-id="f9db2-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9db2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9db2-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="f9db2-116">See Also</span></span>  
 [<span data-ttu-id="f9db2-117">Struktury metadat</span><span class="sxs-lookup"><span data-stu-id="f9db2-117">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
 [<span data-ttu-id="f9db2-118">Imetadataemit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f9db2-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="f9db2-119">Imetadataimport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f9db2-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
