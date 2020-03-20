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
ms.openlocfilehash: a71d8694ec8c5bd35ecd3e98ed32e05bc7b382fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177621"
---
# <a name="imetadataemitdefineuserstring-method"></a><span data-ttu-id="06f5e-102">IMetaDataEmit::DefineUserString – metoda</span><span class="sxs-lookup"><span data-stu-id="06f5e-102">IMetaDataEmit::DefineUserString Method</span></span>
<span data-ttu-id="06f5e-103">Získá token metadat pro zadaný řetězec literálu.</span><span class="sxs-lookup"><span data-stu-id="06f5e-103">Gets a metadata token for the specified literal string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06f5e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="06f5e-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineUserString (
    [in]  LPCWSTR     szString,
    [in]  ULONG       cchString,
    [out] mdString    *pstk
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06f5e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="06f5e-105">Parameters</span></span>  
 `szString`  
 <span data-ttu-id="06f5e-106">[v] Uživatelský řetězec k uložení.</span><span class="sxs-lookup"><span data-stu-id="06f5e-106">[in] The user string to store.</span></span>  
  
 `cchString`  
 <span data-ttu-id="06f5e-107">[v] Počet širokých znaků `szString`v .</span><span class="sxs-lookup"><span data-stu-id="06f5e-107">[in] The count of wide characters in `szString`.</span></span>  
  
 `pstk`  
 <span data-ttu-id="06f5e-108">[out] Přiřazený token řetězce.</span><span class="sxs-lookup"><span data-stu-id="06f5e-108">[out] The string token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06f5e-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="06f5e-109">Requirements</span></span>  
 <span data-ttu-id="06f5e-110">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06f5e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06f5e-111">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="06f5e-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="06f5e-112">**Knihovna:** Používá se jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="06f5e-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="06f5e-113">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06f5e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06f5e-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="06f5e-114">See also</span></span>

- [<span data-ttu-id="06f5e-115">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="06f5e-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="06f5e-116">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="06f5e-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
