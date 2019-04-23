---
title: IMetaDataImport::EnumMembersWithName – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMembersWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMembersWithName
helpviewer_keywords:
- IMetaDataImport::EnumMembersWithName method [.NET Framework metadata]
- EnumMembersWithName method [.NET Framework metadata]
ms.assetid: 7c9e9120-3104-42f0-86ce-19a025f20dcc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c2509945d2799b81e036888d146a51cee87fda09
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59169842"
---
# <a name="imetadataimportenummemberswithname-method"></a><span data-ttu-id="05f08-102">IMetaDataImport::EnumMembersWithName – metoda</span><span class="sxs-lookup"><span data-stu-id="05f08-102">IMetaDataImport::EnumMembersWithName Method</span></span>
<span data-ttu-id="05f08-103">Vytvoří výčet MemberDef tokeny představující členů zadaného typu se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="05f08-103">Enumerates MemberDef tokens representing members of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05f08-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05f08-104">Syntax</span></span>  
  
```  
HRESULT EnumMembersWithName (  
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   cl,   
   [in]      LPCWSTR     szName,   
   [out]     mdToken     rMembers[],   
   [in]      ULONG       cMax,   
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05f08-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="05f08-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="05f08-106">[out v] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="05f08-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="05f08-107">[in] Token TypeDef představující typ s členy výčtu.</span><span class="sxs-lookup"><span data-stu-id="05f08-107">[in] A TypeDef token representing the type with members to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="05f08-108">[in] Název člena, který omezuje rozsah výčtu.</span><span class="sxs-lookup"><span data-stu-id="05f08-108">[in] The member name that limits the scope of the enumerator.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="05f08-109">[out] Pole pro ukládání tokenů MemberDef.</span><span class="sxs-lookup"><span data-stu-id="05f08-109">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="05f08-110">[in] Maximální velikost `rMembers` pole.</span><span class="sxs-lookup"><span data-stu-id="05f08-110">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="05f08-111">[out] Skutečný počet tokenů MemberDef vrácené v `rMembers`.</span><span class="sxs-lookup"><span data-stu-id="05f08-111">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05f08-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="05f08-112">Remarks</span></span>  
 <span data-ttu-id="05f08-113">Tato metoda vytváří výčet polí a metod, ale nikoli vlastnosti nebo události.</span><span class="sxs-lookup"><span data-stu-id="05f08-113">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="05f08-114">Na rozdíl od [imetadataimport::enummembers –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md), `EnumMembersWithName` zahodí všechny pole a člen tokeny, které nemají se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="05f08-114">Unlike [IMetaDataImport::EnumMembers](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md), `EnumMembersWithName` discards all field and member tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="05f08-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="05f08-115">Return Value</span></span>  
  
|<span data-ttu-id="05f08-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="05f08-116">HRESULT</span></span>|<span data-ttu-id="05f08-117">Popis</span><span class="sxs-lookup"><span data-stu-id="05f08-117">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="05f08-118">`EnumTypeDefs` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="05f08-118">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="05f08-119">Neexistují žádné tokeny MemberDef výčet.</span><span class="sxs-lookup"><span data-stu-id="05f08-119">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="05f08-120">V takovém případě `pcTokens` je nula.</span><span class="sxs-lookup"><span data-stu-id="05f08-120">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="05f08-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="05f08-121">Requirements</span></span>  
 <span data-ttu-id="05f08-122">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05f08-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05f08-123">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="05f08-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="05f08-124">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="05f08-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="05f08-125">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05f08-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05f08-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="05f08-126">See also</span></span>

- [<span data-ttu-id="05f08-127">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05f08-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="05f08-128">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05f08-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
