---
title: IMetaDataEmit::ApplyEditAndContinue – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.ApplyEditAndContinue
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::ApplyEditAndContinue
helpviewer_keywords:
- ApplyEditAndContinue method [.NET Framework metadata]
- IMetaDataEmit::ApplyEditAndContinue method [.NET Framework metadata]
ms.assetid: 35991289-f389-495d-8caa-a6384fb1d557
topic_type:
- apiref
ms.openlocfilehash: f876187624d066b9e672fbf44a984d6d02a54c43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175873"
---
# <a name="imetadataemitapplyeditandcontinue-method"></a><span data-ttu-id="5dde3-102">IMetaDataEmit::ApplyEditAndContinue – metoda</span><span class="sxs-lookup"><span data-stu-id="5dde3-102">IMetaDataEmit::ApplyEditAndContinue Method</span></span>
<span data-ttu-id="5dde3-103">Aktualizuje aktuální obor sestavení se změnami provedenými v zadaných metadatech.</span><span class="sxs-lookup"><span data-stu-id="5dde3-103">Updates the current assembly scope with the changes made in the specified metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5dde3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5dde3-104">Syntax</span></span>  
  
```cpp  
HRESULT ApplyEditAndContinue (
    [in]  IUnknown    *pImport  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5dde3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5dde3-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="5dde3-106">\[v\] ukazateli na objekt [IUnknown,](/cpp/atl/iunknown) který představuje rozdílová metadata z přenosného spustitelného souboru (PE).</span><span class="sxs-lookup"><span data-stu-id="5dde3-106">\[in\] Pointer to an [IUnknown](/cpp/atl/iunknown) object that represents the delta metadata from the portable executable (PE) file.</span></span>
  
 <span data-ttu-id="5dde3-107">Delta metadata je blok metadat, který zahrnuje změny, které byly provedeny v kopii skutečné metadata modulu.</span><span class="sxs-lookup"><span data-stu-id="5dde3-107">The delta metadata is the block of metadata that includes the changes that were made to the copy of the module's actual metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5dde3-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5dde3-108">Requirements</span></span>  
 <span data-ttu-id="5dde3-109">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5dde3-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5dde3-110">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="5dde3-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5dde3-111">**Knihovna:** Používá se jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5dde3-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5dde3-112">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5dde3-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dde3-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="5dde3-113">See also</span></span>

- [<span data-ttu-id="5dde3-114">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5dde3-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="5dde3-115">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5dde3-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
