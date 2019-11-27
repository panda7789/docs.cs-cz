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
ms.openlocfilehash: 0542c518b64764ad27aa00b8d595be1191059436
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437457"
---
# <a name="imetadataimportgetmethodsemantics-method"></a><span data-ttu-id="22765-102">IMetaDataImport::GetMethodSemantics – metoda</span><span class="sxs-lookup"><span data-stu-id="22765-102">IMetaDataImport::GetMethodSemantics Method</span></span>
<span data-ttu-id="22765-103">Získá příznaky označující vztah mezi metodou, na kterou se odkazuje zadaný token MethodDef, a spárovanými vlastnostmi a událostmi, na které odkazuje zadaný EventProp token.</span><span class="sxs-lookup"><span data-stu-id="22765-103">Gets flags indicating the relationship between the method referenced by the specified MethodDef token and the paired property and event referenced by the specified EventProp token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22765-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22765-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodSemantics (  
   [in]  mdMethodDef   mb,  
   [in]  mdToken       tkEventProp,  
   [out] DWORD         *pdwSemanticsFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22765-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="22765-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="22765-106">pro Token MethodDef reprezentující metodu pro získání informací o sémantické roli pro.</span><span class="sxs-lookup"><span data-stu-id="22765-106">[in] A MethodDef token representing the method to get the semantic role information for.</span></span>  
  
 `tkEventProp`  
 <span data-ttu-id="22765-107">pro Token představující spárovánou vlastnost a událost, pro kterou má být získána role metody.</span><span class="sxs-lookup"><span data-stu-id="22765-107">[in] A token representing the paired property and event for which to get the method's role.</span></span>  
  
 `pdwSemanticsFlags`  
 <span data-ttu-id="22765-108">mimo Ukazatel na přidružené sémantické příznaky.</span><span class="sxs-lookup"><span data-stu-id="22765-108">[out] A pointer to the associated semantics flags.</span></span> <span data-ttu-id="22765-109">Tato hodnota je Bitová maska z výčtu [CorMethodSemanticsAttr –](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="22765-109">This value is a bitmask from the [CorMethodSemanticsAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22765-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="22765-110">Remarks</span></span>  
 <span data-ttu-id="22765-111">Metoda [IMetaDataEmit::D efineproperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) nastaví příznaky sémantiky metody.</span><span class="sxs-lookup"><span data-stu-id="22765-111">The [IMetaDataEmit::DefineProperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) method sets a method's semantics flags.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22765-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="22765-112">Requirements</span></span>  
 <span data-ttu-id="22765-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22765-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22765-114">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="22765-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="22765-115">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="22765-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="22765-116">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22765-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22765-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="22765-117">See also</span></span>

- [<span data-ttu-id="22765-118">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="22765-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="22765-119">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="22765-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
