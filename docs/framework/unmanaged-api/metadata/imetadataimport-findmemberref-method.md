---
title: IMetaDataImport::FindMemberRef – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMemberRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMemberRef
helpviewer_keywords:
- IMetaDataImport::FindMemberRef method [.NET Framework metadata]
- FindMemberRef method [.NET Framework metadata]
ms.assetid: 1ccda329-d752-4d89-abe8-511af3c3f4c9
topic_type:
- apiref
ms.openlocfilehash: d8b8bfd0e70e75c702f32555c10f433a1ff4ae10
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175418"
---
# <a name="imetadataimportfindmemberref-method"></a><span data-ttu-id="7b2d5-102">IMetaDataImport::FindMemberRef – metoda</span><span class="sxs-lookup"><span data-stu-id="7b2d5-102">IMetaDataImport::FindMemberRef Method</span></span>
<span data-ttu-id="7b2d5-103">Získá ukazatel na memberref token pro odkaz člena, který <xref:System.Type> je uzavřen zadaný a který má zadaný název a metadata podpisu.</span><span class="sxs-lookup"><span data-stu-id="7b2d5-103">Gets a pointer to the MemberRef token for the member reference that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b2d5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b2d5-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMemberRef (  
   [in]  mdTypeRef          td,  
   [in]  LPCWSTR            szName,
   [in]  PCCOR_SIGNATURE    pvSigBlob,
   [in]  ULONG              cbSigBlob,
   [out] mdMemberRef        *pmr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b2d5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7b2d5-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="7b2d5-106">[v] TypeRef token pro třídu nebo rozhraní, které obklopuje odkaz na člena hledat.</span><span class="sxs-lookup"><span data-stu-id="7b2d5-106">[in] The TypeRef token for the class or interface that encloses the member reference to search for.</span></span> <span data-ttu-id="7b2d5-107">Pokud je `mdTokenNil`tato hodnota , vyhledávání se provádí pro globální proměnnou nebo odkaz na globální funkci.</span><span class="sxs-lookup"><span data-stu-id="7b2d5-107">If this value is `mdTokenNil`, the lookup is done for a global variable or a global-function reference.</span></span>  
  
 `szName`  
 <span data-ttu-id="7b2d5-108">[v] Název členského odkazu pro hledání.</span><span class="sxs-lookup"><span data-stu-id="7b2d5-108">[in] The name of the member reference to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="7b2d5-109">[v] Ukazatel na podpis binárních metadat členského odkazu.</span><span class="sxs-lookup"><span data-stu-id="7b2d5-109">[in] A pointer to the binary metadata signature of the member reference.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="7b2d5-110">[v] Velikost v bajtů `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="7b2d5-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="7b2d5-111">[out] Ukazatel na odpovídající MemberRef token.</span><span class="sxs-lookup"><span data-stu-id="7b2d5-111">[out] A pointer to the matching MemberRef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7b2d5-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7b2d5-112">Remarks</span></span>  
 <span data-ttu-id="7b2d5-113">Člen zadejte pomocí jeho ohraničující třídy nebo rozhraní (`td`), jeho názvu (`szName`) a volitelně jeho podpisu (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="7b2d5-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="7b2d5-114">Předaný `FindMemberRef` podpis musí být vygenerován v aktuálním oboru, protože podpisy jsou vázány na určitý obor.</span><span class="sxs-lookup"><span data-stu-id="7b2d5-114">The signature passed to `FindMemberRef` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="7b2d5-115">Podpis může vložit token, který identifikuje ohraničující třídu nebo typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="7b2d5-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="7b2d5-116">Token je index do místní tabulky TypeDef.</span><span class="sxs-lookup"><span data-stu-id="7b2d5-116">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="7b2d5-117">Nelze vytvořit podpis za běhu mimo kontext aktuálního oboru a použít `FindMemberRef`tento podpis jako vstup do aplikace .</span><span class="sxs-lookup"><span data-stu-id="7b2d5-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindMemberRef`.</span></span>  
  
 <span data-ttu-id="7b2d5-118">`FindMemberRef`vyhledá pouze členské odkazy, které byly definovány přímo ve třídě nebo rozhraní; nenalezne zděděné členské odkazy.</span><span class="sxs-lookup"><span data-stu-id="7b2d5-118">`FindMemberRef` finds only member references that were defined directly in the class or interface; it does not find inherited member references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b2d5-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7b2d5-119">Requirements</span></span>  
 <span data-ttu-id="7b2d5-120">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b2d5-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b2d5-121">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="7b2d5-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7b2d5-122">**Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7b2d5-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7b2d5-123">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b2d5-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b2d5-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="7b2d5-124">See also</span></span>

- [<span data-ttu-id="7b2d5-125">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7b2d5-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="7b2d5-126">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7b2d5-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
