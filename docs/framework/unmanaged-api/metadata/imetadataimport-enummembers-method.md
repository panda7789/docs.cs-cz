---
title: "IMetaDataImport::EnumMembers – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumMembers
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumMembers
helpviewer_keywords:
- IMetaDataImport::EnumMembers method [.NET Framework metadata]
- EnumMembers method [.NET Framework metadata]
ms.assetid: 3fb8e178-342b-4c89-9bcf-f7f834e6cb77
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aa7dabad0e555fe965cba4e5cbc69c10c9826b8e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenummembers-method"></a><span data-ttu-id="4b9e1-102">IMetaDataImport::EnumMembers – metoda</span><span class="sxs-lookup"><span data-stu-id="4b9e1-102">IMetaDataImport::EnumMembers Method</span></span>
<span data-ttu-id="4b9e1-103">Vytvoří výčet MemberDef tokeny představující členů zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="4b9e1-103">Enumerates MemberDef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b9e1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4b9e1-104">Syntax</span></span>  
  
```  
HRESULT EnumMembers (   
   [in, out]  HCORENUM    *phEnum,   
   [in]  mdTypeDef   cl,   
   [out] mdToken     rMembers[],   
   [in]  ULONG       cMax,   
   [out] ULONG       *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4b9e1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4b9e1-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="4b9e1-106">[ve out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="4b9e1-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="4b9e1-107">[v] TypeDef token představující typ, jejíž členové jsou výčet.</span><span class="sxs-lookup"><span data-stu-id="4b9e1-107">[in] A TypeDef token representing the type whose members are to be enumerated.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="4b9e1-108">[out] Pole používané pro udržení MemberDef tokenů.</span><span class="sxs-lookup"><span data-stu-id="4b9e1-108">[out] The array used to hold the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="4b9e1-109">[v] Maximální velikost `rMembers` pole.</span><span class="sxs-lookup"><span data-stu-id="4b9e1-109">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="4b9e1-110">[out] Skutečný počet MemberDef tokeny, vrátí se v `rMembers`.</span><span class="sxs-lookup"><span data-stu-id="4b9e1-110">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4b9e1-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4b9e1-111">Return Value</span></span>  
  
|<span data-ttu-id="4b9e1-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4b9e1-112">HRESULT</span></span>|<span data-ttu-id="4b9e1-113">Popis</span><span class="sxs-lookup"><span data-stu-id="4b9e1-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="4b9e1-114">`EnumMembers`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="4b9e1-114">`EnumMembers` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="4b9e1-115">Neexistují žádné MemberDef tokenů pro zobrazení výčtu.</span><span class="sxs-lookup"><span data-stu-id="4b9e1-115">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="4b9e1-116">V takovém případě `pcTokens` je nulová.</span><span class="sxs-lookup"><span data-stu-id="4b9e1-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b9e1-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4b9e1-117">Remarks</span></span>  
 <span data-ttu-id="4b9e1-118">Při vytváření výčtů kolekcí členů pro třídu, `EnumMembers` vrátí pouze členové definované přímo na třídu.</span><span class="sxs-lookup"><span data-stu-id="4b9e1-118">When enumerating collections of members for a class, `EnumMembers` returns only members defined directly on the class.</span></span> <span data-ttu-id="4b9e1-119">I v případě, že třída poskytuje implementaci pro tyto zděděné členy nevrátí žádné členy, které třídy dědí.</span><span class="sxs-lookup"><span data-stu-id="4b9e1-119">It does not return any members that the class inherits, even if the class provides an implementation for those inherited members.</span></span> <span data-ttu-id="4b9e1-120">Výčet zděděné členy, volající musí explicitně provede řetězu dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="4b9e1-120">To enumerate inherited members, the caller must explicitly walk the inheritance chain.</span></span> <span data-ttu-id="4b9e1-121">Všimněte si, že pravidla pro řetězu dědičnosti se mohou lišit v závislosti na jazyce nebo kompilátoru, která vygenerované původní metadata.</span><span class="sxs-lookup"><span data-stu-id="4b9e1-121">Note that the rules for the inheritance chain may vary depending on the language or compiler that emitted the original metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b9e1-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4b9e1-122">Requirements</span></span>  
 <span data-ttu-id="4b9e1-123">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b9e1-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b9e1-124">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4b9e1-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4b9e1-125">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4b9e1-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4b9e1-126">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b9e1-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b9e1-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="4b9e1-127">See Also</span></span>  
 [<span data-ttu-id="4b9e1-128">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4b9e1-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="4b9e1-129">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4b9e1-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
