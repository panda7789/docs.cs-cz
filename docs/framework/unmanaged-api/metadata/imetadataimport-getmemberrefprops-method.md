---
title: "IMetaDataImport::GetMemberRefProps – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetMemberRefProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetMemberRefProps
helpviewer_keywords:
- GetMemberRefProps method [.NET Framework metadata]
- IMetaDataImport::GetMemberRefProps method [.NET Framework metadata]
ms.assetid: 0ea73055-ece0-4151-a094-414c88ef8941
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d6cd229d9286dfe9c12a4c6f7e171f8bb634fcc0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetmemberrefprops-method"></a><span data-ttu-id="0bd5d-102">IMetaDataImport::GetMemberRefProps – metoda</span><span class="sxs-lookup"><span data-stu-id="0bd5d-102">IMetaDataImport::GetMemberRefProps Method</span></span>
<span data-ttu-id="0bd5d-103">Získá metadata spojených se členem odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="0bd5d-103">Gets metadata associated with the member referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bd5d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0bd5d-104">Syntax</span></span>  
  
```  
HRESULT GetMemberRefProps (  
   [in]  mdMemberRef       mr,   
   [out] mdToken           *ptk,   
   [out] LPWSTR            szMember,   
   [in]  ULONG             cchMember,   
   [out] ULONG             *pchMember,   
   [out] PCCOR_SIGNATURE   *ppvSigBlob,   
   [out] ULONG             *pbSig   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0bd5d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0bd5d-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="0bd5d-106">[v] Token MemberRef vrátit související metadata pro.</span><span class="sxs-lookup"><span data-stu-id="0bd5d-106">[in] The MemberRef token to return associated metadata for.</span></span>  
  
 `ptk`  
 <span data-ttu-id="0bd5d-107">[out] TypeDef nebo Odkaz TypeRef nebo typ TypeSpec token, který představuje třídu, který deklaruje člena nebo Odkaz ModuleRef token, který představuje třídu modul, který deklaruje člena nebo MethodDef, který představuje člen.</span><span class="sxs-lookup"><span data-stu-id="0bd5d-107">[out] A TypeDef or TypeRef, or TypeSpec token that represents the class that declares the member, or a ModuleRef token that represents the module class that declares the member, or a MethodDef that represents the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="0bd5d-108">[out] Vyrovnávací paměti řetězců pro název člena.</span><span class="sxs-lookup"><span data-stu-id="0bd5d-108">[out] A string buffer for the member's name.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="0bd5d-109">[v] Požadovaná velikost v široké znaky `szMember`.</span><span class="sxs-lookup"><span data-stu-id="0bd5d-109">[in] The requested size in wide characters of `szMember`.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="0bd5d-110">[out] Vrácený velikost v široké znaky `szMember`.</span><span class="sxs-lookup"><span data-stu-id="0bd5d-110">[out] The returned size in wide characters of `szMember`.</span></span>  
  
 `ppvSibBlob`  
 <span data-ttu-id="0bd5d-111">[out] Ukazatel na binární metadata podpis pro člena.</span><span class="sxs-lookup"><span data-stu-id="0bd5d-111">[out] A pointer to the binary metadata signature for the member.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="0bd5d-112">[out] Velikost v bajtech `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="0bd5d-112">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0bd5d-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0bd5d-113">Requirements</span></span>  
 <span data-ttu-id="0bd5d-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0bd5d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0bd5d-115">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0bd5d-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0bd5d-116">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0bd5d-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0bd5d-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0bd5d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bd5d-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="0bd5d-118">See Also</span></span>  
 [<span data-ttu-id="0bd5d-119">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0bd5d-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="0bd5d-120">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0bd5d-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
