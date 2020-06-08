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
ms.openlocfilehash: ea451bdd645d2d4dea4c5dd00408e0bc51804803
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492067"
---
# <a name="imetadataimportenummemberswithname-method"></a><span data-ttu-id="f5b01-102">IMetaDataImport::EnumMembersWithName – metoda</span><span class="sxs-lookup"><span data-stu-id="f5b01-102">IMetaDataImport::EnumMembersWithName Method</span></span>
<span data-ttu-id="f5b01-103">Vytvoří výčet tokenů memberDef či představujících členy zadaného typu se zadaným názvem.</span><span class="sxs-lookup"><span data-stu-id="f5b01-103">Enumerates MemberDef tokens representing members of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5b01-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f5b01-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="f5b01-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f5b01-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="f5b01-106">[in, out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="f5b01-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="f5b01-107">pro Token TypeDef představující typ s členy pro výčet.</span><span class="sxs-lookup"><span data-stu-id="f5b01-107">[in] A TypeDef token representing the type with members to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="f5b01-108">pro Název členu, který omezuje rozsah čítače.</span><span class="sxs-lookup"><span data-stu-id="f5b01-108">[in] The member name that limits the scope of the enumerator.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="f5b01-109">mimo Pole, které se používá k uložení tokenů memberDef či.</span><span class="sxs-lookup"><span data-stu-id="f5b01-109">[out] The array used to store the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="f5b01-110">pro Maximální velikost `rMembers` pole.</span><span class="sxs-lookup"><span data-stu-id="f5b01-110">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="f5b01-111">mimo Skutečný počet memberDef či tokenů vrácených v `rMembers` .</span><span class="sxs-lookup"><span data-stu-id="f5b01-111">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5b01-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f5b01-112">Remarks</span></span>  
 <span data-ttu-id="f5b01-113">Tato metoda vytváří výčet polí a metod, ale ne vlastností nebo událostí.</span><span class="sxs-lookup"><span data-stu-id="f5b01-113">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="f5b01-114">Na rozdíl od [IMetaDataImport:: enummembers –](imetadataimport-enummembers-method.md) `EnumMembersWithName` zahodí všechny tokeny Field a member, které nemají zadaný název.</span><span class="sxs-lookup"><span data-stu-id="f5b01-114">Unlike [IMetaDataImport::EnumMembers](imetadataimport-enummembers-method.md), `EnumMembersWithName` discards all field and member tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f5b01-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f5b01-115">Return Value</span></span>  
  
|<span data-ttu-id="f5b01-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f5b01-116">HRESULT</span></span>|<span data-ttu-id="f5b01-117">Description</span><span class="sxs-lookup"><span data-stu-id="f5b01-117">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="f5b01-118">`EnumTypeDefs`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="f5b01-118">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="f5b01-119">Nejsou k dispozici žádné tokeny memberDef či pro zobrazení výčtu.</span><span class="sxs-lookup"><span data-stu-id="f5b01-119">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="f5b01-120">V takovém případě `pcTokens` je nula.</span><span class="sxs-lookup"><span data-stu-id="f5b01-120">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f5b01-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f5b01-121">Requirements</span></span>  
 <span data-ttu-id="f5b01-122">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5b01-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5b01-123">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f5b01-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f5b01-124">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f5b01-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f5b01-125">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5b01-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5b01-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f5b01-126">See also</span></span>

- [<span data-ttu-id="f5b01-127">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f5b01-127">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="f5b01-128">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f5b01-128">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
