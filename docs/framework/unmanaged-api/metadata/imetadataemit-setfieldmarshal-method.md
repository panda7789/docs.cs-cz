---
title: IMetaDataEmit::SetFieldMarshal – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldMarshal
helpviewer_keywords:
- SetFieldMarshal method [.NET Framework metadata]
- IMetaDataEmit::SetFieldMarshal method [.NET Framework metadata]
ms.assetid: be232314-7f69-4855-bfab-63361bd22307
topic_type:
- apiref
ms.openlocfilehash: 1037cd4210605192870d43d88979b89af6536380
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175652"
---
# <a name="imetadataemitsetfieldmarshal-method"></a><span data-ttu-id="d9b48-102">IMetaDataEmit::SetFieldMarshal – metoda</span><span class="sxs-lookup"><span data-stu-id="d9b48-102">IMetaDataEmit::SetFieldMarshal Method</span></span>
<span data-ttu-id="d9b48-103">Nastaví informace o zařazování PInvoke pro pole, metodu return nebo parametr metody odkazující zadaným tokenem.</span><span class="sxs-lookup"><span data-stu-id="d9b48-103">Sets the PInvoke marshaling information for the field, method return, or method parameter referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9b48-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d9b48-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldMarshal (  
    [in]  mdToken          tk,
    [in]  PCCOR_SIGNATURE  pvNativeType,
    [in]  ULONG            cbNativeType
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9b48-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d9b48-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="d9b48-106">[v] Token pro cílovou položku dat.</span><span class="sxs-lookup"><span data-stu-id="d9b48-106">[in] The token for target data item.</span></span> <span data-ttu-id="d9b48-107">Toto je `mdFieldDef` buď `mdParamDef` token nebo.</span><span class="sxs-lookup"><span data-stu-id="d9b48-107">This is either a `mdFieldDef` or a `mdParamDef` token.</span></span>  
  
 `pvNativeType`  
 <span data-ttu-id="d9b48-108">[v] Podpis pro nespravovaný typ.</span><span class="sxs-lookup"><span data-stu-id="d9b48-108">[in] The signature for unmanaged type.</span></span>  
  
 `cbNativeType`  
 <span data-ttu-id="d9b48-109">[v] Počet bajtů v `pvNativeType`.</span><span class="sxs-lookup"><span data-stu-id="d9b48-109">[in] The count of bytes in `pvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9b48-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d9b48-110">Requirements</span></span>  
 <span data-ttu-id="d9b48-111">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9b48-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9b48-112">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="d9b48-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d9b48-113">**Knihovna:** Používá se jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d9b48-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d9b48-114">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9b48-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9b48-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="d9b48-115">See also</span></span>

- [<span data-ttu-id="d9b48-116">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d9b48-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="d9b48-117">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d9b48-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
