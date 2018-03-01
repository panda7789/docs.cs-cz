---
title: "IMetaDataImport::FindField – metoda"
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
- IMetaDataImport.FindField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindField
helpviewer_keywords:
- IMetaDataImport::FindField method [.NET Framework metadata]
- FindField method [.NET Framework metadata]
ms.assetid: 38cd4e16-fbb2-471c-aa73-ac51a1931ad2
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3178d3ff3c64de5390e1150445f0c49c560aa32a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportfindfield-method"></a><span data-ttu-id="b232c-102">IMetaDataImport::FindField – metoda</span><span class="sxs-lookup"><span data-stu-id="b232c-102">IMetaDataImport::FindField Method</span></span>
<span data-ttu-id="b232c-103">Získá ukazatel na FieldDef token pole, která je uzavřena k zadanému <xref:System.Type> a má zadaný název a metadata podpis.</span><span class="sxs-lookup"><span data-stu-id="b232c-103">Gets a pointer to the FieldDef token for the field that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b232c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b232c-104">Syntax</span></span>  
  
```  
HRESULT FindField (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,  
   [in]  PCCOR_SIGNATURE   pvSigBlob,  
   [in]  ULONG             cbSigBlob,  
   [out] mdFieldDef        *pmb  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b232c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b232c-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="b232c-106">[v] Token TypeDef pro třídy nebo rozhraní, která obklopuje pole pro vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="b232c-106">[in] The TypeDef token for the class or interface that encloses the field to search for.</span></span> <span data-ttu-id="b232c-107">Pokud je tato hodnota `mdTokenNil`, globální proměnné se provádí vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="b232c-107">If this value is `mdTokenNil`, the lookup is done for a global variable.</span></span>  
  
 `szName`  
 <span data-ttu-id="b232c-108">[v] Název pole, které chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="b232c-108">[in] The name of the field to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="b232c-109">[v] Ukazatel na binární metadata podpis pole.</span><span class="sxs-lookup"><span data-stu-id="b232c-109">[in] A pointer to the binary metadata signature of the field.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="b232c-110">[v] Velikost v bajtech `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="b232c-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="b232c-111">[out] Ukazatel na odpovídající FieldDef token.</span><span class="sxs-lookup"><span data-stu-id="b232c-111">[out] A pointer to the matching FieldDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b232c-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b232c-112">Remarks</span></span>  
 <span data-ttu-id="b232c-113">Zadejte pole, které používá jeho nadřazených třídy nebo rozhraní (`td`), jeho název (`szName`) a volitelně jeho podpis (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="b232c-113">You specify the field using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="b232c-114">Podpis předaný `FindField` musí být vygenerováno v aktuálním oboru, protože podpis je vázána na konkrétní rozsah.</span><span class="sxs-lookup"><span data-stu-id="b232c-114">The signature passed to `FindField` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="b232c-115">Podpis můžete vložit token, který identifikuje nadřazeného typu třídy nebo hodnota.</span><span class="sxs-lookup"><span data-stu-id="b232c-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="b232c-116">(Token je index do místní tabulky TypeDef).</span><span class="sxs-lookup"><span data-stu-id="b232c-116">(The token is an index into the local TypeDef table).</span></span> <span data-ttu-id="b232c-117">Nelze vytvořit podpis běhu mimo kontext aktuálního oboru a použít jako vstup pro tento podpis `FindField`.</span><span class="sxs-lookup"><span data-stu-id="b232c-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindField`.</span></span>  
  
 <span data-ttu-id="b232c-118">`FindField`Vyhledá pouze pole, které byly definovány přímo v třídy nebo rozhraní; zděděné pole nenajde.</span><span class="sxs-lookup"><span data-stu-id="b232c-118">`FindField` finds only fields that were defined directly in the class or interface; it does not find inherited fields.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b232c-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b232c-119">Requirements</span></span>  
 <span data-ttu-id="b232c-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b232c-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b232c-121">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b232c-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b232c-122">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b232c-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b232c-123">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b232c-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b232c-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="b232c-124">See Also</span></span>  
 [<span data-ttu-id="b232c-125">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b232c-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="b232c-126">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b232c-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
