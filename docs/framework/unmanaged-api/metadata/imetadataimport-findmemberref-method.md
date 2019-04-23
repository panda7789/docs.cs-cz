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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: abbd35fe390cc09951b762a5fd671d2d34a57c6c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59177889"
---
# <a name="imetadataimportfindmemberref-method"></a><span data-ttu-id="fe8d2-102">IMetaDataImport::FindMemberRef – metoda</span><span class="sxs-lookup"><span data-stu-id="fe8d2-102">IMetaDataImport::FindMemberRef Method</span></span>
<span data-ttu-id="fe8d2-103">Získá ukazatel na token MemberRef pro člena, který je odkaz uzavřen parametrem <xref:System.Type> a, který má zadaný název a metadata podpis.</span><span class="sxs-lookup"><span data-stu-id="fe8d2-103">Gets a pointer to the MemberRef token for the member reference that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe8d2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fe8d2-104">Syntax</span></span>  
  
```  
HRESULT FindMemberRef (  
   [in]  mdTypeRef          td,  
   [in]  LPCWSTR            szName,   
   [in]  PCCOR_SIGNATURE    pvSigBlob,   
   [in]  ULONG              cbSigBlob,   
   [out] mdMemberRef        *pmr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe8d2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fe8d2-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="fe8d2-106">[in] Token TypeRef pro třídu nebo rozhraní, který obklopuje odkaz na člena pro hledání.</span><span class="sxs-lookup"><span data-stu-id="fe8d2-106">[in] The TypeRef token for the class or interface that encloses the member reference to search for.</span></span> <span data-ttu-id="fe8d2-107">Pokud je tato hodnota `mdTokenNil`, vyhledávání se provádí pro globální proměnnou nebo odkaz na globální funkce.</span><span class="sxs-lookup"><span data-stu-id="fe8d2-107">If this value is `mdTokenNil`, the lookup is done for a global variable or a global-function reference.</span></span>  
  
 `szName`  
 <span data-ttu-id="fe8d2-108">[in] Název člena odkazu pro vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="fe8d2-108">[in] The name of the member reference to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="fe8d2-109">[in] Ukazatel na binární metadat podpisu člena odkazu.</span><span class="sxs-lookup"><span data-stu-id="fe8d2-109">[in] A pointer to the binary metadata signature of the member reference.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="fe8d2-110">[in] Velikost v bajtech `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="fe8d2-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="fe8d2-111">[out] Ukazatel na odpovídající token MemberRef.</span><span class="sxs-lookup"><span data-stu-id="fe8d2-111">[out] A pointer to the matching MemberRef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fe8d2-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fe8d2-112">Remarks</span></span>  
 <span data-ttu-id="fe8d2-113">Zadejte členu pomocí jeho nadřazené třídu nebo rozhraní (`td`), jeho název (`szName`) a volitelně jeho podpis (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="fe8d2-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="fe8d2-114">Podpis předán `FindMemberRef` musí byly vytvořeny v aktuálním oboru, protože podpisy jsou vázány na určitém rozsahu.</span><span class="sxs-lookup"><span data-stu-id="fe8d2-114">The signature passed to `FindMemberRef` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="fe8d2-115">Podpis můžete vložit token, který identifikuje nadřazeného class nebo hodnotového typu.</span><span class="sxs-lookup"><span data-stu-id="fe8d2-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="fe8d2-116">Token je index do místní tabulky TypeDef.</span><span class="sxs-lookup"><span data-stu-id="fe8d2-116">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="fe8d2-117">Nelze sestavit podpis za běhu mimo kontext aktuálního oboru a použít tento podpis jako vstup pro `FindMemberRef`.</span><span class="sxs-lookup"><span data-stu-id="fe8d2-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindMemberRef`.</span></span>  
  
 <span data-ttu-id="fe8d2-118">`FindMemberRef` Vyhledá pouze odkazy na členy, které byly definovány přímo v dané třídy nebo rozhraní; Nelze najít odkazy zděděný člen.</span><span class="sxs-lookup"><span data-stu-id="fe8d2-118">`FindMemberRef` finds only member references that were defined directly in the class or interface; it does not find inherited member references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe8d2-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fe8d2-119">Requirements</span></span>  
 <span data-ttu-id="fe8d2-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe8d2-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe8d2-121">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fe8d2-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fe8d2-122">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fe8d2-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fe8d2-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe8d2-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe8d2-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fe8d2-124">See also</span></span>

- [<span data-ttu-id="fe8d2-125">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fe8d2-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="fe8d2-126">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fe8d2-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
