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
ms.openlocfilehash: 88b8f874400d68110fa5e8fb66ca910b8e7231e1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645961"
---
# <a name="imetadataimportenummembers-method"></a><span data-ttu-id="2c400-102">IMetaDataImport::EnumMembers – metoda</span><span class="sxs-lookup"><span data-stu-id="2c400-102">IMetaDataImport::EnumMembers Method</span></span>
<span data-ttu-id="2c400-103">Vytvoří výčet MemberDef tokeny představující členů zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="2c400-103">Enumerates MemberDef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c400-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2c400-104">Syntax</span></span>  
  
```  
HRESULT EnumMembers (   
   [in, out]  HCORENUM    *phEnum,   
   [in]  mdTypeDef   cl,   
   [out] mdToken     rMembers[],   
   [in]  ULONG       cMax,   
   [out] ULONG       *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2c400-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2c400-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="2c400-106">[out v] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="2c400-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="2c400-107">[in] Token TypeDef představující typ, jejíž členové jsou pro provedení výčtu.</span><span class="sxs-lookup"><span data-stu-id="2c400-107">[in] A TypeDef token representing the type whose members are to be enumerated.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="2c400-108">[out] Pole sloužící k uchování MemberDef tokeny.</span><span class="sxs-lookup"><span data-stu-id="2c400-108">[out] The array used to hold the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="2c400-109">[in] Maximální velikost `rMembers` pole.</span><span class="sxs-lookup"><span data-stu-id="2c400-109">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="2c400-110">[out] Skutečný počet tokenů MemberDef vrácené v `rMembers`.</span><span class="sxs-lookup"><span data-stu-id="2c400-110">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2c400-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2c400-111">Return Value</span></span>  
  
|<span data-ttu-id="2c400-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2c400-112">HRESULT</span></span>|<span data-ttu-id="2c400-113">Popis</span><span class="sxs-lookup"><span data-stu-id="2c400-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="2c400-114">`EnumMembers` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="2c400-114">`EnumMembers` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="2c400-115">Neexistují žádné tokeny MemberDef výčet.</span><span class="sxs-lookup"><span data-stu-id="2c400-115">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="2c400-116">V takovém případě `pcTokens` je nula.</span><span class="sxs-lookup"><span data-stu-id="2c400-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c400-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2c400-117">Remarks</span></span>  
 <span data-ttu-id="2c400-118">Při vytváření výčtů kolekcí členů v případě třídy `EnumMembers` vrací pouze členy definované přímo ve třídě.</span><span class="sxs-lookup"><span data-stu-id="2c400-118">When enumerating collections of members for a class, `EnumMembers` returns only members defined directly on the class.</span></span> <span data-ttu-id="2c400-119">I v případě, že třída poskytuje implementaci pro členy zděděné nevrací žádné členy, které dědí třídu.</span><span class="sxs-lookup"><span data-stu-id="2c400-119">It does not return any members that the class inherits, even if the class provides an implementation for those inherited members.</span></span> <span data-ttu-id="2c400-120">Výčet zděděné členy, volající musí explicitně provedou řetězu dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="2c400-120">To enumerate inherited members, the caller must explicitly walk the inheritance chain.</span></span> <span data-ttu-id="2c400-121">Všimněte si, že pravidla pro řetězec dědičnosti mohou lišit v závislosti na jazyk nebo kompilátor, který původní metadata, protože ho.</span><span class="sxs-lookup"><span data-stu-id="2c400-121">Note that the rules for the inheritance chain may vary depending on the language or compiler that emitted the original metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c400-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2c400-122">Requirements</span></span>  
 <span data-ttu-id="2c400-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c400-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c400-124">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2c400-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2c400-125">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2c400-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2c400-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c400-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c400-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2c400-127">See also</span></span>
- [<span data-ttu-id="2c400-128">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2c400-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="2c400-129">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2c400-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
