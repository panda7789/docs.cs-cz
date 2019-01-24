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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 34a6762618780b22bcd8be376209912390524578
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54592009"
---
# <a name="imetadataimportenummemberrefs-method"></a><span data-ttu-id="a79fc-102">IMetaDataImport::EnumMemberRefs – metoda</span><span class="sxs-lookup"><span data-stu-id="a79fc-102">IMetaDataImport::EnumMemberRefs Method</span></span>
<span data-ttu-id="a79fc-103">Vytvoří výčet MemberRef tokeny představující členů zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="a79fc-103">Enumerates MemberRef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a79fc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a79fc-104">Syntax</span></span>  
  
```  
HRESULT EnumMemberRefs (  
   [in, out] HCORENUM    *phEnum,   
   [in]   mdToken        tkParent,   
   [out]  mdMemberRef    rMemberRefs[],   
   [in]   ULONG          cMax,   
   [out]  ULONG          *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a79fc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a79fc-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="a79fc-106">[out v] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="a79fc-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="a79fc-107">[in] Token TypeDef, Odkaz TypeRef, MethodDef nebo Odkaz ModuleRef pro typ, jejíž členové jsou pro provedení výčtu.</span><span class="sxs-lookup"><span data-stu-id="a79fc-107">[in] A TypeDef, TypeRef, MethodDef, or ModuleRef token for the type whose members are to be enumerated.</span></span>  
  
 `rMemberRefs`  
 <span data-ttu-id="a79fc-108">[out] Pole pro ukládání tokenů MemberRef.</span><span class="sxs-lookup"><span data-stu-id="a79fc-108">[out] The array used to store MemberRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="a79fc-109">[in] Maximální velikost `rMemberRefs` pole.</span><span class="sxs-lookup"><span data-stu-id="a79fc-109">[in] The maximum size of the `rMemberRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="a79fc-110">[out] Skutečný počet tokenů MemberRef vrácené v `rMemberRefs`.</span><span class="sxs-lookup"><span data-stu-id="a79fc-110">[out] The actual number of MemberRef tokens returned in `rMemberRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a79fc-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a79fc-111">Return Value</span></span>  
  
|<span data-ttu-id="a79fc-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a79fc-112">HRESULT</span></span>|<span data-ttu-id="a79fc-113">Popis</span><span class="sxs-lookup"><span data-stu-id="a79fc-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="a79fc-114">`EnumMemberRefs` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="a79fc-114">`EnumMemberRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="a79fc-115">Neexistují žádné tokeny MemberRef se vytvořit výčet.</span><span class="sxs-lookup"><span data-stu-id="a79fc-115">There are no MemberRef tokens to enumerate.</span></span> <span data-ttu-id="a79fc-116">V takovém případě `pcTokens` je na nulu.</span><span class="sxs-lookup"><span data-stu-id="a79fc-116">In that case, `pcTokens` is to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a79fc-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a79fc-117">Requirements</span></span>  
 <span data-ttu-id="a79fc-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a79fc-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a79fc-119">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a79fc-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a79fc-120">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a79fc-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a79fc-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a79fc-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a79fc-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a79fc-122">See also</span></span>
- [<span data-ttu-id="a79fc-123">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a79fc-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="a79fc-124">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a79fc-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
