---
title: IMetaDataImport::GetMethodSemantics – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMethodSemantics
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMethodSemantics
helpviewer_keywords:
- GetMethodSemantics method [.NET Framework metadata]
- IMetaDataImport::GetMethodSemantics method [.NET Framework metadata]
ms.assetid: 5e018eaa-d60e-4a0b-a2c5-8c36bd09d905
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a12310f1281da99706589894a4793c2a28c5b938
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745966"
---
# <a name="imetadataimportgetmethodsemantics-method"></a><span data-ttu-id="255f6-102">IMetaDataImport::GetMethodSemantics – metoda</span><span class="sxs-lookup"><span data-stu-id="255f6-102">IMetaDataImport::GetMethodSemantics Method</span></span>
<span data-ttu-id="255f6-103">Získá příznaky, která označuje vztah mezi metodou odkazuje zadaný token MethodDef a spárované vlastnosti a události odkazuje zadaný EventProp token.</span><span class="sxs-lookup"><span data-stu-id="255f6-103">Gets flags indicating the relationship between the method referenced by the specified MethodDef token and the paired property and event referenced by the specified EventProp token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="255f6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="255f6-104">Syntax</span></span>  
  
```  
HRESULT GetMethodSemantics (  
   [in]  mdMethodDef   mb,  
   [in]  mdToken       tkEventProp,  
   [out] DWORD         *pdwSemanticsFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="255f6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="255f6-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="255f6-106">[in] Token MethodDef představující metodu k získání informací o sémantických rolích.</span><span class="sxs-lookup"><span data-stu-id="255f6-106">[in] A MethodDef token representing the method to get the semantic role information for.</span></span>  
  
 `tkEventProp`  
 <span data-ttu-id="255f6-107">[in] Token představující spárované vlastnosti a události, pro který má být získána metody role.</span><span class="sxs-lookup"><span data-stu-id="255f6-107">[in] A token representing the paired property and event for which to get the method's role.</span></span>  
  
 `pdwSemanticsFlags`  
 <span data-ttu-id="255f6-108">[out] Ukazatel na příznaky přidružené sémantiku.</span><span class="sxs-lookup"><span data-stu-id="255f6-108">[out] A pointer to the associated semantics flags.</span></span> <span data-ttu-id="255f6-109">Tato hodnota je bitová maska z [cormethodsemanticsattr –](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="255f6-109">This value is a bitmask from the [CorMethodSemanticsAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="255f6-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="255f6-110">Remarks</span></span>  
 <span data-ttu-id="255f6-111">[Imetadataemit::defineproperty –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) metoda nastavuje příznaky sémantiku metody.</span><span class="sxs-lookup"><span data-stu-id="255f6-111">The [IMetaDataEmit::DefineProperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) method sets a method's semantics flags.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="255f6-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="255f6-112">Requirements</span></span>  
 <span data-ttu-id="255f6-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="255f6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="255f6-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="255f6-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="255f6-115">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="255f6-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="255f6-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="255f6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="255f6-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="255f6-117">See also</span></span>
- [<span data-ttu-id="255f6-118">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="255f6-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="255f6-119">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="255f6-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
