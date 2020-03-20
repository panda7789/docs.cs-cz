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
ms.openlocfilehash: 53b3d94e8b1e273fcbc041d25a5bf586a12735c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177254"
---
# <a name="imetadataimportfindmethod-method"></a><span data-ttu-id="29f08-102">IMetaDataImport::FindMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="29f08-102">IMetaDataImport::FindMethod Method</span></span>
<span data-ttu-id="29f08-103">Získá ukazatel na MethodDef token pro metodu, která <xref:System.Type> je uzavřena zadaný a který má zadaný název a metadata podpisu.</span><span class="sxs-lookup"><span data-stu-id="29f08-103">Gets a pointer to the MethodDef token for the method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29f08-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29f08-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMethod (  
   [in]  mdTypeDef          td,  
   [in]  LPCWSTR            szName,
   [in]  PCCOR_SIGNATURE    pvSigBlob,
   [in]  ULONG              cbSigBlob,
   [out] mdMethodDef        *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29f08-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="29f08-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="29f08-106">[v] Token `mdTypeDef` pro typ (třída nebo rozhraní), který obklopuje člena hledat.</span><span class="sxs-lookup"><span data-stu-id="29f08-106">[in] The `mdTypeDef` token for the type (a class or interface) that encloses the member to search for.</span></span> <span data-ttu-id="29f08-107">Pokud je `mdTokenNil`tato hodnota , pak vyhledávání se provádí pro globální funkce.</span><span class="sxs-lookup"><span data-stu-id="29f08-107">If this value is `mdTokenNil`, then the lookup is done for a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="29f08-108">[v] Název metody, kterou chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="29f08-108">[in] The name of the method to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="29f08-109">[v] Ukazatel na podpis binárních metadat metody.</span><span class="sxs-lookup"><span data-stu-id="29f08-109">[in] A pointer to the binary metadata signature of the method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="29f08-110">[v] Velikost v bajtů `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="29f08-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="29f08-111">[out] Ukazatel na odpovídající token MethodDef.</span><span class="sxs-lookup"><span data-stu-id="29f08-111">[out] A pointer to the matching MethodDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29f08-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="29f08-112">Remarks</span></span>  
 <span data-ttu-id="29f08-113">Metodu určíte pomocí její ohraničující třídy nebo rozhraní (`td`), její název (`szName`) a volitelně její podpis (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="29f08-113">You specify the method using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="29f08-114">Ve třídě nebo rozhraní může existovat více metod se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="29f08-114">There might be multiple methods with the same name in a class or interface.</span></span> <span data-ttu-id="29f08-115">V takovém případě předavěte podpis metody a najděte jedinečnou shodu.</span><span class="sxs-lookup"><span data-stu-id="29f08-115">In that case, pass the method's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="29f08-116">Předaný `FindMethod` podpis musí být vygenerován v aktuálním oboru, protože podpisy jsou vázány na určitý obor.</span><span class="sxs-lookup"><span data-stu-id="29f08-116">The signature passed to `FindMethod` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="29f08-117">Podpis může vložit token, který identifikuje ohraničující třídu nebo typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="29f08-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="29f08-118">Token je index do místní tabulky TypeDef.</span><span class="sxs-lookup"><span data-stu-id="29f08-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="29f08-119">Nelze vytvořit podpis za běhu mimo kontext aktuálního oboru a použít tento `FindMethod`podpis jako vstup pro vstup do aplikace .</span><span class="sxs-lookup"><span data-stu-id="29f08-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMethod`.</span></span>  
  
 <span data-ttu-id="29f08-120">`FindMethod`vyhledá pouze metody, které byly definovány přímo ve třídě nebo rozhraní; nenalezne zděděné metody.</span><span class="sxs-lookup"><span data-stu-id="29f08-120">`FindMethod` finds only methods that were defined directly in the class or interface; it does not find inherited methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29f08-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="29f08-121">Requirements</span></span>  
 <span data-ttu-id="29f08-122">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29f08-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29f08-123">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="29f08-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="29f08-124">**Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="29f08-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="29f08-125">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29f08-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29f08-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="29f08-126">See also</span></span>

- <xref:System.Reflection.MethodInfo>
- [<span data-ttu-id="29f08-127">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="29f08-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="29f08-128">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="29f08-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
