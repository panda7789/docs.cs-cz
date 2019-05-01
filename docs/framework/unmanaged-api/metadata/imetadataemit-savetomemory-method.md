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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bc840df9dd0793a7347b7f0d8a05296a09d634c8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050061"
---
# <a name="imetadataemitsavetomemory-method"></a><span data-ttu-id="78bd4-102">IMetaDataEmit::SaveToMemory – metoda</span><span class="sxs-lookup"><span data-stu-id="78bd4-102">IMetaDataEmit::SaveToMemory Method</span></span>
<span data-ttu-id="78bd4-103">Uloží všechna metadata v aktuálním oboru k zadané oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="78bd4-103">Saves all metadata in the current scope to the specified area of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78bd4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78bd4-104">Syntax</span></span>  
  
```  
HRESULT SaveToMemory (   
    [out]  void        *pbData,   
    [in]   ULONG       cbData   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78bd4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="78bd4-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="78bd4-106">[out] Adresa, na kterém má být zápis metadat.</span><span class="sxs-lookup"><span data-stu-id="78bd4-106">[out] The address at which to begin writing metadata.</span></span>  
  
 `cbData`  
 <span data-ttu-id="78bd4-107">[in] Velikost v bajtech přidělené paměti.</span><span class="sxs-lookup"><span data-stu-id="78bd4-107">[in] The size, in bytes, of the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78bd4-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="78bd4-108">Requirements</span></span>  
 <span data-ttu-id="78bd4-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78bd4-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78bd4-110">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="78bd4-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="78bd4-111">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="78bd4-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="78bd4-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78bd4-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78bd4-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="78bd4-113">See also</span></span>

- [<span data-ttu-id="78bd4-114">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="78bd4-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="78bd4-115">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="78bd4-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
