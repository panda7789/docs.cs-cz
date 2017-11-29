---
title: "IMetaDataImport::FindMember – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.FindMember
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::FindMember
helpviewer_keywords:
- IMetaDataImport::FindMember method [.NET Framework metadata]
- FindMember method [.NET Framework metadata]
ms.assetid: ad32fb84-c2b6-41cd-888d-787ff3a90449
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a47060575d14e1206e715ea2bfd2ea750bd49c91
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportfindmember-method"></a><span data-ttu-id="66b6b-102">IMetaDataImport::FindMember – metoda</span><span class="sxs-lookup"><span data-stu-id="66b6b-102">IMetaDataImport::FindMember Method</span></span>
<span data-ttu-id="66b6b-103">Získá ukazatel na MemberDef token pro pole nebo metoda, která je uzavřena k zadanému <xref:System.Type> a má zadaný název a metadata podpis.</span><span class="sxs-lookup"><span data-stu-id="66b6b-103">Gets a pointer to the MemberDef token for field or method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66b6b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66b6b-104">Syntax</span></span>  
  
```  
HRESULT FindMember (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,   
   [in]  PCCOR_SIGNATURE   pvSigBlob,   
   [in]  ULONG             cbSigBlob,   
   [out] mdToken           *pmb  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="66b6b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="66b6b-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="66b6b-106">[v] Token TypeDef pro třídy nebo rozhraní, která obklopuje člena pro vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="66b6b-106">[in] The TypeDef token for the class or interface that encloses the member to search for.</span></span> <span data-ttu-id="66b6b-107">Pokud je tato hodnota `mdTokenNil`, se provádí vyhledávání pro globální proměnná nebo globální funkce.</span><span class="sxs-lookup"><span data-stu-id="66b6b-107">If this value is `mdTokenNil`, the lookup is done for a global-variable or global-function.</span></span>  
  
 `szName`  
 <span data-ttu-id="66b6b-108">[v] Název člena pro vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="66b6b-108">[in] The name of the member to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="66b6b-109">[v] Ukazatel na podpis binární metadata člena.</span><span class="sxs-lookup"><span data-stu-id="66b6b-109">[in] A pointer to the binary metadata signature of the member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="66b6b-110">[v] Velikost v bajtech `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="66b6b-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="66b6b-111">[out] Ukazatel na odpovídající MemberDef token.</span><span class="sxs-lookup"><span data-stu-id="66b6b-111">[out] A pointer to the matching MemberDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66b6b-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="66b6b-112">Remarks</span></span>  
 <span data-ttu-id="66b6b-113">Zadejte člena pomocí jeho nadřazených třídy nebo rozhraní (`td`), jeho název (`szName`) a volitelně jeho podpis (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="66b6b-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="66b6b-114">Může existovat více členy se stejným názvem do třídy nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="66b6b-114">There might be multiple members with the same name in a class or interface.</span></span> <span data-ttu-id="66b6b-115">V takovém případě předejte člena podpis se najít shodu jedinečný.</span><span class="sxs-lookup"><span data-stu-id="66b6b-115">In that case, pass the member's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="66b6b-116">Podpis předaný `FindMember` musí být vygenerováno v aktuálním oboru, protože podpis je vázána na konkrétní rozsah.</span><span class="sxs-lookup"><span data-stu-id="66b6b-116">The signature passed to `FindMember` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="66b6b-117">Podpis můžete vložit token, který identifikuje nadřazeného typu třídy nebo hodnota.</span><span class="sxs-lookup"><span data-stu-id="66b6b-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="66b6b-118">Token je index do místní definice typu tabulky.</span><span class="sxs-lookup"><span data-stu-id="66b6b-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="66b6b-119">Nelze vytvořit podpis běhu mimo kontext aktuálního oboru a používání tohoto podpisu jako vstup pro vstup na `FindMember`.</span><span class="sxs-lookup"><span data-stu-id="66b6b-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMember`.</span></span>  
  
 <span data-ttu-id="66b6b-120">`FindMember`Vyhledá pouze členové, které byly definovány přímo v třídy nebo rozhraní; zděděné členy nenajde.</span><span class="sxs-lookup"><span data-stu-id="66b6b-120">`FindMember` finds only members that were defined directly in the class or interface; it does not find inherited members.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="66b6b-121">`FindMember`je metoda helper.</span><span class="sxs-lookup"><span data-stu-id="66b6b-121">`FindMember` is a helper method.</span></span> <span data-ttu-id="66b6b-122">Zavolá [imetadataimport::findmethod –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); Pokud toto volání nebyl nalezen odpovídající, `FindMember` pak zavolá [imetadataimport::findfield –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).</span><span class="sxs-lookup"><span data-stu-id="66b6b-122">It calls [IMetaDataImport::FindMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); if that call does not find a match, `FindMember` then calls [IMetaDataImport::FindField](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66b6b-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="66b6b-123">Requirements</span></span>  
 <span data-ttu-id="66b6b-124">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66b6b-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66b6b-125">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="66b6b-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="66b6b-126">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="66b6b-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="66b6b-127">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66b6b-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66b6b-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="66b6b-128">See Also</span></span>  
 [<span data-ttu-id="66b6b-129">Imetadataimport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="66b6b-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="66b6b-130">Imetadataimport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="66b6b-130">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
