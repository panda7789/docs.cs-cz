---
title: IMetaDataEmit::DefineUserString – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineUserString
helpviewer_keywords:
- DefineUserString method [.NET Framework metadata]
- IMetaDataEmit::DefineUserString method [.NET Framework metadata]
ms.assetid: 88fb7ef3-bbdf-429c-b678-c9c153456461
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 25e35fd9afd2ce4dc60e23ccd64e0630a008bf39
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777431"
---
# <a name="imetadataemitdefineuserstring-method"></a><span data-ttu-id="b2e0f-102">IMetaDataEmit::DefineUserString – metoda</span><span class="sxs-lookup"><span data-stu-id="b2e0f-102">IMetaDataEmit::DefineUserString Method</span></span>
<span data-ttu-id="b2e0f-103">Získá token metadat zadaného řetězcového literálu.</span><span class="sxs-lookup"><span data-stu-id="b2e0f-103">Gets a metadata token for the specified literal string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2e0f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b2e0f-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineUserString (   
    [in]  LPCWSTR     szString,   
    [in]  ULONG       cchString,   
    [out] mdString    *pstk   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2e0f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b2e0f-105">Parameters</span></span>  
 `szString`  
 <span data-ttu-id="b2e0f-106">[in] Řetězec uživatelského k uložení.</span><span class="sxs-lookup"><span data-stu-id="b2e0f-106">[in] The user string to store.</span></span>  
  
 `cchString`  
 <span data-ttu-id="b2e0f-107">[in] Počet širokých znaků v `szString`.</span><span class="sxs-lookup"><span data-stu-id="b2e0f-107">[in] The count of wide characters in `szString`.</span></span>  
  
 `pstk`  
 <span data-ttu-id="b2e0f-108">[out] Řetězec s tokenem přiřazené.</span><span class="sxs-lookup"><span data-stu-id="b2e0f-108">[out] The string token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2e0f-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b2e0f-109">Requirements</span></span>  
 <span data-ttu-id="b2e0f-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2e0f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2e0f-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b2e0f-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b2e0f-112">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b2e0f-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b2e0f-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2e0f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2e0f-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b2e0f-114">See also</span></span>

- [<span data-ttu-id="b2e0f-115">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b2e0f-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="b2e0f-116">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b2e0f-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
