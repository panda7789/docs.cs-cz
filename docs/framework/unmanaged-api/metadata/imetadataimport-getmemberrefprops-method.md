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
ms.openlocfilehash: 00693f1a87334620442e8865e76183b2dab68878
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503611"
---
# <a name="imetadataimportgetmemberrefprops-method"></a><span data-ttu-id="ca4f4-102">IMetaDataImport::GetMemberRefProps – metoda</span><span class="sxs-lookup"><span data-stu-id="ca4f4-102">IMetaDataImport::GetMemberRefProps Method</span></span>
<span data-ttu-id="ca4f4-103">Načte metadata přidružená k členu, na který odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="ca4f4-103">Gets metadata associated with the member referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca4f4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ca4f4-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="ca4f4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ca4f4-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="ca4f4-106">pro Token MemberRef, pro který mají být vrácena přidružená metadata</span><span class="sxs-lookup"><span data-stu-id="ca4f4-106">[in] The MemberRef token to return associated metadata for.</span></span>  
  
 `ptk`  
 <span data-ttu-id="ca4f4-107">mimo Token TypeDef nebo TypeRef nebo token token TypeSpec, který představuje třídu, která deklaruje člen, nebo token Odkaz ModuleRef, který reprezentuje třídu modulu, který deklaruje člen nebo prvek MethodDef, který představuje člena.</span><span class="sxs-lookup"><span data-stu-id="ca4f4-107">[out] A TypeDef or TypeRef, or TypeSpec token that represents the class that declares the member, or a ModuleRef token that represents the module class that declares the member, or a MethodDef that represents the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="ca4f4-108">mimo Vyrovnávací paměť řetězce pro název člena.</span><span class="sxs-lookup"><span data-stu-id="ca4f4-108">[out] A string buffer for the member's name.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="ca4f4-109">pro Požadovaná velikost v různých znacích `szMember` .</span><span class="sxs-lookup"><span data-stu-id="ca4f4-109">[in] The requested size in wide characters of `szMember`.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="ca4f4-110">mimo Vrácená velikost v různých znacích `szMember` .</span><span class="sxs-lookup"><span data-stu-id="ca4f4-110">[out] The returned size in wide characters of `szMember`.</span></span>  
  
 `ppvSibBlob`  
 <span data-ttu-id="ca4f4-111">mimo Ukazatel na binární podpis metadat pro člena.</span><span class="sxs-lookup"><span data-stu-id="ca4f4-111">[out] A pointer to the binary metadata signature for the member.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="ca4f4-112">mimo Velikost v bajtech `ppvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="ca4f4-112">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca4f4-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ca4f4-113">Requirements</span></span>  
 <span data-ttu-id="ca4f4-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca4f4-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca4f4-115">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ca4f4-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ca4f4-116">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ca4f4-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ca4f4-117">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca4f4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca4f4-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ca4f4-118">See also</span></span>

- [<span data-ttu-id="ca4f4-119">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ca4f4-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="ca4f4-120">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ca4f4-120">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
