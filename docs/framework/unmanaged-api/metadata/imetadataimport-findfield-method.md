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
ms.openlocfilehash: 4a6f2e428366d2fe96313879ef1256d7b86ddd29
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57490408"
---
# <a name="imetadataimportfindfield-method"></a><span data-ttu-id="b08c7-102">IMetaDataImport::FindField – metoda</span><span class="sxs-lookup"><span data-stu-id="b08c7-102">IMetaDataImport::FindField Method</span></span>
<span data-ttu-id="b08c7-103">Získá ukazatel FieldDef token pro pole, který je uzavřen parametrem <xref:System.Type> a, který má zadaný název a metadata podpis.</span><span class="sxs-lookup"><span data-stu-id="b08c7-103">Gets a pointer to the FieldDef token for the field that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b08c7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b08c7-104">Syntax</span></span>  
  
```  
HRESULT FindField (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,  
   [in]  PCCOR_SIGNATURE   pvSigBlob,  
   [in]  ULONG             cbSigBlob,  
   [out] mdFieldDef        *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b08c7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b08c7-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="b08c7-106">[in] Token TypeDef pro třídu nebo rozhraní, který obklopuje pole pro hledání.</span><span class="sxs-lookup"><span data-stu-id="b08c7-106">[in] The TypeDef token for the class or interface that encloses the field to search for.</span></span> <span data-ttu-id="b08c7-107">Pokud je tato hodnota `mdTokenNil`, vyhledávání se provádí pro globální proměnné.</span><span class="sxs-lookup"><span data-stu-id="b08c7-107">If this value is `mdTokenNil`, the lookup is done for a global variable.</span></span>  
  
 `szName`  
 <span data-ttu-id="b08c7-108">[in] Název pole, které chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="b08c7-108">[in] The name of the field to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="b08c7-109">[in] Ukazatel na binární metadat podpis pole.</span><span class="sxs-lookup"><span data-stu-id="b08c7-109">[in] A pointer to the binary metadata signature of the field.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="b08c7-110">[in] Velikost v bajtech `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="b08c7-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="b08c7-111">[out] Ukazatel na odpovídající token FieldDef.</span><span class="sxs-lookup"><span data-stu-id="b08c7-111">[out] A pointer to the matching FieldDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b08c7-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b08c7-112">Remarks</span></span>  
 <span data-ttu-id="b08c7-113">Zadejte pole pomocí jeho nadřazené třídu nebo rozhraní (`td`), jeho název (`szName`) a volitelně jeho podpis (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="b08c7-113">You specify the field using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="b08c7-114">Podpis předán `FindField` musí byly vytvořeny v aktuálním oboru, protože podpisy jsou vázány na určitém rozsahu.</span><span class="sxs-lookup"><span data-stu-id="b08c7-114">The signature passed to `FindField` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="b08c7-115">Podpis můžete vložit token, který identifikuje nadřazeného class nebo hodnotového typu.</span><span class="sxs-lookup"><span data-stu-id="b08c7-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="b08c7-116">(Token je index do místní tabulky TypeDef).</span><span class="sxs-lookup"><span data-stu-id="b08c7-116">(The token is an index into the local TypeDef table).</span></span> <span data-ttu-id="b08c7-117">Nelze sestavit podpis za běhu mimo kontext aktuálního oboru a použít tento podpis jako vstup pro `FindField`.</span><span class="sxs-lookup"><span data-stu-id="b08c7-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindField`.</span></span>  
  
 <span data-ttu-id="b08c7-118">`FindField` Vyhledá pouze pole, které byly definovány přímo v dané třídy nebo rozhraní; Nelze najít zděděného pole.</span><span class="sxs-lookup"><span data-stu-id="b08c7-118">`FindField` finds only fields that were defined directly in the class or interface; it does not find inherited fields.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b08c7-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b08c7-119">Requirements</span></span>  
 <span data-ttu-id="b08c7-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b08c7-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b08c7-121">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b08c7-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b08c7-122">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b08c7-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b08c7-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b08c7-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b08c7-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b08c7-124">See also</span></span>
- [<span data-ttu-id="b08c7-125">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b08c7-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="b08c7-126">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b08c7-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
