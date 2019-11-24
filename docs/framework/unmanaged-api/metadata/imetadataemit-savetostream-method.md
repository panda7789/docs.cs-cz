---
title: IMetaDataEmit::SaveToStream – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SaveToStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SaveToStream
helpviewer_keywords:
- IMetaDataEmit::SaveToStream method [.NET Framework metadata]
- SaveToStream method [.NET Framework metadata]
ms.assetid: e0290a49-3818-4a43-ad46-3014faa34f97
topic_type:
- apiref
ms.openlocfilehash: 23f6186b2561cbcd52db767616d986084f33860b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435925"
---
# <a name="imetadataemitsavetostream-method"></a><span data-ttu-id="ae098-102">IMetaDataEmit::SaveToStream – metoda</span><span class="sxs-lookup"><span data-stu-id="ae098-102">IMetaDataEmit::SaveToStream Method</span></span>
<span data-ttu-id="ae098-103">Saves all metadata in the current scope to the specified `IStream`.</span><span class="sxs-lookup"><span data-stu-id="ae098-103">Saves all metadata in the current scope to the specified `IStream`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae098-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ae098-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveToStream (   
    [in]  IStream     *pIStream,  
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae098-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ae098-105">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="ae098-106">[in] The writable stream to save to.</span><span class="sxs-lookup"><span data-stu-id="ae098-106">[in] The writable stream to save to.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="ae098-107">[in] Reserved.</span><span class="sxs-lookup"><span data-stu-id="ae098-107">[in] Reserved.</span></span> <span data-ttu-id="ae098-108">Must be zero.</span><span class="sxs-lookup"><span data-stu-id="ae098-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae098-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ae098-109">Requirements</span></span>  
 <span data-ttu-id="ae098-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae098-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae098-111">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ae098-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ae098-112">**Library:** Used as a resource in MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ae098-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ae098-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae098-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae098-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ae098-114">See also</span></span>

- [<span data-ttu-id="ae098-115">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ae098-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="ae098-116">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ae098-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
