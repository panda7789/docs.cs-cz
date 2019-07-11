---
title: IMetaDataImport::FindMethod – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMethod
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMethod
helpviewer_keywords:
- FindMethod method [.NET Framework metadata]
- IMetaDataImport::FindMethod method [.NET Framework metadata]
ms.assetid: 0f9bde1d-e306-438d-941b-d0925b322304
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4225794740b7786c6f758c9a0953d323c31a1081
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782493"
---
# <a name="imetadataimportfindmethod-method"></a><span data-ttu-id="0c520-102">IMetaDataImport::FindMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="0c520-102">IMetaDataImport::FindMethod Method</span></span>
<span data-ttu-id="0c520-103">Získá ukazatel MethodDef token pro metodu, která je uzavřena parametrem <xref:System.Type> a, který má zadaný název a metadata podpis.</span><span class="sxs-lookup"><span data-stu-id="0c520-103">Gets a pointer to the MethodDef token for the method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c520-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0c520-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMethod (  
   [in]  mdTypeDef          td,  
   [in]  LPCWSTR            szName,   
   [in]  PCCOR_SIGNATURE    pvSigBlob,   
   [in]  ULONG              cbSigBlob,   
   [out] mdMethodDef        *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c520-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0c520-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="0c520-106">[in] `mdTypeDef` Tokenů pro typ (třídu nebo rozhraní), který obklopuje členu, který chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="0c520-106">[in] The `mdTypeDef` token for the type (a class or interface) that encloses the member to search for.</span></span> <span data-ttu-id="0c520-107">Pokud je tato hodnota `mdTokenNil`, pak vyhledávání se provádí pro globální funkce.</span><span class="sxs-lookup"><span data-stu-id="0c520-107">If this value is `mdTokenNil`, then the lookup is done for a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="0c520-108">[in] Název metody pro hledání.</span><span class="sxs-lookup"><span data-stu-id="0c520-108">[in] The name of the method to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="0c520-109">[in] Ukazatel na binární metadat podpis metody.</span><span class="sxs-lookup"><span data-stu-id="0c520-109">[in] A pointer to the binary metadata signature of the method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="0c520-110">[in] Velikost v bajtech `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="0c520-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="0c520-111">[out] Ukazatel na odpovídající token MethodDef.</span><span class="sxs-lookup"><span data-stu-id="0c520-111">[out] A pointer to the matching MethodDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c520-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0c520-112">Remarks</span></span>  
 <span data-ttu-id="0c520-113">Zadejte metodu, pomocí jeho nadřazené třídu nebo rozhraní (`td`), jeho název (`szName`) a volitelně jeho podpis (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="0c520-113">You specify the method using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="0c520-114">Může existovat více metod se stejným názvem ve třídě nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0c520-114">There might be multiple methods with the same name in a class or interface.</span></span> <span data-ttu-id="0c520-115">V takovém případě předejte podpis metody k vyhledání unikátní shoda.</span><span class="sxs-lookup"><span data-stu-id="0c520-115">In that case, pass the method's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="0c520-116">Podpis předán `FindMethod` musí byly vytvořeny v aktuálním oboru, protože podpisy jsou vázány na určitém rozsahu.</span><span class="sxs-lookup"><span data-stu-id="0c520-116">The signature passed to `FindMethod` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="0c520-117">Podpis můžete vložit token, který identifikuje nadřazeného class nebo hodnotového typu.</span><span class="sxs-lookup"><span data-stu-id="0c520-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="0c520-118">Token je index do místní tabulky TypeDef.</span><span class="sxs-lookup"><span data-stu-id="0c520-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="0c520-119">Nelze sestavit podpis za běhu mimo kontext aktuálního oboru a použít tento podpis jako vstup pro vstup do `FindMethod`.</span><span class="sxs-lookup"><span data-stu-id="0c520-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMethod`.</span></span>  
  
 <span data-ttu-id="0c520-120">`FindMethod` Vyhledá pouze metody, které byly definovány přímo v dané třídy nebo rozhraní; Nelze najít zděděných metod.</span><span class="sxs-lookup"><span data-stu-id="0c520-120">`FindMethod` finds only methods that were defined directly in the class or interface; it does not find inherited methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c520-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0c520-121">Requirements</span></span>  
 <span data-ttu-id="0c520-122">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c520-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c520-123">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0c520-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0c520-124">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0c520-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0c520-125">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c520-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c520-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0c520-126">See also</span></span>

- <xref:System.Reflection.MethodInfo>
- [<span data-ttu-id="0c520-127">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0c520-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="0c520-128">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0c520-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
