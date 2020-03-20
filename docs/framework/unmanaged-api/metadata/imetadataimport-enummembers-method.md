---
title: IMetaDataImport::EnumMembers – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMembers
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMembers
helpviewer_keywords:
- IMetaDataImport::EnumMembers method [.NET Framework metadata]
- EnumMembers method [.NET Framework metadata]
ms.assetid: 3fb8e178-342b-4c89-9bcf-f7f834e6cb77
topic_type:
- apiref
ms.openlocfilehash: 20c7a90f27defa18a5ef311d1f3a549b81fc5c40
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175483"
---
# <a name="imetadataimportenummembers-method"></a><span data-ttu-id="237cc-102">IMetaDataImport::EnumMembers – metoda</span><span class="sxs-lookup"><span data-stu-id="237cc-102">IMetaDataImport::EnumMembers Method</span></span>
<span data-ttu-id="237cc-103">Vyjmenovává tokeny MemberDef představující členy zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="237cc-103">Enumerates MemberDef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="237cc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="237cc-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMembers (
   [in, out]  HCORENUM    *phEnum,
   [in]  mdTypeDef   cl,
   [out] mdToken     rMembers[],
   [in]  ULONG       cMax,
   [out] ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="237cc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="237cc-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="237cc-106">[dovnitř, ven] Ukazatel na čítač výčtu.</span><span class="sxs-lookup"><span data-stu-id="237cc-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="237cc-107">[v] A TypeDef token představující typ, jehož členy mají být uvedeny.</span><span class="sxs-lookup"><span data-stu-id="237cc-107">[in] A TypeDef token representing the type whose members are to be enumerated.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="237cc-108">[out] Pole používané k uložení tokenů MemberDef.</span><span class="sxs-lookup"><span data-stu-id="237cc-108">[out] The array used to hold the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="237cc-109">[v] Maximální velikost `rMembers` pole.</span><span class="sxs-lookup"><span data-stu-id="237cc-109">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="237cc-110">[out] Skutečný počet tokenů MemberDef `rMembers`vrácených v .</span><span class="sxs-lookup"><span data-stu-id="237cc-110">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="237cc-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="237cc-111">Return Value</span></span>  
  
|<span data-ttu-id="237cc-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="237cc-112">HRESULT</span></span>|<span data-ttu-id="237cc-113">Popis</span><span class="sxs-lookup"><span data-stu-id="237cc-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="237cc-114">`EnumMembers`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="237cc-114">`EnumMembers` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="237cc-115">Neexistují žádné tokeny MemberDef pro výčet.</span><span class="sxs-lookup"><span data-stu-id="237cc-115">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="237cc-116">V tom `pcTokens` případě je nula.</span><span class="sxs-lookup"><span data-stu-id="237cc-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="237cc-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="237cc-117">Remarks</span></span>  
 <span data-ttu-id="237cc-118">Při výčtu kolekce členů pro třídu vrátí `EnumMembers` pouze členy (pole a metody, ale **ne** vlastnosti nebo události) definované přímo na třídu.</span><span class="sxs-lookup"><span data-stu-id="237cc-118">When enumerating collections of members for a class, `EnumMembers` returns only members (fields and methods, but **not** properties or events) defined directly on the class.</span></span> <span data-ttu-id="237cc-119">Nevrátí žádné členy, které zdědí třídy, i v případě, že třída poskytuje implementaci pro tyto zděděné členy.</span><span class="sxs-lookup"><span data-stu-id="237cc-119">It does not return any members that the class inherits, even if the class provides an implementation for those inherited members.</span></span> <span data-ttu-id="237cc-120">Chcete-li vytvořit výčet zděděných členů, volající musí explicitně chodit řetězce dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="237cc-120">To enumerate inherited members, the caller must explicitly walk the inheritance chain.</span></span> <span data-ttu-id="237cc-121">Všimněte si, že pravidla pro řetězec dědičnosti se může lišit v závislosti na jazyku nebo kompilátoru, který vyzařoval původní metadata.</span><span class="sxs-lookup"><span data-stu-id="237cc-121">Note that the rules for the inheritance chain may vary depending on the language or compiler that emitted the original metadata.</span></span>

 <span data-ttu-id="237cc-122">Vlastnosti a události nejsou výčty . `EnumMembers`</span><span class="sxs-lookup"><span data-stu-id="237cc-122">Properties and events are not enumerated by `EnumMembers`.</span></span> <span data-ttu-id="237cc-123">Chcete-li vytvořit výčet těchto, použijte [EnumProperties](imetadataimport-enumproperties-method.md) nebo [EnumEvents](imetadataimport-enumevents-method.md).</span><span class="sxs-lookup"><span data-stu-id="237cc-123">To enumerate those, use [EnumProperties](imetadataimport-enumproperties-method.md) or [EnumEvents](imetadataimport-enumevents-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="237cc-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="237cc-124">Requirements</span></span>  
 <span data-ttu-id="237cc-125">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="237cc-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="237cc-126">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="237cc-126">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="237cc-127">**Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="237cc-127">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="237cc-128">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="237cc-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="237cc-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="237cc-129">See also</span></span>

- [<span data-ttu-id="237cc-130">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="237cc-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="237cc-131">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="237cc-131">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
