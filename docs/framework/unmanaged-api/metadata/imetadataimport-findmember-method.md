---
title: "IMetaDataImport::FindMember – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a20930688aed210309a719de2c7187f1f5fd1f24
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportfindmember-method"></a><span data-ttu-id="843b7-102">IMetaDataImport::FindMember – metoda</span><span class="sxs-lookup"><span data-stu-id="843b7-102">IMetaDataImport::FindMember Method</span></span>
<span data-ttu-id="843b7-103">Získá ukazatel na MemberDef token pro pole nebo metoda, která je uzavřena k zadanému <xref:System.Type> a má zadaný název a metadata podpis.</span><span class="sxs-lookup"><span data-stu-id="843b7-103">Gets a pointer to the MemberDef token for field or method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="843b7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="843b7-104">Syntax</span></span>  
  
```  
HRESULT FindMember (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,   
   [in]  PCCOR_SIGNATURE   pvSigBlob,   
   [in]  ULONG             cbSigBlob,   
   [out] mdToken           *pmb  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="843b7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="843b7-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="843b7-106">[v] Token TypeDef pro třídy nebo rozhraní, která obklopuje člena pro vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="843b7-106">[in] The TypeDef token for the class or interface that encloses the member to search for.</span></span> <span data-ttu-id="843b7-107">Pokud je tato hodnota `mdTokenNil`, se provádí vyhledávání pro globální proměnná nebo globální funkce.</span><span class="sxs-lookup"><span data-stu-id="843b7-107">If this value is `mdTokenNil`, the lookup is done for a global-variable or global-function.</span></span>  
  
 `szName`  
 <span data-ttu-id="843b7-108">[v] Název člena pro vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="843b7-108">[in] The name of the member to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="843b7-109">[v] Ukazatel na podpis binární metadata člena.</span><span class="sxs-lookup"><span data-stu-id="843b7-109">[in] A pointer to the binary metadata signature of the member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="843b7-110">[v] Velikost v bajtech `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="843b7-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="843b7-111">[out] Ukazatel na odpovídající MemberDef token.</span><span class="sxs-lookup"><span data-stu-id="843b7-111">[out] A pointer to the matching MemberDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="843b7-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="843b7-112">Remarks</span></span>  
 <span data-ttu-id="843b7-113">Zadejte člena pomocí jeho nadřazených třídy nebo rozhraní (`td`), jeho název (`szName`) a volitelně jeho podpis (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="843b7-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="843b7-114">Může existovat více členy se stejným názvem do třídy nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="843b7-114">There might be multiple members with the same name in a class or interface.</span></span> <span data-ttu-id="843b7-115">V takovém případě předejte člena podpis se najít shodu jedinečný.</span><span class="sxs-lookup"><span data-stu-id="843b7-115">In that case, pass the member's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="843b7-116">Podpis předaný `FindMember` musí být vygenerováno v aktuálním oboru, protože podpis je vázána na konkrétní rozsah.</span><span class="sxs-lookup"><span data-stu-id="843b7-116">The signature passed to `FindMember` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="843b7-117">Podpis můžete vložit token, který identifikuje nadřazeného typu třídy nebo hodnota.</span><span class="sxs-lookup"><span data-stu-id="843b7-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="843b7-118">Token je index do místní definice typu tabulky.</span><span class="sxs-lookup"><span data-stu-id="843b7-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="843b7-119">Nelze vytvořit podpis běhu mimo kontext aktuálního oboru a používání tohoto podpisu jako vstup pro vstup na `FindMember`.</span><span class="sxs-lookup"><span data-stu-id="843b7-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMember`.</span></span>  
  
 <span data-ttu-id="843b7-120">`FindMember`Vyhledá pouze členové, které byly definovány přímo v třídy nebo rozhraní; zděděné členy nenajde.</span><span class="sxs-lookup"><span data-stu-id="843b7-120">`FindMember` finds only members that were defined directly in the class or interface; it does not find inherited members.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="843b7-121">`FindMember`je metoda helper.</span><span class="sxs-lookup"><span data-stu-id="843b7-121">`FindMember` is a helper method.</span></span> <span data-ttu-id="843b7-122">Zavolá [imetadataimport::findmethod –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); Pokud toto volání nebyl nalezen odpovídající, `FindMember` pak zavolá [imetadataimport::findfield –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).</span><span class="sxs-lookup"><span data-stu-id="843b7-122">It calls [IMetaDataImport::FindMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); if that call does not find a match, `FindMember` then calls [IMetaDataImport::FindField](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="843b7-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="843b7-123">Requirements</span></span>  
 <span data-ttu-id="843b7-124">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="843b7-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="843b7-125">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="843b7-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="843b7-126">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="843b7-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="843b7-127">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="843b7-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="843b7-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="843b7-128">See Also</span></span>  
 [<span data-ttu-id="843b7-129">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="843b7-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="843b7-130">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="843b7-130">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
