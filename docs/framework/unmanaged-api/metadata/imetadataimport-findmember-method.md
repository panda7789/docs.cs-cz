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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 63afd82ca88e1a7c61913ec7fcc4d77d03ae9927
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59183167"
---
# <a name="imetadataimportfindmember-method"></a><span data-ttu-id="d2d30-102">IMetaDataImport::FindMember – metoda</span><span class="sxs-lookup"><span data-stu-id="d2d30-102">IMetaDataImport::FindMember Method</span></span>
<span data-ttu-id="d2d30-103">Získá ukazatel MemberDef token pro pole nebo metoda, která je uzavřena parametrem <xref:System.Type> a, který má zadaný název a metadata podpis.</span><span class="sxs-lookup"><span data-stu-id="d2d30-103">Gets a pointer to the MemberDef token for field or method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2d30-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d2d30-104">Syntax</span></span>  
  
```  
HRESULT FindMember (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,   
   [in]  PCCOR_SIGNATURE   pvSigBlob,   
   [in]  ULONG             cbSigBlob,   
   [out] mdToken           *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2d30-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d2d30-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="d2d30-106">[in] Token TypeDef pro třídu nebo rozhraní, který obklopuje členu, který chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="d2d30-106">[in] The TypeDef token for the class or interface that encloses the member to search for.</span></span> <span data-ttu-id="d2d30-107">Pokud je tato hodnota `mdTokenNil`, vyhledávání se provádí pro globální proměnnou nebo globální funkce.</span><span class="sxs-lookup"><span data-stu-id="d2d30-107">If this value is `mdTokenNil`, the lookup is done for a global-variable or global-function.</span></span>  
  
 `szName`  
 <span data-ttu-id="d2d30-108">[in] Název členu, který chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="d2d30-108">[in] The name of the member to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="d2d30-109">[in] Ukazatel na binární metadat podpisu člena.</span><span class="sxs-lookup"><span data-stu-id="d2d30-109">[in] A pointer to the binary metadata signature of the member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="d2d30-110">[in] Velikost v bajtech `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="d2d30-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="d2d30-111">[out] Ukazatel na odpovídající MemberDef token.</span><span class="sxs-lookup"><span data-stu-id="d2d30-111">[out] A pointer to the matching MemberDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2d30-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d2d30-112">Remarks</span></span>  
 <span data-ttu-id="d2d30-113">Zadejte členu pomocí jeho nadřazené třídu nebo rozhraní (`td`), jeho název (`szName`) a volitelně jeho podpis (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="d2d30-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="d2d30-114">Může existovat více členů se stejným názvem ve třídě nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d2d30-114">There might be multiple members with the same name in a class or interface.</span></span> <span data-ttu-id="d2d30-115">V takovém případě předejte podpis členu zobrazíte unikátní shoda.</span><span class="sxs-lookup"><span data-stu-id="d2d30-115">In that case, pass the member's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="d2d30-116">Podpis předán `FindMember` musí byly vytvořeny v aktuálním oboru, protože podpisy jsou vázány na určitém rozsahu.</span><span class="sxs-lookup"><span data-stu-id="d2d30-116">The signature passed to `FindMember` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="d2d30-117">Podpis můžete vložit token, který identifikuje nadřazeného class nebo hodnotového typu.</span><span class="sxs-lookup"><span data-stu-id="d2d30-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="d2d30-118">Token je index do místní tabulky TypeDef.</span><span class="sxs-lookup"><span data-stu-id="d2d30-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="d2d30-119">Nelze sestavit podpis za běhu mimo kontext aktuálního oboru a použít tento podpis jako vstup pro vstup do `FindMember`.</span><span class="sxs-lookup"><span data-stu-id="d2d30-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMember`.</span></span>  
  
 `FindMember` <span data-ttu-id="d2d30-120">Vyhledá pouze členy, které byly definovány přímo v dané třídy nebo rozhraní; Nelze najít zděděných členů.</span><span class="sxs-lookup"><span data-stu-id="d2d30-120">finds only members that were defined directly in the class or interface; it does not find inherited members.</span></span>  
  
> [!NOTE]
>  `FindMember` <span data-ttu-id="d2d30-121">je pomocná metoda.</span><span class="sxs-lookup"><span data-stu-id="d2d30-121">is a helper method.</span></span> <span data-ttu-id="d2d30-122">Volá [imetadataimport::findmethod –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); Pokud je toto volání nenajde shoda, `FindMember` pak zavolá [imetadataimport::findfield –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).</span><span class="sxs-lookup"><span data-stu-id="d2d30-122">It calls [IMetaDataImport::FindMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); if that call does not find a match, `FindMember` then calls [IMetaDataImport::FindField](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2d30-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d2d30-123">Requirements</span></span>  
 <span data-ttu-id="d2d30-124">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2d30-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2d30-125">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d2d30-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d2d30-126">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d2d30-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="d2d30-127">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="d2d30-127">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d2d30-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d2d30-128">See also</span></span>

- [<span data-ttu-id="d2d30-129">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d2d30-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="d2d30-130">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d2d30-130">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
