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
ms.openlocfilehash: 820c99de1bdb108a24203a3438b1709ca54490b7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59078119"
---
# <a name="corfieldoffset-structure"></a><span data-ttu-id="f9dbc-102">COR_FIELD_OFFSET – struktura</span><span class="sxs-lookup"><span data-stu-id="f9dbc-102">COR_FIELD_OFFSET Structure</span></span>
<span data-ttu-id="f9dbc-103">Ukládá posun v rámci třídy, zadaného pole.</span><span class="sxs-lookup"><span data-stu-id="f9dbc-103">Stores the offset, within a class, of the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9dbc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f9dbc-104">Syntax</span></span>  
  
```  
typedef struct COR_FIELD_OFFSET {  
    mdFieldDef  ridOfField;  
    ULONG       ulOffset;  
} COR_FIELD_OFFSET;  
```  
  
## <a name="members"></a><span data-ttu-id="f9dbc-105">Členové</span><span class="sxs-lookup"><span data-stu-id="f9dbc-105">Members</span></span>  
  
|<span data-ttu-id="f9dbc-106">Člen</span><span class="sxs-lookup"><span data-stu-id="f9dbc-106">Member</span></span>|<span data-ttu-id="f9dbc-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f9dbc-107">Description</span></span>|  
|------------|-----------------|  
|`ridOfField`|<span data-ttu-id="f9dbc-108">`mdFieldDef` Token metadat, který představuje pole.</span><span class="sxs-lookup"><span data-stu-id="f9dbc-108">An `mdFieldDef` metadata token that represents the field.</span></span>|  
|`ulOffset`|<span data-ttu-id="f9dbc-109">Pole Posun v rámci své třídy.</span><span class="sxs-lookup"><span data-stu-id="f9dbc-109">The field's offset within its class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9dbc-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f9dbc-110">Remarks</span></span>  
 <span data-ttu-id="f9dbc-111">[Imetadataimport::getclasslayout –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) a [imetadataemit::setclasslayout –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md) metody přijímají parametr typu `COR_FIELD_OFFSET`.</span><span class="sxs-lookup"><span data-stu-id="f9dbc-111">[IMetaDataImport::GetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) and [IMetaDataEmit::SetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md) methods take a parameter of type `COR_FIELD_OFFSET`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9dbc-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f9dbc-112">Requirements</span></span>  
 <span data-ttu-id="f9dbc-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9dbc-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9dbc-114">**Záhlaví:** CorHdr.h, CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="f9dbc-114">**Header:** CorHdr.h, CorProf.idl</span></span>  
  
 **<span data-ttu-id="f9dbc-115">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="f9dbc-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f9dbc-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f9dbc-116">See also</span></span>

- [<span data-ttu-id="f9dbc-117">Struktury metadat</span><span class="sxs-lookup"><span data-stu-id="f9dbc-117">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="f9dbc-118">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f9dbc-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="f9dbc-119">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f9dbc-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
