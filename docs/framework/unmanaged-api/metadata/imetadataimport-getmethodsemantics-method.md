---
title: "IMetaDataImport::GetMethodSemantics – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8f8921c4f6a676c9647d4e8907a22f0d68b0b359
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetmethodsemantics-method"></a><span data-ttu-id="cb13b-102">IMetaDataImport::GetMethodSemantics – metoda</span><span class="sxs-lookup"><span data-stu-id="cb13b-102">IMetaDataImport::GetMethodSemantics Method</span></span>
<span data-ttu-id="cb13b-103">Získá příznaky udávající vztah mezi metoda odkazuje zadaný token MethodDef a spárované vlastnosti a události odkazuje zadaný EventProp token.</span><span class="sxs-lookup"><span data-stu-id="cb13b-103">Gets flags indicating the relationship between the method referenced by the specified MethodDef token and the paired property and event referenced by the specified EventProp token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb13b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cb13b-104">Syntax</span></span>  
  
```  
HRESULT GetMethodSemantics (  
   [in]  mdMethodDef   mb,  
   [in]  mdToken       tkEventProp,  
   [out] DWORD         *pdwSemanticsFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cb13b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cb13b-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="cb13b-106">[v] MethodDef token představující metodu k získání informací sémantického role pro.</span><span class="sxs-lookup"><span data-stu-id="cb13b-106">[in] A MethodDef token representing the method to get the semantic role information for.</span></span>  
  
 `tkEventProp`  
 <span data-ttu-id="cb13b-107">[v] Token představující spárované vlastností a událostí, pro které chcete získat role metody.</span><span class="sxs-lookup"><span data-stu-id="cb13b-107">[in] A token representing the paired property and event for which to get the method's role.</span></span>  
  
 `pdwSemanticsFlags`  
 <span data-ttu-id="cb13b-108">[out] Ukazatel na přidružené sémantiku příznaků.</span><span class="sxs-lookup"><span data-stu-id="cb13b-108">[out] A pointer to the associated semantics flags.</span></span> <span data-ttu-id="cb13b-109">Tato hodnota je bitová maska z [CorMethodSemanticsAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="cb13b-109">This value is a bitmask from the [CorMethodSemanticsAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb13b-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cb13b-110">Remarks</span></span>  
 <span data-ttu-id="cb13b-111">[Imetadataemit::defineproperty –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) metoda nastaví příznaky sémantiku metoda.</span><span class="sxs-lookup"><span data-stu-id="cb13b-111">The [IMetaDataEmit::DefineProperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) method sets a method's semantics flags.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb13b-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cb13b-112">Requirements</span></span>  
 <span data-ttu-id="cb13b-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb13b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb13b-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cb13b-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cb13b-115">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cb13b-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cb13b-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb13b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb13b-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="cb13b-117">See Also</span></span>  
 [<span data-ttu-id="cb13b-118">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cb13b-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="cb13b-119">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cb13b-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
