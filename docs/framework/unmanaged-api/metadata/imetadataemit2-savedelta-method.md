---
title: IMetaDataEmit2::SaveDelta – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SaveDelta
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDelta
helpviewer_keywords:
- IMetaDataEmit2::SaveDelta method [.NET Framework metadata]
- SaveDelta method [.NET Framework metadata]
ms.assetid: b95739fe-d2fa-4776-ae0d-31d9707ef799
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d97f536d54ac1cb77c5d0413d2437508374ac7f4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59168997"
---
# <a name="imetadataemit2savedelta-method"></a><span data-ttu-id="d6296-102">IMetaDataEmit2::SaveDelta – metoda</span><span class="sxs-lookup"><span data-stu-id="d6296-102">IMetaDataEmit2::SaveDelta Method</span></span>
<span data-ttu-id="d6296-103">Uloží změny z aktuální relace edit-and-continue do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="d6296-103">Saves changes from the current edit-and-continue session to the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6296-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6296-104">Syntax</span></span>  
  
```  
HRESULT SaveDelta (  
    [in] LPCWSTR     szFile,   
    [in] DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6296-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d6296-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="d6296-106">[in] Název souboru v rámci kterého chcete uložit změny.</span><span class="sxs-lookup"><span data-stu-id="d6296-106">[in] The file name under which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="d6296-107">[in] Vyhrazená.</span><span class="sxs-lookup"><span data-stu-id="d6296-107">[in] Reserved.</span></span> <span data-ttu-id="d6296-108">Musí být nula.</span><span class="sxs-lookup"><span data-stu-id="d6296-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6296-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d6296-109">Requirements</span></span>  
 <span data-ttu-id="d6296-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6296-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6296-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d6296-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d6296-112">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d6296-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d6296-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6296-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6296-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d6296-114">See also</span></span>

- [<span data-ttu-id="d6296-115">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d6296-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="d6296-116">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d6296-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
