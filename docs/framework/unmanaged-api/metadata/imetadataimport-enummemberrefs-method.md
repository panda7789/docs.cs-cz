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
ms.openlocfilehash: a08577f15a6fab0e630d40032a23c273ee935faa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59072987"
---
# <a name="imetadataimportenummemberrefs-method"></a><span data-ttu-id="5c741-102">IMetaDataImport::EnumMemberRefs – metoda</span><span class="sxs-lookup"><span data-stu-id="5c741-102">IMetaDataImport::EnumMemberRefs Method</span></span>
<span data-ttu-id="5c741-103">Vytvoří výčet MemberRef tokeny představující členů zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="5c741-103">Enumerates MemberRef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c741-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5c741-104">Syntax</span></span>  
  
```  
HRESULT EnumMemberRefs (  
   [in, out] HCORENUM    *phEnum,   
   [in]   mdToken        tkParent,   
   [out]  mdMemberRef    rMemberRefs[],   
   [in]   ULONG          cMax,   
   [out]  ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c741-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5c741-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="5c741-106">[out v] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="5c741-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="5c741-107">[in] Token TypeDef, Odkaz TypeRef, MethodDef nebo Odkaz ModuleRef pro typ, jejíž členové jsou pro provedení výčtu.</span><span class="sxs-lookup"><span data-stu-id="5c741-107">[in] A TypeDef, TypeRef, MethodDef, or ModuleRef token for the type whose members are to be enumerated.</span></span>  
  
 `rMemberRefs`  
 <span data-ttu-id="5c741-108">[out] Pole pro ukládání tokenů MemberRef.</span><span class="sxs-lookup"><span data-stu-id="5c741-108">[out] The array used to store MemberRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="5c741-109">[in] Maximální velikost `rMemberRefs` pole.</span><span class="sxs-lookup"><span data-stu-id="5c741-109">[in] The maximum size of the `rMemberRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="5c741-110">[out] Skutečný počet tokenů MemberRef vrácené v `rMemberRefs`.</span><span class="sxs-lookup"><span data-stu-id="5c741-110">[out] The actual number of MemberRef tokens returned in `rMemberRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5c741-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="5c741-111">Return Value</span></span>  
  
|<span data-ttu-id="5c741-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5c741-112">HRESULT</span></span>|<span data-ttu-id="5c741-113">Popis</span><span class="sxs-lookup"><span data-stu-id="5c741-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="5c741-114">`EnumMemberRefs` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="5c741-114">`EnumMemberRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="5c741-115">Neexistují žádné tokeny MemberRef se vytvořit výčet.</span><span class="sxs-lookup"><span data-stu-id="5c741-115">There are no MemberRef tokens to enumerate.</span></span> <span data-ttu-id="5c741-116">V takovém případě `pcTokens` je na nulu.</span><span class="sxs-lookup"><span data-stu-id="5c741-116">In that case, `pcTokens` is to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5c741-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5c741-117">Requirements</span></span>  
 <span data-ttu-id="5c741-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c741-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c741-119">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5c741-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5c741-120">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5c741-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5c741-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c741-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c741-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5c741-122">See also</span></span>

- [<span data-ttu-id="5c741-123">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5c741-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="5c741-124">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5c741-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
