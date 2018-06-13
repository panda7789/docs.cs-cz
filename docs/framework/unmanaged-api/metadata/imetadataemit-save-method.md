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
ms.openlocfilehash: a6d97d3e4a93985f9b2de3ed9785eff5f7f46c36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444676"
---
# <a name="imetadataemitsave-method"></a><span data-ttu-id="04f5e-102">IMetaDataEmit::Save – metoda</span><span class="sxs-lookup"><span data-stu-id="04f5e-102">IMetaDataEmit::Save Method</span></span>
<span data-ttu-id="04f5e-103">Uloží všechna metadata v aktuálním oboru do souboru na zadané adrese.</span><span class="sxs-lookup"><span data-stu-id="04f5e-103">Saves all metadata in the current scope to the file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04f5e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04f5e-104">Syntax</span></span>  
  
```  
HRESULT Save (   
    [in]  LPCWSTR     szFile,   
    [in]  DWORD       dwSaveFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="04f5e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="04f5e-105">Parameters</span></span>  
 `wzFile`  
 <span data-ttu-id="04f5e-106">[v] Název souboru uložte.</span><span class="sxs-lookup"><span data-stu-id="04f5e-106">[in] The name of the file to save to.</span></span> <span data-ttu-id="04f5e-107">Pokud je tato hodnota null, kopie v paměti se uloží na poslední umístění, která byla použita.</span><span class="sxs-lookup"><span data-stu-id="04f5e-107">If this value is null, the in-memory copy will be saved to the last location that was used.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="04f5e-108">[v] Vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="04f5e-108">[in] Reserved.</span></span> <span data-ttu-id="04f5e-109">Musí být nula.</span><span class="sxs-lookup"><span data-stu-id="04f5e-109">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04f5e-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="04f5e-110">Requirements</span></span>  
 <span data-ttu-id="04f5e-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04f5e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04f5e-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="04f5e-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="04f5e-113">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="04f5e-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="04f5e-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04f5e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04f5e-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="04f5e-115">See Also</span></span>  
 [<span data-ttu-id="04f5e-116">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="04f5e-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="04f5e-117">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="04f5e-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
