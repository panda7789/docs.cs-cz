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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168997"
---
# <a name="imetadataemit2savedelta-method"></a><span data-ttu-id="e5af0-102">IMetaDataEmit2::SaveDelta – metoda</span><span class="sxs-lookup"><span data-stu-id="e5af0-102">IMetaDataEmit2::SaveDelta Method</span></span>
<span data-ttu-id="e5af0-103">Uloží změny z aktuální relace edit-and-continue do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="e5af0-103">Saves changes from the current edit-and-continue session to the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5af0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5af0-104">Syntax</span></span>  
  
```  
HRESULT SaveDelta (  
    [in] LPCWSTR     szFile,   
    [in] DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5af0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e5af0-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="e5af0-106">[in] Název souboru v rámci kterého chcete uložit změny.</span><span class="sxs-lookup"><span data-stu-id="e5af0-106">[in] The file name under which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="e5af0-107">[in] Vyhrazená.</span><span class="sxs-lookup"><span data-stu-id="e5af0-107">[in] Reserved.</span></span> <span data-ttu-id="e5af0-108">Musí být nula.</span><span class="sxs-lookup"><span data-stu-id="e5af0-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5af0-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e5af0-109">Requirements</span></span>  
 <span data-ttu-id="e5af0-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5af0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5af0-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e5af0-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e5af0-112">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e5af0-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="e5af0-113">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="e5af0-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e5af0-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e5af0-114">See also</span></span>

- [<span data-ttu-id="e5af0-115">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e5af0-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="e5af0-116">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e5af0-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
