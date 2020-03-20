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
ms.openlocfilehash: a61254ba751e47b0089a3f7528aca337a32e2db3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175366"
---
# <a name="imetadataimportgetmemberrefprops-method"></a><span data-ttu-id="06169-102">IMetaDataImport::GetMemberRefProps – metoda</span><span class="sxs-lookup"><span data-stu-id="06169-102">IMetaDataImport::GetMemberRefProps Method</span></span>
<span data-ttu-id="06169-103">Získá metadata spojená s členem odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="06169-103">Gets metadata associated with the member referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06169-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="06169-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="06169-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="06169-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="06169-106">[v] Token MemberRef pro vrácení přidružených metadat.</span><span class="sxs-lookup"><span data-stu-id="06169-106">[in] The MemberRef token to return associated metadata for.</span></span>  
  
 `ptk`  
 <span data-ttu-id="06169-107">[out] A TypeDef nebo TypeRef nebo TypeSpec token, který představuje třídu, která deklaruje člen nebo Token ModuleRef, který představuje třídu modulu, která deklaruje člen nebo MethodDef, který představuje člen.</span><span class="sxs-lookup"><span data-stu-id="06169-107">[out] A TypeDef or TypeRef, or TypeSpec token that represents the class that declares the member, or a ModuleRef token that represents the module class that declares the member, or a MethodDef that represents the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="06169-108">[out] Vyrovnávací paměť řetězce pro název člena.</span><span class="sxs-lookup"><span data-stu-id="06169-108">[out] A string buffer for the member's name.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="06169-109">[v] Požadovaná velikost v `szMember`široké znaky .</span><span class="sxs-lookup"><span data-stu-id="06169-109">[in] The requested size in wide characters of `szMember`.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="06169-110">[out] Vrácená velikost v `szMember`široké znaky .</span><span class="sxs-lookup"><span data-stu-id="06169-110">[out] The returned size in wide characters of `szMember`.</span></span>  
  
 `ppvSibBlob`  
 <span data-ttu-id="06169-111">[out] Ukazatel na podpis binárních metadat pro člena.</span><span class="sxs-lookup"><span data-stu-id="06169-111">[out] A pointer to the binary metadata signature for the member.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="06169-112">[out] Velikost v bajtů `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="06169-112">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06169-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="06169-113">Requirements</span></span>  
 <span data-ttu-id="06169-114">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06169-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06169-115">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="06169-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="06169-116">**Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="06169-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="06169-117">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06169-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06169-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="06169-118">See also</span></span>

- [<span data-ttu-id="06169-119">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="06169-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="06169-120">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="06169-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
