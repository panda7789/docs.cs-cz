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
ms.openlocfilehash: ccf82531eb1f78bcfc6762d10d53ffee59f30ad8
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84003937"
---
# <a name="imetadataemitsavetomemory-method"></a><span data-ttu-id="7b87f-102">IMetaDataEmit::SaveToMemory – metoda</span><span class="sxs-lookup"><span data-stu-id="7b87f-102">IMetaDataEmit::SaveToMemory Method</span></span>
<span data-ttu-id="7b87f-103">Uloží všechna metadata v aktuálním oboru do zadané oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="7b87f-103">Saves all metadata in the current scope to the specified area of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b87f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b87f-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveToMemory (
    [out]  void        *pbData,
    [in]   ULONG       cbData
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b87f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7b87f-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="7b87f-106">mimo Adresa, na které začíná zapisovat metadata</span><span class="sxs-lookup"><span data-stu-id="7b87f-106">[out] The address at which to begin writing metadata.</span></span>  
  
 `cbData`  
 <span data-ttu-id="7b87f-107">pro Velikost přidělené paměti (v bajtech)</span><span class="sxs-lookup"><span data-stu-id="7b87f-107">[in] The size, in bytes, of the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b87f-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7b87f-108">Requirements</span></span>  
 <span data-ttu-id="7b87f-109">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b87f-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b87f-110">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="7b87f-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7b87f-111">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="7b87f-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7b87f-112">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b87f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b87f-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="7b87f-113">See also</span></span>

- [<span data-ttu-id="7b87f-114">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7b87f-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="7b87f-115">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7b87f-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
