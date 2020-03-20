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
ms.openlocfilehash: 7410f91a853f3a677a105dc2e12a86d723c9fad6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177323"
---
# <a name="imetadataimportenummemberswithname-method"></a><span data-ttu-id="1a563-102">IMetaDataImport::EnumMembersWithName – metoda</span><span class="sxs-lookup"><span data-stu-id="1a563-102">IMetaDataImport::EnumMembersWithName Method</span></span>
<span data-ttu-id="1a563-103">Výčet tokenů MemberDef představujících členy zadaného typu se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="1a563-103">Enumerates MemberDef tokens representing members of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a563-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1a563-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMembersWithName (  
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   cl,
   [in]      LPCWSTR     szName,
   [out]     mdToken     rMembers[],
   [in]      ULONG       cMax,
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a563-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1a563-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="1a563-106">[dovnitř, ven] Ukazatel na čítač výčtu.</span><span class="sxs-lookup"><span data-stu-id="1a563-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="1a563-107">[v] A TypeDef token představující typ s členy výčet.</span><span class="sxs-lookup"><span data-stu-id="1a563-107">[in] A TypeDef token representing the type with members to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="1a563-108">[v] Název člena, který omezuje rozsah čítače výčtu.</span><span class="sxs-lookup"><span data-stu-id="1a563-108">[in] The member name that limits the scope of the enumerator.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="1a563-109">[out] Pole používané k uložení tokenů MemberDef.</span><span class="sxs-lookup"><span data-stu-id="1a563-109">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="1a563-110">[v] Maximální velikost `rMembers` pole.</span><span class="sxs-lookup"><span data-stu-id="1a563-110">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="1a563-111">[out] Skutečný počet tokenů MemberDef `rMembers`vrácených v .</span><span class="sxs-lookup"><span data-stu-id="1a563-111">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a563-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1a563-112">Remarks</span></span>  
 <span data-ttu-id="1a563-113">Tato metoda vyjmenovává pole a metody, ale ne vlastnosti nebo události.</span><span class="sxs-lookup"><span data-stu-id="1a563-113">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="1a563-114">Na rozdíl od [IMetaDataImport::EnumMembers](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md), `EnumMembersWithName` zahodí všechny tokeny polí a členů, které nemají zadaný název.</span><span class="sxs-lookup"><span data-stu-id="1a563-114">Unlike [IMetaDataImport::EnumMembers](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummembers-method.md), `EnumMembersWithName` discards all field and member tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1a563-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1a563-115">Return Value</span></span>  
  
|<span data-ttu-id="1a563-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1a563-116">HRESULT</span></span>|<span data-ttu-id="1a563-117">Popis</span><span class="sxs-lookup"><span data-stu-id="1a563-117">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="1a563-118">`EnumTypeDefs`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="1a563-118">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="1a563-119">Neexistují žádné tokeny MemberDef pro výčet.</span><span class="sxs-lookup"><span data-stu-id="1a563-119">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="1a563-120">V tom `pcTokens` případě je nula.</span><span class="sxs-lookup"><span data-stu-id="1a563-120">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1a563-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1a563-121">Requirements</span></span>  
 <span data-ttu-id="1a563-122">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a563-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a563-123">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="1a563-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1a563-124">**Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1a563-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1a563-125">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a563-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a563-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="1a563-126">See also</span></span>

- [<span data-ttu-id="1a563-127">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1a563-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="1a563-128">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1a563-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
