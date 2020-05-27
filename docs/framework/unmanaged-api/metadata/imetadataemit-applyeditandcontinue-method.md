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
ms.openlocfilehash: 7ce9ac95c7183a7d47c367914d80f77c57dde0d7
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005762"
---
# <a name="imetadataemitapplyeditandcontinue-method"></a><span data-ttu-id="874f9-102">IMetaDataEmit::ApplyEditAndContinue – metoda</span><span class="sxs-lookup"><span data-stu-id="874f9-102">IMetaDataEmit::ApplyEditAndContinue Method</span></span>
<span data-ttu-id="874f9-103">Aktualizuje aktuální obor sestavení o změny provedené v zadaných metadatech.</span><span class="sxs-lookup"><span data-stu-id="874f9-103">Updates the current assembly scope with the changes made in the specified metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="874f9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="874f9-104">Syntax</span></span>  
  
```cpp  
HRESULT ApplyEditAndContinue (
    [in]  IUnknown    *pImport  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="874f9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="874f9-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="874f9-106">\[v \] ukazatel na objekt [IUnknown](/cpp/atl/iunknown) , který představuje rozdílová metadata z přenositelného spustitelného souboru (PE).</span><span class="sxs-lookup"><span data-stu-id="874f9-106">\[in\] Pointer to an [IUnknown](/cpp/atl/iunknown) object that represents the delta metadata from the portable executable (PE) file.</span></span>
  
 <span data-ttu-id="874f9-107">Rozdílová metadata jsou blok metadat, který obsahuje změny provedené v kopii skutečných metadat modulu.</span><span class="sxs-lookup"><span data-stu-id="874f9-107">The delta metadata is the block of metadata that includes the changes that were made to the copy of the module's actual metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="874f9-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="874f9-108">Requirements</span></span>  
 <span data-ttu-id="874f9-109">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="874f9-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="874f9-110">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="874f9-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="874f9-111">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="874f9-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="874f9-112">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="874f9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="874f9-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="874f9-113">See also</span></span>

- [<span data-ttu-id="874f9-114">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="874f9-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="874f9-115">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="874f9-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
