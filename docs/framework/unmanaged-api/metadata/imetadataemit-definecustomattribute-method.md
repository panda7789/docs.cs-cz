---
title: IMetaDataEmit::DefineCustomAttribute – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineCustomAttribute
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineCustomAttribute
helpviewer_keywords:
- DefineCustomAttribute method [.NET Framework metadata]
- IMetaDataEmit::DefineCustomAttribute method [.NET Framework metadata]
ms.assetid: 7dd14854-b756-4401-b167-88ca576dc8f0
topic_type:
- apiref
ms.openlocfilehash: e6a732b98ae02ba2b273b45921b7de61ab4fd29f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432636"
---
# <a name="imetadataemitdefinecustomattribute-method"></a><span data-ttu-id="cb391-102">IMetaDataEmit::DefineCustomAttribute – metoda</span><span class="sxs-lookup"><span data-stu-id="cb391-102">IMetaDataEmit::DefineCustomAttribute Method</span></span>
<span data-ttu-id="cb391-103">Vytvoří definici pro vlastní atribut se zadaným podpisem metadat, který se má připojit k zadanému objektu, a získá token do této definice vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="cb391-103">Creates a definition for a custom attribute with the specified metadata signature, to be attached to the specified object, and gets a token to that custom attribute definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb391-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cb391-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineCustomAttribute (   
    [in]  mdToken     tkObj,   
    [in]  mdToken     tkType,   
    [in]  void const  *pCustomAttribute,   
    [in]  ULONG       cbCustomAttribute,   
    [out] mdCustomAttribute *pcv   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb391-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cb391-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="cb391-106">pro Token pro položku vlastníka</span><span class="sxs-lookup"><span data-stu-id="cb391-106">[in] The token for the owner item.</span></span>  
  
 `tkType`  
 <span data-ttu-id="cb391-107">pro Token, který identifikuje vlastní atribut.</span><span class="sxs-lookup"><span data-stu-id="cb391-107">[in] The token that identifies the custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="cb391-108">pro Ukazatel na vlastní atribut.</span><span class="sxs-lookup"><span data-stu-id="cb391-108">[in] A pointer to the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="cb391-109">pro Počet bajtů v `pCustomAttribute`.</span><span class="sxs-lookup"><span data-stu-id="cb391-109">[in] The count of bytes in `pCustomAttribute`.</span></span>  
  
 `pcv`  
 <span data-ttu-id="cb391-110">mimo Byl přiřazen token `mdCustomAttribute`.</span><span class="sxs-lookup"><span data-stu-id="cb391-110">[out] The `mdCustomAttribute` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb391-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cb391-111">Requirements</span></span>  
 <span data-ttu-id="cb391-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb391-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb391-113">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="cb391-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cb391-114">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="cb391-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cb391-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb391-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb391-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cb391-116">See also</span></span>

- [<span data-ttu-id="cb391-117">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cb391-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="cb391-118">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cb391-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
