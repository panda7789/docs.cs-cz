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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 90ddc540115a60154953ac6e8cb931103a650752
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492410"
---
# <a name="imetadataemitsave-method"></a><span data-ttu-id="7c022-102">IMetaDataEmit::Save – metoda</span><span class="sxs-lookup"><span data-stu-id="7c022-102">IMetaDataEmit::Save Method</span></span>
<span data-ttu-id="7c022-103">Uloží všechna metadata v aktuálním oboru k souboru na zadané adrese.</span><span class="sxs-lookup"><span data-stu-id="7c022-103">Saves all metadata in the current scope to the file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c022-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7c022-104">Syntax</span></span>  
  
```  
HRESULT Save (   
    [in]  LPCWSTR     szFile,   
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c022-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7c022-105">Parameters</span></span>  
 `wzFile`  
 <span data-ttu-id="7c022-106">[in] Název souboru uložte.</span><span class="sxs-lookup"><span data-stu-id="7c022-106">[in] The name of the file to save to.</span></span> <span data-ttu-id="7c022-107">Pokud je tato hodnota null, kopie v paměti se uloží na poslední umístění, která byla použita.</span><span class="sxs-lookup"><span data-stu-id="7c022-107">If this value is null, the in-memory copy will be saved to the last location that was used.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="7c022-108">[in] Vyhrazená.</span><span class="sxs-lookup"><span data-stu-id="7c022-108">[in] Reserved.</span></span> <span data-ttu-id="7c022-109">Musí být nula.</span><span class="sxs-lookup"><span data-stu-id="7c022-109">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c022-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7c022-110">Requirements</span></span>  
 <span data-ttu-id="7c022-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c022-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c022-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7c022-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7c022-113">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7c022-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7c022-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c022-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c022-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7c022-115">See also</span></span>
- [<span data-ttu-id="7c022-116">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7c022-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="7c022-117">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7c022-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
