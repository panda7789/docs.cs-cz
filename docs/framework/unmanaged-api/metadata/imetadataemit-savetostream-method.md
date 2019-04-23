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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8f6b5582b96dfc83eed482def2c4c4abfeb33a4c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59207783"
---
# <a name="imetadataemitsavetostream-method"></a><span data-ttu-id="89226-102">IMetaDataEmit::SaveToStream – metoda</span><span class="sxs-lookup"><span data-stu-id="89226-102">IMetaDataEmit::SaveToStream Method</span></span>
<span data-ttu-id="89226-103">Uloží všechna metadata v aktuálním oboru na zadaný `IStream`.</span><span class="sxs-lookup"><span data-stu-id="89226-103">Saves all metadata in the current scope to the specified `IStream`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89226-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89226-104">Syntax</span></span>  
  
```  
HRESULT SaveToStream (   
    [in]  IStream     *pIStream,  
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89226-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="89226-105">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="89226-106">[in] Zapisovatelný datový proud uložte.</span><span class="sxs-lookup"><span data-stu-id="89226-106">[in] The writable stream to save to.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="89226-107">[in] Vyhrazená.</span><span class="sxs-lookup"><span data-stu-id="89226-107">[in] Reserved.</span></span> <span data-ttu-id="89226-108">Musí být nula.</span><span class="sxs-lookup"><span data-stu-id="89226-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89226-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="89226-109">Requirements</span></span>  
 <span data-ttu-id="89226-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89226-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89226-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="89226-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="89226-112">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="89226-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="89226-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89226-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89226-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="89226-114">See also</span></span>

- [<span data-ttu-id="89226-115">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="89226-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="89226-116">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="89226-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
