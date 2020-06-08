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
ms.openlocfilehash: c2ec907759a25048444ebcc81bf5bb0fd23ced58
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503650"
---
# <a name="imetadataimportfindmethod-method"></a><span data-ttu-id="aad78-102">IMetaDataImport::FindMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="aad78-102">IMetaDataImport::FindMethod Method</span></span>
<span data-ttu-id="aad78-103">Získá ukazatel na token MethodDef pro metodu, která je ohraničena specifikovanou <xref:System.Type> a, která má zadaný název a signaturu metadat.</span><span class="sxs-lookup"><span data-stu-id="aad78-103">Gets a pointer to the MethodDef token for the method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aad78-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aad78-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMethod (  
   [in]  mdTypeDef          td,  
   [in]  LPCWSTR            szName,
   [in]  PCCOR_SIGNATURE    pvSigBlob,
   [in]  ULONG              cbSigBlob,
   [out] mdMethodDef        *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aad78-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="aad78-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="aad78-106">pro `mdTypeDef`Token pro typ (třída nebo rozhraní), který obklopuje člena k hledání.</span><span class="sxs-lookup"><span data-stu-id="aad78-106">[in] The `mdTypeDef` token for the type (a class or interface) that encloses the member to search for.</span></span> <span data-ttu-id="aad78-107">Pokud je tato hodnota `mdTokenNil` , pak se pro globální funkci provede vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="aad78-107">If this value is `mdTokenNil`, then the lookup is done for a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="aad78-108">pro Název metody, která se má vyhledat.</span><span class="sxs-lookup"><span data-stu-id="aad78-108">[in] The name of the method to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="aad78-109">pro Ukazatel na binární podpis metadat metody.</span><span class="sxs-lookup"><span data-stu-id="aad78-109">[in] A pointer to the binary metadata signature of the method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="aad78-110">pro Velikost v bajtech `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="aad78-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="aad78-111">mimo Ukazatel na shodný token MethodDef.</span><span class="sxs-lookup"><span data-stu-id="aad78-111">[out] A pointer to the matching MethodDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aad78-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aad78-112">Remarks</span></span>  
 <span data-ttu-id="aad78-113">Zadejte metodu pomocí své nadřazené třídy nebo rozhraní () `td` , jejího názvu ( `szName` ) a volitelně její signatura ( `pvSigBlob` ).</span><span class="sxs-lookup"><span data-stu-id="aad78-113">You specify the method using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="aad78-114">V rámci třídy nebo rozhraní může existovat více metod se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="aad78-114">There might be multiple methods with the same name in a class or interface.</span></span> <span data-ttu-id="aad78-115">V takovém případě předejte signaturu metody, abyste našli jedinečnou shodu.</span><span class="sxs-lookup"><span data-stu-id="aad78-115">In that case, pass the method's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="aad78-116">Signatura předaná do `FindMethod` musí být vygenerována v aktuálním oboru, protože signatury jsou vázány na konkrétní obor.</span><span class="sxs-lookup"><span data-stu-id="aad78-116">The signature passed to `FindMethod` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="aad78-117">Podpis může vložit token, který identifikuje ohraničující třídu nebo typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="aad78-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="aad78-118">Token je index do místní tabulky TypeDef.</span><span class="sxs-lookup"><span data-stu-id="aad78-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="aad78-119">Nemůžete sestavit signaturu za běhu mimo kontext aktuálního oboru a použít ho jako vstup pro vstup do `FindMethod` .</span><span class="sxs-lookup"><span data-stu-id="aad78-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMethod`.</span></span>  
  
 <span data-ttu-id="aad78-120">`FindMethod`najde pouze metody, které byly definovány přímo ve třídě nebo rozhraní; nenalezne zděděné metody.</span><span class="sxs-lookup"><span data-stu-id="aad78-120">`FindMethod` finds only methods that were defined directly in the class or interface; it does not find inherited methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aad78-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aad78-121">Requirements</span></span>  
 <span data-ttu-id="aad78-122">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aad78-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aad78-123">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="aad78-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="aad78-124">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="aad78-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="aad78-125">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aad78-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aad78-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aad78-126">See also</span></span>

- <xref:System.Reflection.MethodInfo>
- [<span data-ttu-id="aad78-127">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aad78-127">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="aad78-128">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aad78-128">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
