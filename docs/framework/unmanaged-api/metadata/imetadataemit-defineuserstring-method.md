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
ms.openlocfilehash: def77bb64e21b1421983cf263d488ecc1ddb9452
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009314"
---
# <a name="imetadataemitdefineuserstring-method"></a><span data-ttu-id="006f5-102">IMetaDataEmit::DefineUserString – metoda</span><span class="sxs-lookup"><span data-stu-id="006f5-102">IMetaDataEmit::DefineUserString Method</span></span>
<span data-ttu-id="006f5-103">Získá token metadat pro zadaný řetězcový literál.</span><span class="sxs-lookup"><span data-stu-id="006f5-103">Gets a metadata token for the specified literal string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="006f5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="006f5-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineUserString (
    [in]  LPCWSTR     szString,
    [in]  ULONG       cchString,
    [out] mdString    *pstk
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="006f5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="006f5-105">Parameters</span></span>  
 `szString`  
 <span data-ttu-id="006f5-106">pro Řetězec uživatele, který se má uložit.</span><span class="sxs-lookup"><span data-stu-id="006f5-106">[in] The user string to store.</span></span>  
  
 `cchString`  
 <span data-ttu-id="006f5-107">pro Počet velkých znaků v `szString` .</span><span class="sxs-lookup"><span data-stu-id="006f5-107">[in] The count of wide characters in `szString`.</span></span>  
  
 `pstk`  
 <span data-ttu-id="006f5-108">mimo Byl přiřazen řetězcový token.</span><span class="sxs-lookup"><span data-stu-id="006f5-108">[out] The string token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="006f5-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="006f5-109">Requirements</span></span>  
 <span data-ttu-id="006f5-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="006f5-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="006f5-111">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="006f5-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="006f5-112">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="006f5-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="006f5-113">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="006f5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="006f5-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="006f5-114">See also</span></span>

- [<span data-ttu-id="006f5-115">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="006f5-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="006f5-116">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="006f5-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
