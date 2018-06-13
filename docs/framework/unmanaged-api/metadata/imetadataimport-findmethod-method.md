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
ms.openlocfilehash: 6b68d4e3d51fdb50290319de804a78c1a78a07a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447385"
---
# <a name="imetadataimportfindmethod-method"></a><span data-ttu-id="c137a-102">IMetaDataImport::FindMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="c137a-102">IMetaDataImport::FindMethod Method</span></span>
<span data-ttu-id="c137a-103">Získá ukazatel na MethodDef token pro metodu, která je uzavřena k zadanému <xref:System.Type> a má zadaný název a metadata podpis.</span><span class="sxs-lookup"><span data-stu-id="c137a-103">Gets a pointer to the MethodDef token for the method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c137a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c137a-104">Syntax</span></span>  
  
```  
HRESULT FindMethod (  
   [in]  mdTypeDef          td,  
   [in]  LPCWSTR            szName,   
   [in]  PCCOR_SIGNATURE    pvSigBlob,   
   [in]  ULONG              cbSigBlob,   
   [out] mdMethodDef        *pmb  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c137a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c137a-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="c137a-106">[v] `mdTypeDef` Tokenu pro typ (třídy nebo rozhraní), která obklopuje člena pro vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="c137a-106">[in] The `mdTypeDef` token for the type (a class or interface) that encloses the member to search for.</span></span> <span data-ttu-id="c137a-107">Pokud je tato hodnota `mdTokenNil`, pak se provádí vyhledávání pro globální funkce.</span><span class="sxs-lookup"><span data-stu-id="c137a-107">If this value is `mdTokenNil`, then the lookup is done for a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="c137a-108">[v] Název metody, které chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="c137a-108">[in] The name of the method to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="c137a-109">[v] Ukazatel na binární metadata podpis metody.</span><span class="sxs-lookup"><span data-stu-id="c137a-109">[in] A pointer to the binary metadata signature of the method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="c137a-110">[v] Velikost v bajtech `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="c137a-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="c137a-111">[out] Ukazatel na odpovídající MethodDef token.</span><span class="sxs-lookup"><span data-stu-id="c137a-111">[out] A pointer to the matching MethodDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c137a-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c137a-112">Remarks</span></span>  
 <span data-ttu-id="c137a-113">Zadejte metodu pomocí jeho nadřazených třídy nebo rozhraní (`td`), jeho název (`szName`) a volitelně jeho podpis (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="c137a-113">You specify the method using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="c137a-114">Může být několik metod se stejným názvem do třídy nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c137a-114">There might be multiple methods with the same name in a class or interface.</span></span> <span data-ttu-id="c137a-115">V takovém případě předejte signatury metody se najít shodu jedinečný.</span><span class="sxs-lookup"><span data-stu-id="c137a-115">In that case, pass the method's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="c137a-116">Podpis předaný `FindMethod` musí být vygenerováno v aktuálním oboru, protože podpis je vázána na konkrétní rozsah.</span><span class="sxs-lookup"><span data-stu-id="c137a-116">The signature passed to `FindMethod` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="c137a-117">Podpis můžete vložit token, který identifikuje nadřazeného typu třídy nebo hodnota.</span><span class="sxs-lookup"><span data-stu-id="c137a-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="c137a-118">Token je index do místní definice typu tabulky.</span><span class="sxs-lookup"><span data-stu-id="c137a-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="c137a-119">Nelze vytvořit podpis běhu mimo kontext aktuálního oboru a používání tohoto podpisu jako vstup pro vstup na `FindMethod`.</span><span class="sxs-lookup"><span data-stu-id="c137a-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMethod`.</span></span>  
  
 <span data-ttu-id="c137a-120">`FindMethod` Vyhledá pouze metod, které byly definovány přímo v třídy nebo rozhraní; zděděné metody nenajde.</span><span class="sxs-lookup"><span data-stu-id="c137a-120">`FindMethod` finds only methods that were defined directly in the class or interface; it does not find inherited methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c137a-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c137a-121">Requirements</span></span>  
 <span data-ttu-id="c137a-122">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c137a-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c137a-123">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c137a-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c137a-124">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c137a-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c137a-125">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c137a-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c137a-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="c137a-126">See Also</span></span>  
 <xref:System.Reflection.MethodInfo>  
 [<span data-ttu-id="c137a-127">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c137a-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="c137a-128">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c137a-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
