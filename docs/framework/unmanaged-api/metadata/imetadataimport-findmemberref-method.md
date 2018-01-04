---
title: "IMetaDataImport::FindMemberRef – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.FindMemberRef
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::FindMemberRef
helpviewer_keywords:
- IMetaDataImport::FindMemberRef method [.NET Framework metadata]
- FindMemberRef method [.NET Framework metadata]
ms.assetid: 1ccda329-d752-4d89-abe8-511af3c3f4c9
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a94fb09e1ff62abac9dd716257ba75542453707e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportfindmemberref-method"></a><span data-ttu-id="4a302-102">IMetaDataImport::FindMemberRef – metoda</span><span class="sxs-lookup"><span data-stu-id="4a302-102">IMetaDataImport::FindMemberRef Method</span></span>
<span data-ttu-id="4a302-103">Získá ukazatel na token MemberRef pro člena odkazovat na který je uzavřené do zadané <xref:System.Type> a má zadaný název a metadata podpis.</span><span class="sxs-lookup"><span data-stu-id="4a302-103">Gets a pointer to the MemberRef token for the member reference that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a302-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4a302-104">Syntax</span></span>  
  
```  
HRESULT FindMemberRef (  
   [in]  mdTypeRef          td,  
   [in]  LPCWSTR            szName,   
   [in]  PCCOR_SIGNATURE    pvSigBlob,   
   [in]  ULONG              cbSigBlob,   
   [out] mdMemberRef        *pmr  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4a302-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4a302-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="4a302-106">[v] Odkaz TypeRef token pro třídu nebo rozhraní, která obklopuje odkaz na člena pro vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="4a302-106">[in] The TypeRef token for the class or interface that encloses the member reference to search for.</span></span> <span data-ttu-id="4a302-107">Pokud je tato hodnota `mdTokenNil`, se provádí vyhledávání pro globální proměnné nebo odkaz na globální funkce.</span><span class="sxs-lookup"><span data-stu-id="4a302-107">If this value is `mdTokenNil`, the lookup is done for a global variable or a global-function reference.</span></span>  
  
 `szName`  
 <span data-ttu-id="4a302-108">[v] Název odkaz na člena pro vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="4a302-108">[in] The name of the member reference to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="4a302-109">[v] Ukazatel na binární metadata podpis odkaz na člena.</span><span class="sxs-lookup"><span data-stu-id="4a302-109">[in] A pointer to the binary metadata signature of the member reference.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="4a302-110">[v] Velikost v bajtech `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="4a302-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="4a302-111">[out] Ukazatel na odpovídající MemberRef token.</span><span class="sxs-lookup"><span data-stu-id="4a302-111">[out] A pointer to the matching MemberRef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a302-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4a302-112">Remarks</span></span>  
 <span data-ttu-id="4a302-113">Zadejte člena pomocí jeho nadřazených třídy nebo rozhraní (`td`), jeho název (`szName`) a volitelně jeho podpis (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="4a302-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="4a302-114">Podpis předaný `FindMemberRef` musí být vygenerováno v aktuálním oboru, protože podpis je vázána na konkrétní rozsah.</span><span class="sxs-lookup"><span data-stu-id="4a302-114">The signature passed to `FindMemberRef` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="4a302-115">Podpis můžete vložit token, který identifikuje nadřazeného typu třídy nebo hodnota.</span><span class="sxs-lookup"><span data-stu-id="4a302-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="4a302-116">Token je index do místní definice typu tabulky.</span><span class="sxs-lookup"><span data-stu-id="4a302-116">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="4a302-117">Nelze vytvořit podpis běhu mimo kontext aktuálního oboru a použít jako vstup pro tento podpis `FindMemberRef`.</span><span class="sxs-lookup"><span data-stu-id="4a302-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindMemberRef`.</span></span>  
  
 <span data-ttu-id="4a302-118">`FindMemberRef`Vyhledá pouze člen odkazy, které byly definovány přímo v třídy nebo rozhraní; odkazy na zděděné členy nenajde.</span><span class="sxs-lookup"><span data-stu-id="4a302-118">`FindMemberRef` finds only member references that were defined directly in the class or interface; it does not find inherited member references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a302-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4a302-119">Requirements</span></span>  
 <span data-ttu-id="4a302-120">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a302-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a302-121">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4a302-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4a302-122">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4a302-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4a302-123">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a302-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a302-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="4a302-124">See Also</span></span>  
 [<span data-ttu-id="4a302-125">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4a302-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="4a302-126">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4a302-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
