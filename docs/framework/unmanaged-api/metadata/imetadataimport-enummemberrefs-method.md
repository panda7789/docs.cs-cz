---
title: "IMetaDataImport::EnumMemberRefs – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumMemberRefs
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumMemberRefs
helpviewer_keywords:
- EnumMemberRefs method [.NET Framework metadata]
- IMetaDataImport::EnumMemberRefs method [.NET Framework metadata]
ms.assetid: e97c97a6-6e4f-41f5-9af1-9b3cf3bdbd6b
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ea308db566e37d10cccdc2777b5a2374408a8ea6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportenummemberrefs-method"></a><span data-ttu-id="04a44-102">IMetaDataImport::EnumMemberRefs – metoda</span><span class="sxs-lookup"><span data-stu-id="04a44-102">IMetaDataImport::EnumMemberRefs Method</span></span>
<span data-ttu-id="04a44-103">Vytvoří výčet MemberRef tokeny představující členů zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="04a44-103">Enumerates MemberRef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04a44-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04a44-104">Syntax</span></span>  
  
```  
HRESULT EnumMemberRefs (  
   [in, out] HCORENUM    *phEnum,   
   [in]   mdToken        tkParent,   
   [out]  mdMemberRef    rMemberRefs[],   
   [in]   ULONG          cMax,   
   [out]  ULONG          *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="04a44-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="04a44-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="04a44-106">[ve out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="04a44-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="04a44-107">[v] TypeDef, Odkaz TypeRef, MethodDef nebo Odkaz ModuleRef token pro typ, jejíž členové jsou výčet.</span><span class="sxs-lookup"><span data-stu-id="04a44-107">[in] A TypeDef, TypeRef, MethodDef, or ModuleRef token for the type whose members are to be enumerated.</span></span>  
  
 `rMemberRefs`  
 <span data-ttu-id="04a44-108">[out] Pole používá k ukládání MemberRef tokeny.</span><span class="sxs-lookup"><span data-stu-id="04a44-108">[out] The array used to store MemberRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="04a44-109">[v] Maximální velikost `rMemberRefs` pole.</span><span class="sxs-lookup"><span data-stu-id="04a44-109">[in] The maximum size of the `rMemberRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="04a44-110">[out] Skutečný počet MemberRef tokeny, vrátí se v `rMemberRefs`.</span><span class="sxs-lookup"><span data-stu-id="04a44-110">[out] The actual number of MemberRef tokens returned in `rMemberRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="04a44-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="04a44-111">Return Value</span></span>  
  
|<span data-ttu-id="04a44-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="04a44-112">HRESULT</span></span>|<span data-ttu-id="04a44-113">Popis</span><span class="sxs-lookup"><span data-stu-id="04a44-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="04a44-114">`EnumMemberRefs`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="04a44-114">`EnumMemberRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="04a44-115">Neexistují žádné MemberRef tokenů pro zobrazení výčtu.</span><span class="sxs-lookup"><span data-stu-id="04a44-115">There are no MemberRef tokens to enumerate.</span></span> <span data-ttu-id="04a44-116">V takovém případě `pcTokens` je nula.</span><span class="sxs-lookup"><span data-stu-id="04a44-116">In that case, `pcTokens` is to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="04a44-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="04a44-117">Requirements</span></span>  
 <span data-ttu-id="04a44-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04a44-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04a44-119">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="04a44-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="04a44-120">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="04a44-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="04a44-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04a44-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04a44-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="04a44-122">See Also</span></span>  
 [<span data-ttu-id="04a44-123">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="04a44-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="04a44-124">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="04a44-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
