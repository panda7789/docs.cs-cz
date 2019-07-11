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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 50035799fcfa4c4b08404d63fe91e7dba85722fa
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758832"
---
# <a name="imetadataimportenummembers-method"></a><span data-ttu-id="6e6b9-102">IMetaDataImport::EnumMembers – metoda</span><span class="sxs-lookup"><span data-stu-id="6e6b9-102">IMetaDataImport::EnumMembers Method</span></span>
<span data-ttu-id="6e6b9-103">Vytvoří výčet MemberDef tokeny představující členů zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="6e6b9-103">Enumerates MemberDef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e6b9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6e6b9-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMembers (   
   [in, out]  HCORENUM    *phEnum,   
   [in]  mdTypeDef   cl,   
   [out] mdToken     rMembers[],   
   [in]  ULONG       cMax,   
   [out] ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e6b9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6e6b9-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="6e6b9-106">[out v] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="6e6b9-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="6e6b9-107">[in] Token TypeDef představující typ, jejíž členové jsou pro provedení výčtu.</span><span class="sxs-lookup"><span data-stu-id="6e6b9-107">[in] A TypeDef token representing the type whose members are to be enumerated.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="6e6b9-108">[out] Pole sloužící k uchování MemberDef tokeny.</span><span class="sxs-lookup"><span data-stu-id="6e6b9-108">[out] The array used to hold the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="6e6b9-109">[in] Maximální velikost `rMembers` pole.</span><span class="sxs-lookup"><span data-stu-id="6e6b9-109">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="6e6b9-110">[out] Skutečný počet tokenů MemberDef vrácené v `rMembers`.</span><span class="sxs-lookup"><span data-stu-id="6e6b9-110">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6e6b9-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6e6b9-111">Return Value</span></span>  
  
|<span data-ttu-id="6e6b9-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6e6b9-112">HRESULT</span></span>|<span data-ttu-id="6e6b9-113">Popis</span><span class="sxs-lookup"><span data-stu-id="6e6b9-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="6e6b9-114">`EnumMembers` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="6e6b9-114">`EnumMembers` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="6e6b9-115">Neexistují žádné tokeny MemberDef výčet.</span><span class="sxs-lookup"><span data-stu-id="6e6b9-115">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="6e6b9-116">V takovém případě `pcTokens` je nula.</span><span class="sxs-lookup"><span data-stu-id="6e6b9-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e6b9-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6e6b9-117">Remarks</span></span>  
 <span data-ttu-id="6e6b9-118">Při vytváření výčtů kolekcí členů v případě třídy `EnumMembers` vrací pouze členy (polím a metodám, ale **není** vlastnosti nebo události) definované přímo ve třídě.</span><span class="sxs-lookup"><span data-stu-id="6e6b9-118">When enumerating collections of members for a class, `EnumMembers` returns only members (fields and methods, but **not** properties or events) defined directly on the class.</span></span> <span data-ttu-id="6e6b9-119">I v případě, že třída poskytuje implementaci pro členy zděděné nevrací žádné členy, které dědí třídu.</span><span class="sxs-lookup"><span data-stu-id="6e6b9-119">It does not return any members that the class inherits, even if the class provides an implementation for those inherited members.</span></span> <span data-ttu-id="6e6b9-120">Výčet zděděné členy, volající musí explicitně provedou řetězu dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="6e6b9-120">To enumerate inherited members, the caller must explicitly walk the inheritance chain.</span></span> <span data-ttu-id="6e6b9-121">Všimněte si, že pravidla pro řetězec dědičnosti mohou lišit v závislosti na jazyk nebo kompilátor, který původní metadata, protože ho.</span><span class="sxs-lookup"><span data-stu-id="6e6b9-121">Note that the rules for the inheritance chain may vary depending on the language or compiler that emitted the original metadata.</span></span>
 
 <span data-ttu-id="6e6b9-122">Vlastnosti a události, které nejsou ve výčtu `EnumMembers`.</span><span class="sxs-lookup"><span data-stu-id="6e6b9-122">Properties and events are not enumerated by `EnumMembers`.</span></span> <span data-ttu-id="6e6b9-123">Chcete-li vytvořit výčet ty, použijte [enumproperties –](imetadataimport-enumproperties-method.md) nebo [enumevents –](imetadataimport-enumevents-method.md).</span><span class="sxs-lookup"><span data-stu-id="6e6b9-123">To enumerate those, use [EnumProperties](imetadataimport-enumproperties-method.md) or [EnumEvents](imetadataimport-enumevents-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="6e6b9-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6e6b9-124">Requirements</span></span>  
 <span data-ttu-id="6e6b9-125">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e6b9-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e6b9-126">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6e6b9-126">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6e6b9-127">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6e6b9-127">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6e6b9-128">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e6b9-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e6b9-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6e6b9-129">See also</span></span>

- [<span data-ttu-id="6e6b9-130">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6e6b9-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="6e6b9-131">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6e6b9-131">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
