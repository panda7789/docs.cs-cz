---
title: IMetaDataImport::EnumMemberRefs – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMemberRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMemberRefs
helpviewer_keywords:
- EnumMemberRefs method [.NET Framework metadata]
- IMetaDataImport::EnumMemberRefs method [.NET Framework metadata]
ms.assetid: e97c97a6-6e4f-41f5-9af1-9b3cf3bdbd6b
topic_type:
- apiref
ms.openlocfilehash: b8a65b0748fec0e474d8b3b5dc03473fbd716108
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177335"
---
# <a name="imetadataimportenummemberrefs-method"></a><span data-ttu-id="e33d5-102">IMetaDataImport::EnumMemberRefs – metoda</span><span class="sxs-lookup"><span data-stu-id="e33d5-102">IMetaDataImport::EnumMemberRefs Method</span></span>
<span data-ttu-id="e33d5-103">Výčet Tokeny MemberRef představující členy zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="e33d5-103">Enumerates MemberRef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e33d5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e33d5-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemberRefs (  
   [in, out] HCORENUM    *phEnum,
   [in]   mdToken        tkParent,
   [out]  mdMemberRef    rMemberRefs[],
   [in]   ULONG          cMax,
   [out]  ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e33d5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e33d5-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="e33d5-106">[dovnitř, ven] Ukazatel na čítač výčtu.</span><span class="sxs-lookup"><span data-stu-id="e33d5-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="e33d5-107">[v] A TypeDef, TypeRef, MethodDef nebo ModuleRef token pro typ, jehož členy mají být uvedeny ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="e33d5-107">[in] A TypeDef, TypeRef, MethodDef, or ModuleRef token for the type whose members are to be enumerated.</span></span>  
  
 `rMemberRefs`  
 <span data-ttu-id="e33d5-108">[out] Pole používané k ukládání tokenů MemberRef.</span><span class="sxs-lookup"><span data-stu-id="e33d5-108">[out] The array used to store MemberRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="e33d5-109">[v] Maximální velikost `rMemberRefs` pole.</span><span class="sxs-lookup"><span data-stu-id="e33d5-109">[in] The maximum size of the `rMemberRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="e33d5-110">[out] Skutečný počet Tokenů MemberRef `rMemberRefs`vrácených v .</span><span class="sxs-lookup"><span data-stu-id="e33d5-110">[out] The actual number of MemberRef tokens returned in `rMemberRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e33d5-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e33d5-111">Return Value</span></span>  
  
|<span data-ttu-id="e33d5-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e33d5-112">HRESULT</span></span>|<span data-ttu-id="e33d5-113">Popis</span><span class="sxs-lookup"><span data-stu-id="e33d5-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="e33d5-114">`EnumMemberRefs`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="e33d5-114">`EnumMemberRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="e33d5-115">Neexistují žádné MemberRef tokeny k výčetu.</span><span class="sxs-lookup"><span data-stu-id="e33d5-115">There are no MemberRef tokens to enumerate.</span></span> <span data-ttu-id="e33d5-116">V tom `pcTokens` případě je na nulu.</span><span class="sxs-lookup"><span data-stu-id="e33d5-116">In that case, `pcTokens` is to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e33d5-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e33d5-117">Requirements</span></span>  
 <span data-ttu-id="e33d5-118">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e33d5-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e33d5-119">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="e33d5-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e33d5-120">**Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e33d5-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e33d5-121">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e33d5-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e33d5-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="e33d5-122">See also</span></span>

- [<span data-ttu-id="e33d5-123">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e33d5-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="e33d5-124">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e33d5-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
