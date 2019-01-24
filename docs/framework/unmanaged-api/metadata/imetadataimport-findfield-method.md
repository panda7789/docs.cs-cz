---
title: IMetaDataImport::FindField – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b07d75b6a8839f9a223ef2c0be52830e107e4088
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527598"
---
# <a name="imetadataimportfindfield-method"></a><span data-ttu-id="c26d0-102">IMetaDataImport::FindField – metoda</span><span class="sxs-lookup"><span data-stu-id="c26d0-102">IMetaDataImport::FindField Method</span></span>
<span data-ttu-id="c26d0-103">Získá ukazatel FieldDef token pro pole, který je uzavřen parametrem <xref:System.Type> a, který má zadaný název a metadata podpis.</span><span class="sxs-lookup"><span data-stu-id="c26d0-103">Gets a pointer to the FieldDef token for the field that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c26d0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c26d0-104">Syntax</span></span>  
  
```  
HRESULT FindField (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,  
   [in]  PCCOR_SIGNATURE   pvSigBlob,  
   [in]  ULONG             cbSigBlob,  
   [out] mdFieldDef        *pmb  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c26d0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c26d0-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="c26d0-106">[in] Token TypeDef pro třídu nebo rozhraní, který obklopuje pole pro hledání.</span><span class="sxs-lookup"><span data-stu-id="c26d0-106">[in] The TypeDef token for the class or interface that encloses the field to search for.</span></span> <span data-ttu-id="c26d0-107">Pokud je tato hodnota `mdTokenNil`, vyhledávání se provádí pro globální proměnné.</span><span class="sxs-lookup"><span data-stu-id="c26d0-107">If this value is `mdTokenNil`, the lookup is done for a global variable.</span></span>  
  
 `szName`  
 <span data-ttu-id="c26d0-108">[in] Název pole, které chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="c26d0-108">[in] The name of the field to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="c26d0-109">[in] Ukazatel na binární metadat podpis pole.</span><span class="sxs-lookup"><span data-stu-id="c26d0-109">[in] A pointer to the binary metadata signature of the field.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="c26d0-110">[in] Velikost v bajtech `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="c26d0-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="c26d0-111">[out] Ukazatel na odpovídající token FieldDef.</span><span class="sxs-lookup"><span data-stu-id="c26d0-111">[out] A pointer to the matching FieldDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c26d0-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c26d0-112">Remarks</span></span>  
 <span data-ttu-id="c26d0-113">Zadejte pole pomocí jeho nadřazené třídu nebo rozhraní (`td`), jeho název (`szName`) a volitelně jeho podpis (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="c26d0-113">You specify the field using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="c26d0-114">Podpis předán `FindField` musí byly vytvořeny v aktuálním oboru, protože podpisy jsou vázány na určitém rozsahu.</span><span class="sxs-lookup"><span data-stu-id="c26d0-114">The signature passed to `FindField` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="c26d0-115">Podpis můžete vložit token, který identifikuje nadřazeného class nebo hodnotového typu.</span><span class="sxs-lookup"><span data-stu-id="c26d0-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="c26d0-116">(Token je index do místní tabulky TypeDef).</span><span class="sxs-lookup"><span data-stu-id="c26d0-116">(The token is an index into the local TypeDef table).</span></span> <span data-ttu-id="c26d0-117">Nelze sestavit podpis za běhu mimo kontext aktuálního oboru a použít tento podpis jako vstup pro `FindField`.</span><span class="sxs-lookup"><span data-stu-id="c26d0-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindField`.</span></span>  
  
 <span data-ttu-id="c26d0-118">`FindField` Vyhledá pouze pole, které byly definovány přímo v dané třídy nebo rozhraní; Nelze najít zděděného pole.</span><span class="sxs-lookup"><span data-stu-id="c26d0-118">`FindField` finds only fields that were defined directly in the class or interface; it does not find inherited fields.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c26d0-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c26d0-119">Requirements</span></span>  
 <span data-ttu-id="c26d0-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c26d0-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c26d0-121">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c26d0-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c26d0-122">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c26d0-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c26d0-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c26d0-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c26d0-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c26d0-124">See also</span></span>
- [<span data-ttu-id="c26d0-125">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c26d0-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="c26d0-126">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c26d0-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
