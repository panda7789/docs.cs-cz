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
ms.openlocfilehash: 8cc803e3cf1442d324bf2eed0a37d0d236acd86d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493055"
---
# <a name="cor_field_offset-structure"></a><span data-ttu-id="61a60-102">COR_FIELD_OFFSET – struktura</span><span class="sxs-lookup"><span data-stu-id="61a60-102">COR_FIELD_OFFSET Structure</span></span>
<span data-ttu-id="61a60-103">Ukládá posun v rámci třídy zadaného pole.</span><span class="sxs-lookup"><span data-stu-id="61a60-103">Stores the offset, within a class, of the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61a60-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="61a60-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_FIELD_OFFSET {  
    mdFieldDef  ridOfField;  
    ULONG       ulOffset;  
} COR_FIELD_OFFSET;  
```  
  
## <a name="members"></a><span data-ttu-id="61a60-105">Členové</span><span class="sxs-lookup"><span data-stu-id="61a60-105">Members</span></span>  
  
|<span data-ttu-id="61a60-106">Člen</span><span class="sxs-lookup"><span data-stu-id="61a60-106">Member</span></span>|<span data-ttu-id="61a60-107">Description</span><span class="sxs-lookup"><span data-stu-id="61a60-107">Description</span></span>|  
|------------|-----------------|  
|`ridOfField`|<span data-ttu-id="61a60-108">`mdFieldDef`Token metadat, který představuje pole.</span><span class="sxs-lookup"><span data-stu-id="61a60-108">An `mdFieldDef` metadata token that represents the field.</span></span>|  
|`ulOffset`|<span data-ttu-id="61a60-109">Posun pole v rámci jeho třídy.</span><span class="sxs-lookup"><span data-stu-id="61a60-109">The field's offset within its class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="61a60-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="61a60-110">Remarks</span></span>  
 <span data-ttu-id="61a60-111">[IMetaDataImport:: GetClassLayout –](imetadataimport-getclasslayout-method.md) a [IMetaDataEmit:: SetClassLayout –](imetadataemit-setclasslayout-method.md) metody přebírají parametr typu `COR_FIELD_OFFSET` .</span><span class="sxs-lookup"><span data-stu-id="61a60-111">[IMetaDataImport::GetClassLayout](imetadataimport-getclasslayout-method.md) and [IMetaDataEmit::SetClassLayout](imetadataemit-setclasslayout-method.md) methods take a parameter of type `COR_FIELD_OFFSET`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61a60-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="61a60-112">Requirements</span></span>  
 <span data-ttu-id="61a60-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61a60-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61a60-114">**Hlavička:** CorHdr. h, CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="61a60-114">**Header:** CorHdr.h, CorProf.idl</span></span>  
  
 <span data-ttu-id="61a60-115">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61a60-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61a60-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="61a60-116">See also</span></span>

- [<span data-ttu-id="61a60-117">Struktury pro metadata</span><span class="sxs-lookup"><span data-stu-id="61a60-117">Metadata Structures</span></span>](metadata-structures.md)
- [<span data-ttu-id="61a60-118">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="61a60-118">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="61a60-119">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="61a60-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
