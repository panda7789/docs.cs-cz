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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 153aa7d6b8c35129638de3d47ffa6aff72f550c9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130699"
---
# <a name="imetadatatablesgetcodedtokeninfo-method"></a><span data-ttu-id="11d50-102">IMetaDataTables::GetCodedTokenInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="11d50-102">IMetaDataTables::GetCodedTokenInfo Method</span></span>
<span data-ttu-id="11d50-103">Získá ukazatel na pole tokenů přidružený index zadaný řádek.</span><span class="sxs-lookup"><span data-stu-id="11d50-103">Gets a pointer to an array of tokens associated with the specified row index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11d50-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11d50-104">Syntax</span></span>  
  
```  
HRESULT GetCodedTokenInfo (   
    [in]  ULONG       ixCdTkn,  
    [out] ULONG       *pcTokens,  
    [out] ULONG       **ppTokens,  
    [out] const char  **ppName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11d50-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="11d50-105">Parameters</span></span>  
 `ixCdTkn`  
 <span data-ttu-id="11d50-106">[in] Druh programové token k vrácení.</span><span class="sxs-lookup"><span data-stu-id="11d50-106">[in] The kind of coded token to return.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="11d50-107">[out] Ukazatel na délku `ppTokens`.</span><span class="sxs-lookup"><span data-stu-id="11d50-107">[out] A pointer to the length of `ppTokens`.</span></span>  
  
 `ppTokens`  
 <span data-ttu-id="11d50-108">[out] Ukazatel na ukazatel na pole, která obsahuje seznam vrácených tokenů.</span><span class="sxs-lookup"><span data-stu-id="11d50-108">[out] A pointer to a pointer to an array that contains the list of returned tokens.</span></span>  
  
 `ppName`  
 <span data-ttu-id="11d50-109">[out] Ukazatel na ukazatel na název token na `ixCdTkn`.</span><span class="sxs-lookup"><span data-stu-id="11d50-109">[out] A pointer to a pointer to the name of the token at `ixCdTkn`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11d50-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="11d50-110">Requirements</span></span>  
 <span data-ttu-id="11d50-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11d50-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11d50-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="11d50-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="11d50-113">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="11d50-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="11d50-114">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="11d50-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="11d50-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="11d50-115">See also</span></span>

- [<span data-ttu-id="11d50-116">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="11d50-116">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="11d50-117">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="11d50-117">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
