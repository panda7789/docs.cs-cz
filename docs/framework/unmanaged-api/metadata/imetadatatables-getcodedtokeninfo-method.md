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
ms.openlocfilehash: 11ab93e9cb4449ab77e5e9c4da81073aaf432382
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54669689"
---
# <a name="imetadatatablesgetcodedtokeninfo-method"></a><span data-ttu-id="dea34-102">IMetaDataTables::GetCodedTokenInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="dea34-102">IMetaDataTables::GetCodedTokenInfo Method</span></span>
<span data-ttu-id="dea34-103">Získá ukazatel na pole tokenů přidružený index zadaný řádek.</span><span class="sxs-lookup"><span data-stu-id="dea34-103">Gets a pointer to an array of tokens associated with the specified row index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dea34-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dea34-104">Syntax</span></span>  
  
```  
HRESULT GetCodedTokenInfo (   
    [in]  ULONG       ixCdTkn,  
    [out] ULONG       *pcTokens,  
    [out] ULONG       **ppTokens,  
    [out] const char  **ppName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dea34-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dea34-105">Parameters</span></span>  
 `ixCdTkn`  
 <span data-ttu-id="dea34-106">[in] Druh programové token k vrácení.</span><span class="sxs-lookup"><span data-stu-id="dea34-106">[in] The kind of coded token to return.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="dea34-107">[out] Ukazatel na délku `ppTokens`.</span><span class="sxs-lookup"><span data-stu-id="dea34-107">[out] A pointer to the length of `ppTokens`.</span></span>  
  
 `ppTokens`  
 <span data-ttu-id="dea34-108">[out] Ukazatel na ukazatel na pole, která obsahuje seznam vrácených tokenů.</span><span class="sxs-lookup"><span data-stu-id="dea34-108">[out] A pointer to a pointer to an array that contains the list of returned tokens.</span></span>  
  
 `ppName`  
 <span data-ttu-id="dea34-109">[out] Ukazatel na ukazatel na název token na `ixCdTkn`.</span><span class="sxs-lookup"><span data-stu-id="dea34-109">[out] A pointer to a pointer to the name of the token at `ixCdTkn`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dea34-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dea34-110">Requirements</span></span>  
 <span data-ttu-id="dea34-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dea34-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dea34-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="dea34-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dea34-113">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dea34-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dea34-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dea34-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dea34-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dea34-115">See also</span></span>
- [<span data-ttu-id="dea34-116">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dea34-116">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="dea34-117">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dea34-117">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
