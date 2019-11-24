---
title: IMetaDataEmit::Save – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.Save
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::Save
helpviewer_keywords:
- Save method, IMetaDataEmit interface [.NET Framework metadata]
- IMetaDataEmit::Save method [.NET Framework metadata]
ms.assetid: c1de8400-adfe-4a71-b828-a1d0cc1ea505
topic_type:
- apiref
ms.openlocfilehash: afd60cdf566bea459816ee890d44cc09258de516
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435943"
---
# <a name="imetadataemitsave-method"></a><span data-ttu-id="f1963-102">IMetaDataEmit::Save – metoda</span><span class="sxs-lookup"><span data-stu-id="f1963-102">IMetaDataEmit::Save Method</span></span>
<span data-ttu-id="f1963-103">Saves all metadata in the current scope to the file at the specified address.</span><span class="sxs-lookup"><span data-stu-id="f1963-103">Saves all metadata in the current scope to the file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1963-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f1963-104">Syntax</span></span>  
  
```cpp  
HRESULT Save (   
    [in]  LPCWSTR     szFile,   
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1963-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f1963-105">Parameters</span></span>  
 `wzFile`  
 <span data-ttu-id="f1963-106">[in] The name of the file to save to.</span><span class="sxs-lookup"><span data-stu-id="f1963-106">[in] The name of the file to save to.</span></span> <span data-ttu-id="f1963-107">If this value is null, the in-memory copy will be saved to the last location that was used.</span><span class="sxs-lookup"><span data-stu-id="f1963-107">If this value is null, the in-memory copy will be saved to the last location that was used.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="f1963-108">[in] Reserved.</span><span class="sxs-lookup"><span data-stu-id="f1963-108">[in] Reserved.</span></span> <span data-ttu-id="f1963-109">Must be zero.</span><span class="sxs-lookup"><span data-stu-id="f1963-109">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1963-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f1963-110">Requirements</span></span>  
 <span data-ttu-id="f1963-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1963-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1963-112">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f1963-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f1963-113">**Library:** Used as a resource in MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f1963-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f1963-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1963-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1963-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f1963-115">See also</span></span>

- [<span data-ttu-id="f1963-116">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f1963-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="f1963-117">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f1963-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
