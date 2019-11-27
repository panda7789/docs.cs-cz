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
ms.openlocfilehash: 470b6511366cef1680eaf97f9ab376736add55c4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437893"
---
# <a name="imetadataimportfindmethod-method"></a><span data-ttu-id="b04f9-102">IMetaDataImport::FindMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="b04f9-102">IMetaDataImport::FindMethod Method</span></span>
<span data-ttu-id="b04f9-103">Získá ukazatel na token MethodDef pro metodu, která je uzavřena zadaným <xref:System.Type> a která má zadaný název a signaturu metadat.</span><span class="sxs-lookup"><span data-stu-id="b04f9-103">Gets a pointer to the MethodDef token for the method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b04f9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b04f9-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMethod (  
   [in]  mdTypeDef          td,  
   [in]  LPCWSTR            szName,   
   [in]  PCCOR_SIGNATURE    pvSigBlob,   
   [in]  ULONG              cbSigBlob,   
   [out] mdMethodDef        *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b04f9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b04f9-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="b04f9-106">pro Token `mdTypeDef` pro typ (třída nebo rozhraní), který je členem pro hledání.</span><span class="sxs-lookup"><span data-stu-id="b04f9-106">[in] The `mdTypeDef` token for the type (a class or interface) that encloses the member to search for.</span></span> <span data-ttu-id="b04f9-107">Pokud je tato hodnota `mdTokenNil`, je vyhledávání provedeno pro globální funkci.</span><span class="sxs-lookup"><span data-stu-id="b04f9-107">If this value is `mdTokenNil`, then the lookup is done for a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="b04f9-108">pro Název metody, která se má vyhledat.</span><span class="sxs-lookup"><span data-stu-id="b04f9-108">[in] The name of the method to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="b04f9-109">pro Ukazatel na binární podpis metadat metody.</span><span class="sxs-lookup"><span data-stu-id="b04f9-109">[in] A pointer to the binary metadata signature of the method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="b04f9-110">pro Velikost v bajtech `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="b04f9-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="b04f9-111">mimo Ukazatel na shodný token MethodDef.</span><span class="sxs-lookup"><span data-stu-id="b04f9-111">[out] A pointer to the matching MethodDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b04f9-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b04f9-112">Remarks</span></span>  
 <span data-ttu-id="b04f9-113">Zadejte metodu pomocí své nadřazené třídy nebo rozhraní (`td`), jejího názvu (`szName`) a volitelně její signaturu (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="b04f9-113">You specify the method using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="b04f9-114">V rámci třídy nebo rozhraní může existovat více metod se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="b04f9-114">There might be multiple methods with the same name in a class or interface.</span></span> <span data-ttu-id="b04f9-115">V takovém případě předejte signaturu metody, abyste našli jedinečnou shodu.</span><span class="sxs-lookup"><span data-stu-id="b04f9-115">In that case, pass the method's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="b04f9-116">Podpis předaný do `FindMethod` musí být vygenerován v aktuálním oboru, protože signatury jsou vázány na konkrétní obor.</span><span class="sxs-lookup"><span data-stu-id="b04f9-116">The signature passed to `FindMethod` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="b04f9-117">Podpis může vložit token, který identifikuje ohraničující třídu nebo typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b04f9-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="b04f9-118">Token je index do místní tabulky TypeDef.</span><span class="sxs-lookup"><span data-stu-id="b04f9-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="b04f9-119">Nemůžete sestavit signaturu za běhu mimo kontext aktuálního oboru a použít tento podpis jako vstup do `FindMethod`.</span><span class="sxs-lookup"><span data-stu-id="b04f9-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMethod`.</span></span>  
  
 <span data-ttu-id="b04f9-120">`FindMethod` najde pouze metody, které byly definovány přímo ve třídě nebo rozhraní; nenalezne zděděné metody.</span><span class="sxs-lookup"><span data-stu-id="b04f9-120">`FindMethod` finds only methods that were defined directly in the class or interface; it does not find inherited methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b04f9-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b04f9-121">Requirements</span></span>  
 <span data-ttu-id="b04f9-122">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b04f9-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b04f9-123">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b04f9-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b04f9-124">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b04f9-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b04f9-125">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b04f9-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b04f9-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b04f9-126">See also</span></span>

- <xref:System.Reflection.MethodInfo>
- [<span data-ttu-id="b04f9-127">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b04f9-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="b04f9-128">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b04f9-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
