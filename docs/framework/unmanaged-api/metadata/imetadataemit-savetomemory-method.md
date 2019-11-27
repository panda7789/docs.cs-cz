---
title: IMetaDataEmit::SaveToMemory – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SaveToMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SaveToMemory
helpviewer_keywords:
- IMetaDataEmit::SaveToMemory method [.NET Framework metadata]
- SaveToMemory method [.NET Framework metadata]
ms.assetid: d5237628-2675-45ed-a39e-65c0731b6a56
topic_type:
- apiref
ms.openlocfilehash: be4fb0b4b49408a97b318e0f54f5a753f3f24ef1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435806"
---
# <a name="imetadataemitsavetomemory-method"></a><span data-ttu-id="05642-102">IMetaDataEmit::SaveToMemory – metoda</span><span class="sxs-lookup"><span data-stu-id="05642-102">IMetaDataEmit::SaveToMemory Method</span></span>
<span data-ttu-id="05642-103">Uloží všechna metadata v aktuálním oboru do zadané oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="05642-103">Saves all metadata in the current scope to the specified area of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05642-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05642-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveToMemory (   
    [out]  void        *pbData,   
    [in]   ULONG       cbData   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05642-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="05642-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="05642-106">mimo Adresa, na které začíná zapisovat metadata</span><span class="sxs-lookup"><span data-stu-id="05642-106">[out] The address at which to begin writing metadata.</span></span>  
  
 `cbData`  
 <span data-ttu-id="05642-107">pro Velikost přidělené paměti (v bajtech)</span><span class="sxs-lookup"><span data-stu-id="05642-107">[in] The size, in bytes, of the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05642-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="05642-108">Requirements</span></span>  
 <span data-ttu-id="05642-109">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05642-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05642-110">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="05642-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="05642-111">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="05642-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="05642-112">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05642-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05642-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="05642-113">See also</span></span>

- [<span data-ttu-id="05642-114">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05642-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="05642-115">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05642-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
