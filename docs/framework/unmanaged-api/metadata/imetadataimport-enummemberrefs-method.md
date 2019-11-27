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
ms.openlocfilehash: 743b6bed1a5d62f5214b8366b1a3c6e4ebecb98b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441714"
---
# <a name="imetadataimportenummemberrefs-method"></a><span data-ttu-id="b9fe4-102">IMetaDataImport::EnumMemberRefs – metoda</span><span class="sxs-lookup"><span data-stu-id="b9fe4-102">IMetaDataImport::EnumMemberRefs Method</span></span>
<span data-ttu-id="b9fe4-103">Vytvoří výčet tokenů MemberRef představujících členy zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="b9fe4-103">Enumerates MemberRef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9fe4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b9fe4-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemberRefs (  
   [in, out] HCORENUM    *phEnum,   
   [in]   mdToken        tkParent,   
   [out]  mdMemberRef    rMemberRefs[],   
   [in]   ULONG          cMax,   
   [out]  ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9fe4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b9fe4-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="b9fe4-106">[in, out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="b9fe4-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="b9fe4-107">pro Token TypeDef, TypeRef, MethodDef nebo odkaz ModuleRef pro typ, jehož členy mají být vyčísleny.</span><span class="sxs-lookup"><span data-stu-id="b9fe4-107">[in] A TypeDef, TypeRef, MethodDef, or ModuleRef token for the type whose members are to be enumerated.</span></span>  
  
 `rMemberRefs`  
 <span data-ttu-id="b9fe4-108">mimo Pole použité pro ukládání tokenů MemberRef</span><span class="sxs-lookup"><span data-stu-id="b9fe4-108">[out] The array used to store MemberRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="b9fe4-109">pro Maximální velikost `rMemberRefs` pole</span><span class="sxs-lookup"><span data-stu-id="b9fe4-109">[in] The maximum size of the `rMemberRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="b9fe4-110">mimo Skutečný počet tokenů MemberRef vrácených v `rMemberRefs`.</span><span class="sxs-lookup"><span data-stu-id="b9fe4-110">[out] The actual number of MemberRef tokens returned in `rMemberRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b9fe4-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b9fe4-111">Return Value</span></span>  
  
|<span data-ttu-id="b9fe4-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b9fe4-112">HRESULT</span></span>|<span data-ttu-id="b9fe4-113">Popis</span><span class="sxs-lookup"><span data-stu-id="b9fe4-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="b9fe4-114">`EnumMemberRefs` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="b9fe4-114">`EnumMemberRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="b9fe4-115">Pro výčet nejsou k dispozici žádné tokeny MemberRef.</span><span class="sxs-lookup"><span data-stu-id="b9fe4-115">There are no MemberRef tokens to enumerate.</span></span> <span data-ttu-id="b9fe4-116">V takovém případě je `pcTokens` nula.</span><span class="sxs-lookup"><span data-stu-id="b9fe4-116">In that case, `pcTokens` is to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b9fe4-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b9fe4-117">Requirements</span></span>  
 <span data-ttu-id="b9fe4-118">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9fe4-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9fe4-119">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b9fe4-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b9fe4-120">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b9fe4-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b9fe4-121">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9fe4-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9fe4-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b9fe4-122">See also</span></span>

- [<span data-ttu-id="b9fe4-123">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b9fe4-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="b9fe4-124">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b9fe4-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
