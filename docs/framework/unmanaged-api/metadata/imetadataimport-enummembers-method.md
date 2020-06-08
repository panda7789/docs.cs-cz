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
ms.openlocfilehash: cc3bc5140da0634b5172f6253de3de37bff487f1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492031"
---
# <a name="imetadataimportenummembers-method"></a><span data-ttu-id="95a60-102">IMetaDataImport::EnumMembers – metoda</span><span class="sxs-lookup"><span data-stu-id="95a60-102">IMetaDataImport::EnumMembers Method</span></span>
<span data-ttu-id="95a60-103">Vytvoří výčet tokenů memberDef či představujících členy zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="95a60-103">Enumerates MemberDef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95a60-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95a60-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMembers (
   [in, out]  HCORENUM    *phEnum,
   [in]  mdTypeDef   cl,
   [out] mdToken     rMembers[],
   [in]  ULONG       cMax,
   [out] ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95a60-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="95a60-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="95a60-106">[in, out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="95a60-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="95a60-107">pro Token TypeDef představující typ, jehož členy mají být vyčísleny.</span><span class="sxs-lookup"><span data-stu-id="95a60-107">[in] A TypeDef token representing the type whose members are to be enumerated.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="95a60-108">mimo Pole použité pro ukládání tokenů memberDef či.</span><span class="sxs-lookup"><span data-stu-id="95a60-108">[out] The array used to hold the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="95a60-109">pro Maximální velikost `rMembers` pole.</span><span class="sxs-lookup"><span data-stu-id="95a60-109">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="95a60-110">mimo Skutečný počet memberDef či tokenů vrácených v `rMembers` .</span><span class="sxs-lookup"><span data-stu-id="95a60-110">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="95a60-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="95a60-111">Return Value</span></span>  
  
|<span data-ttu-id="95a60-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="95a60-112">HRESULT</span></span>|<span data-ttu-id="95a60-113">Description</span><span class="sxs-lookup"><span data-stu-id="95a60-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="95a60-114">`EnumMembers`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="95a60-114">`EnumMembers` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="95a60-115">Nejsou k dispozici žádné tokeny memberDef či pro zobrazení výčtu.</span><span class="sxs-lookup"><span data-stu-id="95a60-115">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="95a60-116">V takovém případě `pcTokens` je nula.</span><span class="sxs-lookup"><span data-stu-id="95a60-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95a60-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="95a60-117">Remarks</span></span>  
 <span data-ttu-id="95a60-118">Při vytváření výčtu kolekcí členů pro třídu `EnumMembers` vrátí pouze členy (pole a metody, ale **ne** vlastnosti nebo události) definované přímo na třídu.</span><span class="sxs-lookup"><span data-stu-id="95a60-118">When enumerating collections of members for a class, `EnumMembers` returns only members (fields and methods, but **not** properties or events) defined directly on the class.</span></span> <span data-ttu-id="95a60-119">Nevrací žádné členy, které třída dědí, a to i v případě, že třída poskytuje implementaci pro tyto zděděné členy.</span><span class="sxs-lookup"><span data-stu-id="95a60-119">It does not return any members that the class inherits, even if the class provides an implementation for those inherited members.</span></span> <span data-ttu-id="95a60-120">Chcete-li vytvořit výčet zděděných členů, volající musí explicitně procházet řetěz dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="95a60-120">To enumerate inherited members, the caller must explicitly walk the inheritance chain.</span></span> <span data-ttu-id="95a60-121">Všimněte si, že pravidla pro řetěz dědičnosti se mohou lišit v závislosti na jazyku nebo kompilátoru, který vyvolal původní metadata.</span><span class="sxs-lookup"><span data-stu-id="95a60-121">Note that the rules for the inheritance chain may vary depending on the language or compiler that emitted the original metadata.</span></span>

 <span data-ttu-id="95a60-122">Vlastnosti a události nejsou vyčísleny pomocí `EnumMembers` .</span><span class="sxs-lookup"><span data-stu-id="95a60-122">Properties and events are not enumerated by `EnumMembers`.</span></span> <span data-ttu-id="95a60-123">K zobrazení výčtu použijte [enumproperties –](imetadataimport-enumproperties-method.md) nebo [enumevents –](imetadataimport-enumevents-method.md).</span><span class="sxs-lookup"><span data-stu-id="95a60-123">To enumerate those, use [EnumProperties](imetadataimport-enumproperties-method.md) or [EnumEvents](imetadataimport-enumevents-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="95a60-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="95a60-124">Requirements</span></span>  
 <span data-ttu-id="95a60-125">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95a60-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95a60-126">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="95a60-126">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="95a60-127">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="95a60-127">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="95a60-128">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95a60-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95a60-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="95a60-129">See also</span></span>

- [<span data-ttu-id="95a60-130">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="95a60-130">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="95a60-131">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="95a60-131">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
