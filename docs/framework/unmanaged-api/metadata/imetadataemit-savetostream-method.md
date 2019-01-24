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
ms.openlocfilehash: 515e925c9b086823450b73cfbb558d0409b4948a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54575996"
---
# <a name="imetadataemitsavetostream-method"></a><span data-ttu-id="5c8e0-102">IMetaDataEmit::SaveToStream – metoda</span><span class="sxs-lookup"><span data-stu-id="5c8e0-102">IMetaDataEmit::SaveToStream Method</span></span>
<span data-ttu-id="5c8e0-103">Uloží všechna metadata v aktuálním oboru na zadaný `IStream`.</span><span class="sxs-lookup"><span data-stu-id="5c8e0-103">Saves all metadata in the current scope to the specified `IStream`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c8e0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5c8e0-104">Syntax</span></span>  
  
```  
HRESULT SaveToStream (   
    [in]  IStream     *pIStream,  
    [in]  DWORD       dwSaveFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5c8e0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5c8e0-105">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="5c8e0-106">[in] Zapisovatelný datový proud uložte.</span><span class="sxs-lookup"><span data-stu-id="5c8e0-106">[in] The writable stream to save to.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="5c8e0-107">[in] Vyhrazená.</span><span class="sxs-lookup"><span data-stu-id="5c8e0-107">[in] Reserved.</span></span> <span data-ttu-id="5c8e0-108">Musí být nula.</span><span class="sxs-lookup"><span data-stu-id="5c8e0-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c8e0-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5c8e0-109">Requirements</span></span>  
 <span data-ttu-id="5c8e0-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c8e0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c8e0-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5c8e0-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5c8e0-112">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5c8e0-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5c8e0-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c8e0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c8e0-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5c8e0-114">See also</span></span>
- [<span data-ttu-id="5c8e0-115">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5c8e0-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="5c8e0-116">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5c8e0-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
