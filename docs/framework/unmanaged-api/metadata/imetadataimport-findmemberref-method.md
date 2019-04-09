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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59177889"
---
# <a name="imetadataimportfindmemberref-method"></a><span data-ttu-id="68f4a-102">IMetaDataImport::FindMemberRef – metoda</span><span class="sxs-lookup"><span data-stu-id="68f4a-102">IMetaDataImport::FindMemberRef Method</span></span>
<span data-ttu-id="68f4a-103">Získá ukazatel na token MemberRef pro člena, který je odkaz uzavřen parametrem <xref:System.Type> a, který má zadaný název a metadata podpis.</span><span class="sxs-lookup"><span data-stu-id="68f4a-103">Gets a pointer to the MemberRef token for the member reference that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68f4a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68f4a-104">Syntax</span></span>  
  
```  
HRESULT FindMemberRef (  
   [in]  mdTypeRef          td,  
   [in]  LPCWSTR            szName,   
   [in]  PCCOR_SIGNATURE    pvSigBlob,   
   [in]  ULONG              cbSigBlob,   
   [out] mdMemberRef        *pmr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68f4a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="68f4a-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="68f4a-106">[in] Token TypeRef pro třídu nebo rozhraní, který obklopuje odkaz na člena pro hledání.</span><span class="sxs-lookup"><span data-stu-id="68f4a-106">[in] The TypeRef token for the class or interface that encloses the member reference to search for.</span></span> <span data-ttu-id="68f4a-107">Pokud je tato hodnota `mdTokenNil`, vyhledávání se provádí pro globální proměnnou nebo odkaz na globální funkce.</span><span class="sxs-lookup"><span data-stu-id="68f4a-107">If this value is `mdTokenNil`, the lookup is done for a global variable or a global-function reference.</span></span>  
  
 `szName`  
 <span data-ttu-id="68f4a-108">[in] Název člena odkazu pro vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="68f4a-108">[in] The name of the member reference to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="68f4a-109">[in] Ukazatel na binární metadat podpisu člena odkazu.</span><span class="sxs-lookup"><span data-stu-id="68f4a-109">[in] A pointer to the binary metadata signature of the member reference.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="68f4a-110">[in] Velikost v bajtech `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="68f4a-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="68f4a-111">[out] Ukazatel na odpovídající token MemberRef.</span><span class="sxs-lookup"><span data-stu-id="68f4a-111">[out] A pointer to the matching MemberRef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68f4a-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="68f4a-112">Remarks</span></span>  
 <span data-ttu-id="68f4a-113">Zadejte členu pomocí jeho nadřazené třídu nebo rozhraní (`td`), jeho název (`szName`) a volitelně jeho podpis (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="68f4a-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="68f4a-114">Podpis předán `FindMemberRef` musí byly vytvořeny v aktuálním oboru, protože podpisy jsou vázány na určitém rozsahu.</span><span class="sxs-lookup"><span data-stu-id="68f4a-114">The signature passed to `FindMemberRef` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="68f4a-115">Podpis můžete vložit token, který identifikuje nadřazeného class nebo hodnotového typu.</span><span class="sxs-lookup"><span data-stu-id="68f4a-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="68f4a-116">Token je index do místní tabulky TypeDef.</span><span class="sxs-lookup"><span data-stu-id="68f4a-116">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="68f4a-117">Nelze sestavit podpis za běhu mimo kontext aktuálního oboru a použít tento podpis jako vstup pro `FindMemberRef`.</span><span class="sxs-lookup"><span data-stu-id="68f4a-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindMemberRef`.</span></span>  
  
 `FindMemberRef` <span data-ttu-id="68f4a-118">Vyhledá pouze odkazy na členy, které byly definovány přímo v dané třídy nebo rozhraní; Nelze najít odkazy zděděný člen.</span><span class="sxs-lookup"><span data-stu-id="68f4a-118">finds only member references that were defined directly in the class or interface; it does not find inherited member references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68f4a-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="68f4a-119">Requirements</span></span>  
 <span data-ttu-id="68f4a-120">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68f4a-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68f4a-121">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="68f4a-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="68f4a-122">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="68f4a-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="68f4a-123">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="68f4a-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="68f4a-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="68f4a-124">See also</span></span>

- [<span data-ttu-id="68f4a-125">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="68f4a-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="68f4a-126">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="68f4a-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
