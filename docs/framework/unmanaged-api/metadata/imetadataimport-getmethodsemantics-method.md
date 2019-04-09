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
ms.openlocfilehash: 57ddbd8c6935f2c0275c132e30ea175c6f198fac
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59200087"
---
# <a name="imetadataimportgetmethodsemantics-method"></a><span data-ttu-id="6b098-102">IMetaDataImport::GetMethodSemantics – metoda</span><span class="sxs-lookup"><span data-stu-id="6b098-102">IMetaDataImport::GetMethodSemantics Method</span></span>
<span data-ttu-id="6b098-103">Získá příznaky, která označuje vztah mezi metodou odkazuje zadaný token MethodDef a spárované vlastnosti a události odkazuje zadaný EventProp token.</span><span class="sxs-lookup"><span data-stu-id="6b098-103">Gets flags indicating the relationship between the method referenced by the specified MethodDef token and the paired property and event referenced by the specified EventProp token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b098-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6b098-104">Syntax</span></span>  
  
```  
HRESULT GetMethodSemantics (  
   [in]  mdMethodDef   mb,  
   [in]  mdToken       tkEventProp,  
   [out] DWORD         *pdwSemanticsFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b098-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6b098-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="6b098-106">[in] Token MethodDef představující metodu k získání informací o sémantických rolích.</span><span class="sxs-lookup"><span data-stu-id="6b098-106">[in] A MethodDef token representing the method to get the semantic role information for.</span></span>  
  
 `tkEventProp`  
 <span data-ttu-id="6b098-107">[in] Token představující spárované vlastnosti a události, pro který má být získána metody role.</span><span class="sxs-lookup"><span data-stu-id="6b098-107">[in] A token representing the paired property and event for which to get the method's role.</span></span>  
  
 `pdwSemanticsFlags`  
 <span data-ttu-id="6b098-108">[out] Ukazatel na příznaky přidružené sémantiku.</span><span class="sxs-lookup"><span data-stu-id="6b098-108">[out] A pointer to the associated semantics flags.</span></span> <span data-ttu-id="6b098-109">Tato hodnota je bitová maska z [cormethodsemanticsattr –](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="6b098-109">This value is a bitmask from the [CorMethodSemanticsAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b098-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6b098-110">Remarks</span></span>  
 <span data-ttu-id="6b098-111">[Imetadataemit::defineproperty –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) metoda nastavuje příznaky sémantiku metody.</span><span class="sxs-lookup"><span data-stu-id="6b098-111">The [IMetaDataEmit::DefineProperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) method sets a method's semantics flags.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b098-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6b098-112">Requirements</span></span>  
 <span data-ttu-id="6b098-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b098-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b098-114">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6b098-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6b098-115">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6b098-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="6b098-116">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="6b098-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6b098-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6b098-117">See also</span></span>

- [<span data-ttu-id="6b098-118">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6b098-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="6b098-119">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6b098-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
