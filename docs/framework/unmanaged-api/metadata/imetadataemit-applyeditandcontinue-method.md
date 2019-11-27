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
ms.openlocfilehash: b9cad4c9647983e5b39f9b7a5d03736f2848e1c9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432693"
---
# <a name="imetadataemitapplyeditandcontinue-method"></a><span data-ttu-id="fdfec-102">IMetaDataEmit::ApplyEditAndContinue – metoda</span><span class="sxs-lookup"><span data-stu-id="fdfec-102">IMetaDataEmit::ApplyEditAndContinue Method</span></span>
<span data-ttu-id="fdfec-103">Aktualizuje aktuální obor sestavení o změny provedené v zadaných metadatech.</span><span class="sxs-lookup"><span data-stu-id="fdfec-103">Updates the current assembly scope with the changes made in the specified metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdfec-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fdfec-104">Syntax</span></span>  
  
```cpp  
HRESULT ApplyEditAndContinue (   
    [in]  IUnknown    *pImport  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fdfec-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fdfec-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="fdfec-106">\[v\] ukazatel na objekt [IUnknown](/cpp/atl/iunknown) , který představuje rozdílová metadata z přenositelného spustitelného souboru (PE).</span><span class="sxs-lookup"><span data-stu-id="fdfec-106">\[in\] Pointer to an [IUnknown](/cpp/atl/iunknown) object that represents the delta metadata from the portable executable (PE) file.</span></span>
  
 <span data-ttu-id="fdfec-107">Rozdílová metadata jsou blok metadat, který obsahuje změny provedené v kopii skutečných metadat modulu.</span><span class="sxs-lookup"><span data-stu-id="fdfec-107">The delta metadata is the block of metadata that includes the changes that were made to the copy of the module's actual metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fdfec-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fdfec-108">Requirements</span></span>  
 <span data-ttu-id="fdfec-109">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fdfec-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fdfec-110">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="fdfec-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fdfec-111">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="fdfec-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fdfec-112">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fdfec-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdfec-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fdfec-113">See also</span></span>

- [<span data-ttu-id="fdfec-114">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fdfec-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="fdfec-115">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fdfec-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
