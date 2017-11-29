---
title: "IMetaDataImport::GetMethodSemantics – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetMethodSemantics
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetMethodSemantics
helpviewer_keywords:
- GetMethodSemantics method [.NET Framework metadata]
- IMetaDataImport::GetMethodSemantics method [.NET Framework metadata]
ms.assetid: 5e018eaa-d60e-4a0b-a2c5-8c36bd09d905
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f15aedb74fd7322031d213c5229f65d70f7cb771
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetmethodsemantics-method"></a><span data-ttu-id="d6145-102">IMetaDataImport::GetMethodSemantics – metoda</span><span class="sxs-lookup"><span data-stu-id="d6145-102">IMetaDataImport::GetMethodSemantics Method</span></span>
<span data-ttu-id="d6145-103">Získá příznaky udávající vztah mezi metoda odkazuje zadaný token MethodDef a spárované vlastnosti a události odkazuje zadaný EventProp token.</span><span class="sxs-lookup"><span data-stu-id="d6145-103">Gets flags indicating the relationship between the method referenced by the specified MethodDef token and the paired property and event referenced by the specified EventProp token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6145-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6145-104">Syntax</span></span>  
  
```  
HRESULT GetMethodSemantics (  
   [in]  mdMethodDef   mb,  
   [in]  mdToken       tkEventProp,  
   [out] DWORD         *pdwSemanticsFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d6145-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d6145-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="d6145-106">[v] MethodDef token představující metodu k získání informací sémantického role pro.</span><span class="sxs-lookup"><span data-stu-id="d6145-106">[in] A MethodDef token representing the method to get the semantic role information for.</span></span>  
  
 `tkEventProp`  
 <span data-ttu-id="d6145-107">[v] Token představující spárované vlastností a událostí, pro které chcete získat role metody.</span><span class="sxs-lookup"><span data-stu-id="d6145-107">[in] A token representing the paired property and event for which to get the method's role.</span></span>  
  
 `pdwSemanticsFlags`  
 <span data-ttu-id="d6145-108">[out] Ukazatel na přidružené sémantiku příznaků.</span><span class="sxs-lookup"><span data-stu-id="d6145-108">[out] A pointer to the associated semantics flags.</span></span> <span data-ttu-id="d6145-109">Tato hodnota je bitová maska z [CorMethodSemanticsAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="d6145-109">This value is a bitmask from the [CorMethodSemanticsAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6145-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d6145-110">Remarks</span></span>  
 <span data-ttu-id="d6145-111">[Imetadataemit::defineproperty –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) metoda nastaví příznaky sémantiku metoda.</span><span class="sxs-lookup"><span data-stu-id="d6145-111">The [IMetaDataEmit::DefineProperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) method sets a method's semantics flags.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6145-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d6145-112">Requirements</span></span>  
 <span data-ttu-id="d6145-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6145-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6145-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d6145-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d6145-115">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d6145-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d6145-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6145-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6145-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="d6145-117">See Also</span></span>  
 [<span data-ttu-id="d6145-118">Imetadataimport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d6145-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="d6145-119">Imetadataimport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d6145-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
