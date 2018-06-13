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
ms.openlocfilehash: ad6e565db634477e4f0382afdec12361ce7111a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446506"
---
# <a name="imetadataemit2getdeltasavesize-method"></a><span data-ttu-id="bd0e4-102">IMetaDataEmit2::GetDeltaSaveSize – metoda</span><span class="sxs-lookup"><span data-stu-id="bd0e4-102">IMetaDataEmit2::GetDeltaSaveSize Method</span></span>
<span data-ttu-id="bd0e4-103">Získá hodnotu označující, všechny změny v velikost metadat, která je výsledkem aktuální relace upravit a pokračovat.</span><span class="sxs-lookup"><span data-stu-id="bd0e4-103">Gets a value indicating any change in metadata size that results from the current edit-and-continue session.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd0e4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bd0e4-104">Syntax</span></span>  
  
```  
HRESULT GetDeltaSaveSize (  
    [in]  CorSaveSize  fSave,  
    [out] DWORD        *pdwSaveSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bd0e4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bd0e4-105">Parameters</span></span>  
 `fSave`  
 <span data-ttu-id="bd0e4-106">[v] Jeden z [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) hodnoty, označující úroveň přesnost potřeby.</span><span class="sxs-lookup"><span data-stu-id="bd0e4-106">[in] One of the [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) values, indicating the level of precision desired.</span></span> <span data-ttu-id="bd0e4-107">Pro rozhraní .NET Framework verze 2.0 je tento parametr ignorován.</span><span class="sxs-lookup"><span data-stu-id="bd0e4-107">For the .NET Framework version 2.0, this parameter is ignored.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="bd0e4-108">[out] Změna velikosti metadat.</span><span class="sxs-lookup"><span data-stu-id="bd0e4-108">[out] The change in the size of the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd0e4-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bd0e4-109">Requirements</span></span>  
 <span data-ttu-id="bd0e4-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd0e4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd0e4-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bd0e4-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bd0e4-112">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bd0e4-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bd0e4-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd0e4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd0e4-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="bd0e4-114">See Also</span></span>  
 [<span data-ttu-id="bd0e4-115">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bd0e4-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="bd0e4-116">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bd0e4-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
