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
ms.openlocfilehash: 646952d5cd55b74081a0ba6171a6eee6b0138512
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443960"
---
# <a name="cor_field_offset-structure"></a><span data-ttu-id="336ba-102">COR_FIELD_OFFSET – struktura</span><span class="sxs-lookup"><span data-stu-id="336ba-102">COR_FIELD_OFFSET Structure</span></span>
<span data-ttu-id="336ba-103">Ukládá posun v rámci třídy zadaného pole.</span><span class="sxs-lookup"><span data-stu-id="336ba-103">Stores the offset, within a class, of the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="336ba-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="336ba-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_FIELD_OFFSET {  
    mdFieldDef  ridOfField;  
    ULONG       ulOffset;  
} COR_FIELD_OFFSET;  
```  
  
## <a name="members"></a><span data-ttu-id="336ba-105">Členové</span><span class="sxs-lookup"><span data-stu-id="336ba-105">Members</span></span>  
  
|<span data-ttu-id="336ba-106">Člen</span><span class="sxs-lookup"><span data-stu-id="336ba-106">Member</span></span>|<span data-ttu-id="336ba-107">Popis</span><span class="sxs-lookup"><span data-stu-id="336ba-107">Description</span></span>|  
|------------|-----------------|  
|`ridOfField`|<span data-ttu-id="336ba-108">Token metadat `mdFieldDef`, který představuje pole.</span><span class="sxs-lookup"><span data-stu-id="336ba-108">An `mdFieldDef` metadata token that represents the field.</span></span>|  
|`ulOffset`|<span data-ttu-id="336ba-109">Posun pole v rámci jeho třídy.</span><span class="sxs-lookup"><span data-stu-id="336ba-109">The field's offset within its class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="336ba-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="336ba-110">Remarks</span></span>  
 <span data-ttu-id="336ba-111">[IMetaDataImport:: GetClassLayout –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) a [IMetaDataEmit:: SetClassLayout –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md) metody přebírají parametr typu `COR_FIELD_OFFSET`.</span><span class="sxs-lookup"><span data-stu-id="336ba-111">[IMetaDataImport::GetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) and [IMetaDataEmit::SetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md) methods take a parameter of type `COR_FIELD_OFFSET`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="336ba-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="336ba-112">Requirements</span></span>  
 <span data-ttu-id="336ba-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="336ba-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="336ba-114">**Hlavička:** CorHdr. h, CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="336ba-114">**Header:** CorHdr.h, CorProf.idl</span></span>  
  
 <span data-ttu-id="336ba-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="336ba-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="336ba-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="336ba-116">See also</span></span>

- [<span data-ttu-id="336ba-117">Struktury pro metadata</span><span class="sxs-lookup"><span data-stu-id="336ba-117">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="336ba-118">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="336ba-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="336ba-119">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="336ba-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
