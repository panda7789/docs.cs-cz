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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 52190583338f1c1ee9183a98d5f4a6cd7236342d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59075663"
---
# <a name="imetadataemitdefinecustomattribute-method"></a><span data-ttu-id="f09f0-102">IMetaDataEmit::DefineCustomAttribute – metoda</span><span class="sxs-lookup"><span data-stu-id="f09f0-102">IMetaDataEmit::DefineCustomAttribute Method</span></span>
<span data-ttu-id="f09f0-103">Vytvoří definici vlastního atributu podpisem Zadaná metadata, připojí se k zadaný objekt a získá token pro tuto definici vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="f09f0-103">Creates a definition for a custom attribute with the specified metadata signature, to be attached to the specified object, and gets a token to that custom attribute definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f09f0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f09f0-104">Syntax</span></span>  
  
```  
HRESULT DefineCustomAttribute (   
    [in]  mdToken     tkObj,   
    [in]  mdToken     tkType,   
    [in]  void const  *pCustomAttribute,   
    [in]  ULONG       cbCustomAttribute,   
    [out] mdCustomAttribute *pcv   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f09f0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f09f0-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="f09f0-106">[in] Token pro položku vlastníka.</span><span class="sxs-lookup"><span data-stu-id="f09f0-106">[in] The token for the owner item.</span></span>  
  
 `tkType`  
 <span data-ttu-id="f09f0-107">[in] Token, který identifikuje vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="f09f0-107">[in] The token that identifies the custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="f09f0-108">[in] Ukazatel na vlastní atribut.</span><span class="sxs-lookup"><span data-stu-id="f09f0-108">[in] A pointer to the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="f09f0-109">[in] Počet bajtů v `pCustomAttribute`.</span><span class="sxs-lookup"><span data-stu-id="f09f0-109">[in] The count of bytes in `pCustomAttribute`.</span></span>  
  
 `pcv`  
 <span data-ttu-id="f09f0-110">[out] `mdCustomAttribute` Token přiřazený.</span><span class="sxs-lookup"><span data-stu-id="f09f0-110">[out] The `mdCustomAttribute` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f09f0-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f09f0-111">Requirements</span></span>  
 <span data-ttu-id="f09f0-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f09f0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f09f0-113">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f09f0-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f09f0-114">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f09f0-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="f09f0-115">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="f09f0-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f09f0-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f09f0-116">See also</span></span>

- [<span data-ttu-id="f09f0-117">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f09f0-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="f09f0-118">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f09f0-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
