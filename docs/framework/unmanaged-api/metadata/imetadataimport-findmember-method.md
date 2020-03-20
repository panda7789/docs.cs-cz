---
title: IMetaDataImport::FindMember – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMember
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMember
helpviewer_keywords:
- IMetaDataImport::FindMember method [.NET Framework metadata]
- FindMember method [.NET Framework metadata]
ms.assetid: ad32fb84-c2b6-41cd-888d-787ff3a90449
topic_type:
- apiref
ms.openlocfilehash: dab155b82d87609b3d3f390133e6490502a43518
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177286"
---
# <a name="imetadataimportfindmember-method"></a><span data-ttu-id="3d8f3-102">IMetaDataImport::FindMember – metoda</span><span class="sxs-lookup"><span data-stu-id="3d8f3-102">IMetaDataImport::FindMember Method</span></span>
<span data-ttu-id="3d8f3-103">Získá ukazatel na MemberDef token pro pole nebo metodu, která je uzavřena zadané <xref:System.Type> a který má zadaný název a metadata podpis.</span><span class="sxs-lookup"><span data-stu-id="3d8f3-103">Gets a pointer to the MemberDef token for field or method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d8f3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d8f3-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMember (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,
   [in]  PCCOR_SIGNATURE   pvSigBlob,
   [in]  ULONG             cbSigBlob,
   [out] mdToken           *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d8f3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3d8f3-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="3d8f3-106">[v] TypeDef token pro třídu nebo rozhraní, které obklopuje člen hledat.</span><span class="sxs-lookup"><span data-stu-id="3d8f3-106">[in] The TypeDef token for the class or interface that encloses the member to search for.</span></span> <span data-ttu-id="3d8f3-107">Pokud je `mdTokenNil`tato hodnota , vyhledávání se provádí pro globální proměnné nebo globální funkce.</span><span class="sxs-lookup"><span data-stu-id="3d8f3-107">If this value is `mdTokenNil`, the lookup is done for a global-variable or global-function.</span></span>  
  
 `szName`  
 <span data-ttu-id="3d8f3-108">[v] Jméno člena, který má být hledán.</span><span class="sxs-lookup"><span data-stu-id="3d8f3-108">[in] The name of the member to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="3d8f3-109">[v] Ukazatel na podpis binárních metadat člena.</span><span class="sxs-lookup"><span data-stu-id="3d8f3-109">[in] A pointer to the binary metadata signature of the member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="3d8f3-110">[v] Velikost v bajtů `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="3d8f3-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="3d8f3-111">[out] Ukazatel na odpovídající token MemberDef.</span><span class="sxs-lookup"><span data-stu-id="3d8f3-111">[out] A pointer to the matching MemberDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d8f3-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3d8f3-112">Remarks</span></span>  
 <span data-ttu-id="3d8f3-113">Člen zadejte pomocí jeho ohraničující třídy nebo rozhraní (`td`), jeho názvu (`szName`) a volitelně jeho podpisu (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="3d8f3-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="3d8f3-114">Ve třídě nebo rozhraní může být více členů se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="3d8f3-114">There might be multiple members with the same name in a class or interface.</span></span> <span data-ttu-id="3d8f3-115">V takovém případě předavěte podpis člena a najděte jedinečnou shodu.</span><span class="sxs-lookup"><span data-stu-id="3d8f3-115">In that case, pass the member's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="3d8f3-116">Předaný `FindMember` podpis musí být vygenerován v aktuálním oboru, protože podpisy jsou vázány na určitý obor.</span><span class="sxs-lookup"><span data-stu-id="3d8f3-116">The signature passed to `FindMember` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="3d8f3-117">Podpis může vložit token, který identifikuje ohraničující třídu nebo typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="3d8f3-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="3d8f3-118">Token je index do místní tabulky TypeDef.</span><span class="sxs-lookup"><span data-stu-id="3d8f3-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="3d8f3-119">Nelze vytvořit podpis za běhu mimo kontext aktuálního oboru a použít tento `FindMember`podpis jako vstup pro vstup do aplikace .</span><span class="sxs-lookup"><span data-stu-id="3d8f3-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMember`.</span></span>  
  
 <span data-ttu-id="3d8f3-120">`FindMember`vyhledá pouze členy, které byly definovány přímo ve třídě nebo rozhraní; nenalezne zděděné členy.</span><span class="sxs-lookup"><span data-stu-id="3d8f3-120">`FindMember` finds only members that were defined directly in the class or interface; it does not find inherited members.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3d8f3-121">`FindMember`je pomocná metoda.</span><span class="sxs-lookup"><span data-stu-id="3d8f3-121">`FindMember` is a helper method.</span></span> <span data-ttu-id="3d8f3-122">Volá [iMetaDataImport::FindMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); Pokud toto volání nenajde `FindMember` shodu, pak volá [IMetaDataImport::FindField](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).</span><span class="sxs-lookup"><span data-stu-id="3d8f3-122">It calls [IMetaDataImport::FindMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); if that call does not find a match, `FindMember` then calls [IMetaDataImport::FindField](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d8f3-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3d8f3-123">Requirements</span></span>  
 <span data-ttu-id="3d8f3-124">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d8f3-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d8f3-125">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="3d8f3-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3d8f3-126">**Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3d8f3-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3d8f3-127">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d8f3-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d8f3-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="3d8f3-128">See also</span></span>

- [<span data-ttu-id="3d8f3-129">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3d8f3-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="3d8f3-130">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3d8f3-130">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
