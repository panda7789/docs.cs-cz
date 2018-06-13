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
ms.openlocfilehash: a7a36d14b67efb3934089dc16de41a3b80ea0c0e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447987"
---
# <a name="imetadatatablesgetcodedtokeninfo-method"></a><span data-ttu-id="e1e10-102">IMetaDataTables::GetCodedTokenInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="e1e10-102">IMetaDataTables::GetCodedTokenInfo Method</span></span>
<span data-ttu-id="e1e10-103">Získá ukazatel na pole tokeny přidružený index zadaný řádku.</span><span class="sxs-lookup"><span data-stu-id="e1e10-103">Gets a pointer to an array of tokens associated with the specified row index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1e10-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e1e10-104">Syntax</span></span>  
  
```  
HRESULT GetCodedTokenInfo (   
    [in]  ULONG       ixCdTkn,  
    [out] ULONG       *pcTokens,  
    [out] ULONG       **ppTokens,  
    [out] const char  **ppName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e1e10-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e1e10-105">Parameters</span></span>  
 `ixCdTkn`  
 <span data-ttu-id="e1e10-106">[v] Druh programové token, který má vrátit.</span><span class="sxs-lookup"><span data-stu-id="e1e10-106">[in] The kind of coded token to return.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="e1e10-107">[out] Ukazatel na délce `ppTokens`.</span><span class="sxs-lookup"><span data-stu-id="e1e10-107">[out] A pointer to the length of `ppTokens`.</span></span>  
  
 `ppTokens`  
 <span data-ttu-id="e1e10-108">[out] Ukazatel na ukazatel na pole, které obsahuje seznam vrátil tokeny.</span><span class="sxs-lookup"><span data-stu-id="e1e10-108">[out] A pointer to a pointer to an array that contains the list of returned tokens.</span></span>  
  
 `ppName`  
 <span data-ttu-id="e1e10-109">[out] Ukazatel na ukazatel na název tokenu v `ixCdTkn`.</span><span class="sxs-lookup"><span data-stu-id="e1e10-109">[out] A pointer to a pointer to the name of the token at `ixCdTkn`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1e10-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e1e10-110">Requirements</span></span>  
 <span data-ttu-id="e1e10-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1e10-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1e10-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e1e10-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e1e10-113">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e1e10-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e1e10-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1e10-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1e10-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="e1e10-115">See Also</span></span>  
 [<span data-ttu-id="e1e10-116">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e1e10-116">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="e1e10-117">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e1e10-117">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
