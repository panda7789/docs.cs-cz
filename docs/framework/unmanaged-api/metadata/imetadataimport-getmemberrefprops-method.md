---
title: IMetaDataImport::GetMemberRefProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMemberRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMemberRefProps
helpviewer_keywords:
- GetMemberRefProps method [.NET Framework metadata]
- IMetaDataImport::GetMemberRefProps method [.NET Framework metadata]
ms.assetid: 0ea73055-ece0-4151-a094-414c88ef8941
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a2c431abb7a4a872454b9c2689ee195ed36ef236
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777712"
---
# <a name="imetadataimportgetmemberrefprops-method"></a><span data-ttu-id="147bd-102">IMetaDataImport::GetMemberRefProps – metoda</span><span class="sxs-lookup"><span data-stu-id="147bd-102">IMetaDataImport::GetMemberRefProps Method</span></span>
<span data-ttu-id="147bd-103">Získá metadata přidružená k členu odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="147bd-103">Gets metadata associated with the member referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="147bd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="147bd-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="147bd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="147bd-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="147bd-106">[in] Token MemberRef vrátit související metadata pro.</span><span class="sxs-lookup"><span data-stu-id="147bd-106">[in] The MemberRef token to return associated metadata for.</span></span>  
  
 `ptk`  
 <span data-ttu-id="147bd-107">[out] Token TypeDef nebo TypeRef nebo token TypeSpec, který představuje třídu, která deklaruje člen, nebo Odkaz ModuleRef token, který představuje třídu modulu, který deklaruje člen nebo typu MethodDef, který představuje člena.</span><span class="sxs-lookup"><span data-stu-id="147bd-107">[out] A TypeDef or TypeRef, or TypeSpec token that represents the class that declares the member, or a ModuleRef token that represents the module class that declares the member, or a MethodDef that represents the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="147bd-108">[out] Vyrovnávací paměti řetězce pro název člena.</span><span class="sxs-lookup"><span data-stu-id="147bd-108">[out] A string buffer for the member's name.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="147bd-109">[in] Požadovaná velikost v širokých znaků `szMember`.</span><span class="sxs-lookup"><span data-stu-id="147bd-109">[in] The requested size in wide characters of `szMember`.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="147bd-110">[out] Velikost vrácené v širokých znaků `szMember`.</span><span class="sxs-lookup"><span data-stu-id="147bd-110">[out] The returned size in wide characters of `szMember`.</span></span>  
  
 `ppvSibBlob`  
 <span data-ttu-id="147bd-111">[out] Ukazatel na binární metadat podpis pro člena.</span><span class="sxs-lookup"><span data-stu-id="147bd-111">[out] A pointer to the binary metadata signature for the member.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="147bd-112">[out] Velikost v bajtech `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="147bd-112">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="147bd-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="147bd-113">Requirements</span></span>  
 <span data-ttu-id="147bd-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="147bd-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="147bd-115">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="147bd-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="147bd-116">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="147bd-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="147bd-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="147bd-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="147bd-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="147bd-118">See also</span></span>

- [<span data-ttu-id="147bd-119">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="147bd-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="147bd-120">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="147bd-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
