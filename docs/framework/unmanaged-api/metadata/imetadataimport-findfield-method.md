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
ms.openlocfilehash: 88cd08b4290739808079bc8ecb713a5c5ea96584
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59172559"
---
# <a name="imetadataimportfindfield-method"></a><span data-ttu-id="3300d-102">IMetaDataImport::FindField – metoda</span><span class="sxs-lookup"><span data-stu-id="3300d-102">IMetaDataImport::FindField Method</span></span>
<span data-ttu-id="3300d-103">Získá ukazatel FieldDef token pro pole, který je uzavřen parametrem <xref:System.Type> a, který má zadaný název a metadata podpis.</span><span class="sxs-lookup"><span data-stu-id="3300d-103">Gets a pointer to the FieldDef token for the field that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3300d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3300d-104">Syntax</span></span>  
  
```  
HRESULT FindField (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,  
   [in]  PCCOR_SIGNATURE   pvSigBlob,  
   [in]  ULONG             cbSigBlob,  
   [out] mdFieldDef        *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3300d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3300d-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="3300d-106">[in] Token TypeDef pro třídu nebo rozhraní, který obklopuje pole pro hledání.</span><span class="sxs-lookup"><span data-stu-id="3300d-106">[in] The TypeDef token for the class or interface that encloses the field to search for.</span></span> <span data-ttu-id="3300d-107">Pokud je tato hodnota `mdTokenNil`, vyhledávání se provádí pro globální proměnné.</span><span class="sxs-lookup"><span data-stu-id="3300d-107">If this value is `mdTokenNil`, the lookup is done for a global variable.</span></span>  
  
 `szName`  
 <span data-ttu-id="3300d-108">[in] Název pole, které chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="3300d-108">[in] The name of the field to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="3300d-109">[in] Ukazatel na binární metadat podpis pole.</span><span class="sxs-lookup"><span data-stu-id="3300d-109">[in] A pointer to the binary metadata signature of the field.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="3300d-110">[in] Velikost v bajtech `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="3300d-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="3300d-111">[out] Ukazatel na odpovídající token FieldDef.</span><span class="sxs-lookup"><span data-stu-id="3300d-111">[out] A pointer to the matching FieldDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3300d-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3300d-112">Remarks</span></span>  
 <span data-ttu-id="3300d-113">Zadejte pole pomocí jeho nadřazené třídu nebo rozhraní (`td`), jeho název (`szName`) a volitelně jeho podpis (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="3300d-113">You specify the field using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="3300d-114">Podpis předán `FindField` musí byly vytvořeny v aktuálním oboru, protože podpisy jsou vázány na určitém rozsahu.</span><span class="sxs-lookup"><span data-stu-id="3300d-114">The signature passed to `FindField` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="3300d-115">Podpis můžete vložit token, který identifikuje nadřazeného class nebo hodnotového typu.</span><span class="sxs-lookup"><span data-stu-id="3300d-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="3300d-116">(Token je index do místní tabulky TypeDef).</span><span class="sxs-lookup"><span data-stu-id="3300d-116">(The token is an index into the local TypeDef table).</span></span> <span data-ttu-id="3300d-117">Nelze sestavit podpis za běhu mimo kontext aktuálního oboru a použít tento podpis jako vstup pro `FindField`.</span><span class="sxs-lookup"><span data-stu-id="3300d-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindField`.</span></span>  
  
 `FindField` <span data-ttu-id="3300d-118">Vyhledá pouze pole, které byly definovány přímo v dané třídy nebo rozhraní; Nelze najít zděděného pole.</span><span class="sxs-lookup"><span data-stu-id="3300d-118">finds only fields that were defined directly in the class or interface; it does not find inherited fields.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3300d-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3300d-119">Requirements</span></span>  
 <span data-ttu-id="3300d-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3300d-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3300d-121">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3300d-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3300d-122">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3300d-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="3300d-123">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="3300d-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3300d-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3300d-124">See also</span></span>

- [<span data-ttu-id="3300d-125">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3300d-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="3300d-126">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3300d-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
