---
title: IMetaDataTables::GetCodedTokenInfo – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetCodedTokenInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetCodedTokenInfo
helpviewer_keywords:
- GetCodedTokenInfo method [.NET Framework metadata]
- IMetaDataTables::GetCodedTokenInfo method [.NET Framework metadata]
ms.assetid: 31214d3a-715e-49af-92b3-0fd11e4f218a
topic_type:
- apiref
ms.openlocfilehash: 64c70fe0b657047ae35dccb763fa57120403deef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177156"
---
# <a name="imetadatatablesgetcodedtokeninfo-method"></a><span data-ttu-id="effa3-102">IMetaDataTables::GetCodedTokenInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="effa3-102">IMetaDataTables::GetCodedTokenInfo Method</span></span>
<span data-ttu-id="effa3-103">Získá ukazatel na pole tokenů přidružených k indexu zadaného řádku.</span><span class="sxs-lookup"><span data-stu-id="effa3-103">Gets a pointer to an array of tokens associated with the specified row index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="effa3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="effa3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodedTokenInfo (
    [in]  ULONG       ixCdTkn,  
    [out] ULONG       *pcTokens,  
    [out] ULONG       **ppTokens,  
    [out] const char  **ppName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="effa3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="effa3-105">Parameters</span></span>  
 `ixCdTkn`  
 <span data-ttu-id="effa3-106">[v] Druh kódovaného tokenu, který chcete vrátit.</span><span class="sxs-lookup"><span data-stu-id="effa3-106">[in] The kind of coded token to return.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="effa3-107">[out] Ukazatel na délku `ppTokens`.</span><span class="sxs-lookup"><span data-stu-id="effa3-107">[out] A pointer to the length of `ppTokens`.</span></span>  
  
 `ppTokens`  
 <span data-ttu-id="effa3-108">[out] Ukazatel na ukazatel na pole, které obsahuje seznam vrácených tokenů.</span><span class="sxs-lookup"><span data-stu-id="effa3-108">[out] A pointer to a pointer to an array that contains the list of returned tokens.</span></span>  
  
 `ppName`  
 <span data-ttu-id="effa3-109">[out] Ukazatel na ukazatel na název tokenu `ixCdTkn`na .</span><span class="sxs-lookup"><span data-stu-id="effa3-109">[out] A pointer to a pointer to the name of the token at `ixCdTkn`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="effa3-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="effa3-110">Requirements</span></span>  
 <span data-ttu-id="effa3-111">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="effa3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="effa3-112">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="effa3-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="effa3-113">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="effa3-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="effa3-114">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="effa3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="effa3-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="effa3-115">See also</span></span>

- [<span data-ttu-id="effa3-116">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="effa3-116">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="effa3-117">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="effa3-117">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
