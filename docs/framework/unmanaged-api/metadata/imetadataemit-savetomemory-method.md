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
ms.openlocfilehash: d8843b2b5f69696dc206e9b530e3062ff225e89e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177584"
---
# <a name="imetadataemitsavetomemory-method"></a><span data-ttu-id="abadd-102">IMetaDataEmit::SaveToMemory – metoda</span><span class="sxs-lookup"><span data-stu-id="abadd-102">IMetaDataEmit::SaveToMemory Method</span></span>
<span data-ttu-id="abadd-103">Uloží všechna metadata v aktuálním oboru do zadané oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="abadd-103">Saves all metadata in the current scope to the specified area of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abadd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="abadd-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveToMemory (
    [out]  void        *pbData,
    [in]   ULONG       cbData
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="abadd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="abadd-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="abadd-106">[out] Adresa, na které chcete začít zápis metadat.</span><span class="sxs-lookup"><span data-stu-id="abadd-106">[out] The address at which to begin writing metadata.</span></span>  
  
 `cbData`  
 <span data-ttu-id="abadd-107">[v] Velikost přidělené paměti v bajtech.</span><span class="sxs-lookup"><span data-stu-id="abadd-107">[in] The size, in bytes, of the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abadd-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="abadd-108">Requirements</span></span>  
 <span data-ttu-id="abadd-109">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abadd-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abadd-110">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="abadd-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="abadd-111">**Knihovna:** Používá se jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="abadd-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="abadd-112">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abadd-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abadd-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="abadd-113">See also</span></span>

- [<span data-ttu-id="abadd-114">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="abadd-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="abadd-115">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="abadd-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
