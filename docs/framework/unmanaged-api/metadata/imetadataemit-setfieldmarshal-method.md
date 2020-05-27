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
ms.openlocfilehash: d0066c6590a9e0cf278e036111c2739f7cfaf679
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84003903"
---
# <a name="imetadataemitsetfieldmarshal-method"></a><span data-ttu-id="412f4-102">IMetaDataEmit::SetFieldMarshal – metoda</span><span class="sxs-lookup"><span data-stu-id="412f4-102">IMetaDataEmit::SetFieldMarshal Method</span></span>
<span data-ttu-id="412f4-103">Nastaví informace o zařazování PInvoke pro pole, návrat metody nebo parametr metody, na který odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="412f4-103">Sets the PInvoke marshaling information for the field, method return, or method parameter referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="412f4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="412f4-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldMarshal (  
    [in]  mdToken          tk,
    [in]  PCCOR_SIGNATURE  pvNativeType,
    [in]  ULONG            cbNativeType
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="412f4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="412f4-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="412f4-106">pro Token pro cílovou datovou položku</span><span class="sxs-lookup"><span data-stu-id="412f4-106">[in] The token for target data item.</span></span> <span data-ttu-id="412f4-107">Toto je buď `mdFieldDef` token, nebo `mdParamDef` .</span><span class="sxs-lookup"><span data-stu-id="412f4-107">This is either a `mdFieldDef` or a `mdParamDef` token.</span></span>  
  
 `pvNativeType`  
 <span data-ttu-id="412f4-108">pro Podpis pro nespravovaný typ</span><span class="sxs-lookup"><span data-stu-id="412f4-108">[in] The signature for unmanaged type.</span></span>  
  
 `cbNativeType`  
 <span data-ttu-id="412f4-109">pro Počet bajtů v `pvNativeType` .</span><span class="sxs-lookup"><span data-stu-id="412f4-109">[in] The count of bytes in `pvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="412f4-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="412f4-110">Requirements</span></span>  
 <span data-ttu-id="412f4-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="412f4-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="412f4-112">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="412f4-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="412f4-113">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="412f4-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="412f4-114">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="412f4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="412f4-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="412f4-115">See also</span></span>

- [<span data-ttu-id="412f4-116">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="412f4-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="412f4-117">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="412f4-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
