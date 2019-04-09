---
title: IMetaDataEmit2::GetDeltaSaveSize – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.GetDeltaSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::GetDeltaSaveSize
helpviewer_keywords:
- IMetaDataEmit2::GetDeltaSaveSize method [.NET Framework metadata]
- GetDeltaSaveSize method [.NET Framework metadata]
ms.assetid: 036db5e7-8211-4645-9a34-03d1a89be955
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 69897a7b646eb9f58e6b38588e302287b4241779
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59139890"
---
# <a name="imetadataemit2getdeltasavesize-method"></a><span data-ttu-id="c8636-102">IMetaDataEmit2::GetDeltaSaveSize – metoda</span><span class="sxs-lookup"><span data-stu-id="c8636-102">IMetaDataEmit2::GetDeltaSaveSize Method</span></span>
<span data-ttu-id="c8636-103">Získá hodnotu, která změnu velikost metadat, která je výsledkem aktuální relace edit-and-continue.</span><span class="sxs-lookup"><span data-stu-id="c8636-103">Gets a value indicating any change in metadata size that results from the current edit-and-continue session.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8636-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c8636-104">Syntax</span></span>  
  
```  
HRESULT GetDeltaSaveSize (  
    [in]  CorSaveSize  fSave,  
    [out] DWORD        *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8636-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c8636-105">Parameters</span></span>  
 `fSave`  
 <span data-ttu-id="c8636-106">[in] Jeden z [corsavesize –](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) hodnoty určující úrovně přesnosti potřeby.</span><span class="sxs-lookup"><span data-stu-id="c8636-106">[in] One of the [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) values, indicating the level of precision desired.</span></span> <span data-ttu-id="c8636-107">Tento parametr je ignorován pro rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="c8636-107">For the .NET Framework version 2.0, this parameter is ignored.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="c8636-108">[out] Změna velikosti metadat.</span><span class="sxs-lookup"><span data-stu-id="c8636-108">[out] The change in the size of the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8636-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c8636-109">Requirements</span></span>  
 <span data-ttu-id="c8636-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8636-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8636-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c8636-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c8636-112">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c8636-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="c8636-113">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="c8636-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c8636-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c8636-114">See also</span></span>

- [<span data-ttu-id="c8636-115">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c8636-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="c8636-116">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c8636-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
