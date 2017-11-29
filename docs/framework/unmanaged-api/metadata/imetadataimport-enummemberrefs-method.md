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
ms.openlocfilehash: a9a47d723aaf7dd83bc488a07b040b43a206be55
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenummemberrefs-method"></a><span data-ttu-id="e277a-102">IMetaDataImport::EnumMemberRefs – metoda</span><span class="sxs-lookup"><span data-stu-id="e277a-102">IMetaDataImport::EnumMemberRefs Method</span></span>
<span data-ttu-id="e277a-103">Vytvoří výčet MemberRef tokeny představující členů zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="e277a-103">Enumerates MemberRef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e277a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e277a-104">Syntax</span></span>  
  
```  
HRESULT EnumMemberRefs (  
   [in, out] HCORENUM    *phEnum,   
   [in]   mdToken        tkParent,   
   [out]  mdMemberRef    rMemberRefs[],   
   [in]   ULONG          cMax,   
   [out]  ULONG          *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e277a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e277a-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="e277a-106">[ve out] Ukazatel na enumerátor.</span><span class="sxs-lookup"><span data-stu-id="e277a-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="e277a-107">[v] TypeDef, Odkaz TypeRef, MethodDef nebo Odkaz ModuleRef token pro typ, jejíž členové jsou výčet.</span><span class="sxs-lookup"><span data-stu-id="e277a-107">[in] A TypeDef, TypeRef, MethodDef, or ModuleRef token for the type whose members are to be enumerated.</span></span>  
  
 `rMemberRefs`  
 <span data-ttu-id="e277a-108">[out] Pole používá k ukládání MemberRef tokeny.</span><span class="sxs-lookup"><span data-stu-id="e277a-108">[out] The array used to store MemberRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="e277a-109">[v] Maximální velikost `rMemberRefs` pole.</span><span class="sxs-lookup"><span data-stu-id="e277a-109">[in] The maximum size of the `rMemberRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="e277a-110">[out] Skutečný počet MemberRef tokeny, vrátí se v `rMemberRefs`.</span><span class="sxs-lookup"><span data-stu-id="e277a-110">[out] The actual number of MemberRef tokens returned in `rMemberRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e277a-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e277a-111">Return Value</span></span>  
  
|<span data-ttu-id="e277a-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e277a-112">HRESULT</span></span>|<span data-ttu-id="e277a-113">Popis</span><span class="sxs-lookup"><span data-stu-id="e277a-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="e277a-114">`EnumMemberRefs`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="e277a-114">`EnumMemberRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="e277a-115">Neexistují žádné MemberRef tokenů pro zobrazení výčtu.</span><span class="sxs-lookup"><span data-stu-id="e277a-115">There are no MemberRef tokens to enumerate.</span></span> <span data-ttu-id="e277a-116">V takovém případě `pcTokens` je nula.</span><span class="sxs-lookup"><span data-stu-id="e277a-116">In that case, `pcTokens` is to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e277a-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e277a-117">Requirements</span></span>  
 <span data-ttu-id="e277a-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e277a-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e277a-119">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e277a-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e277a-120">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e277a-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e277a-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e277a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e277a-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="e277a-122">See Also</span></span>  
 [<span data-ttu-id="e277a-123">Imetadataimport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e277a-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="e277a-124">Imetadataimport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e277a-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
