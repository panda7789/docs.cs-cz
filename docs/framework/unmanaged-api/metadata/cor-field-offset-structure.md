---
title: COR_FIELD_OFFSET – struktura
ms.date: 03/30/2017
api_name:
- COR_FIELD_OFFSET
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_FIELD_OFFSET
helpviewer_keywords:
- COR_FIELD_OFFSET structure [.NET Framework metadata]
ms.assetid: cced5298-277f-4a5a-8ecf-a0050c1096ea
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8c4a5c8efc87940b7df0bfd532beaa67931a8c81
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442115"
---
# <a name="corfieldoffset-structure"></a><span data-ttu-id="caa32-102">COR_FIELD_OFFSET – struktura</span><span class="sxs-lookup"><span data-stu-id="caa32-102">COR_FIELD_OFFSET Structure</span></span>
<span data-ttu-id="caa32-103">Ukládá posun v rámci třídy, zadaného pole.</span><span class="sxs-lookup"><span data-stu-id="caa32-103">Stores the offset, within a class, of the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="caa32-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="caa32-104">Syntax</span></span>  
  
```  
typedef struct COR_FIELD_OFFSET {  
    mdFieldDef  ridOfField;  
    ULONG       ulOffset;  
} COR_FIELD_OFFSET;  
```  
  
## <a name="members"></a><span data-ttu-id="caa32-105">Členové</span><span class="sxs-lookup"><span data-stu-id="caa32-105">Members</span></span>  
  
|<span data-ttu-id="caa32-106">Člen</span><span class="sxs-lookup"><span data-stu-id="caa32-106">Member</span></span>|<span data-ttu-id="caa32-107">Popis</span><span class="sxs-lookup"><span data-stu-id="caa32-107">Description</span></span>|  
|------------|-----------------|  
|`ridOfField`|<span data-ttu-id="caa32-108">`mdFieldDef` Metadata token, který představuje pole.</span><span class="sxs-lookup"><span data-stu-id="caa32-108">An `mdFieldDef` metadata token that represents the field.</span></span>|  
|`ulOffset`|<span data-ttu-id="caa32-109">Pole Posun v rámci své třídy.</span><span class="sxs-lookup"><span data-stu-id="caa32-109">The field's offset within its class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="caa32-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="caa32-110">Remarks</span></span>  
 <span data-ttu-id="caa32-111">[Imetadataimport::getclasslayout –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) a [imetadataemit::setclasslayout –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md) metody přijímají parametr typu `COR_FIELD_OFFSET`.</span><span class="sxs-lookup"><span data-stu-id="caa32-111">[IMetaDataImport::GetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) and [IMetaDataEmit::SetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md) methods take a parameter of type `COR_FIELD_OFFSET`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="caa32-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="caa32-112">Requirements</span></span>  
 <span data-ttu-id="caa32-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="caa32-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="caa32-114">**Záhlaví:** CorHdr.h, CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="caa32-114">**Header:** CorHdr.h, CorProf.idl</span></span>  
  
 <span data-ttu-id="caa32-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="caa32-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caa32-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="caa32-116">See Also</span></span>  
 [<span data-ttu-id="caa32-117">Struktury pro metadata</span><span class="sxs-lookup"><span data-stu-id="caa32-117">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
 [<span data-ttu-id="caa32-118">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="caa32-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="caa32-119">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="caa32-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
