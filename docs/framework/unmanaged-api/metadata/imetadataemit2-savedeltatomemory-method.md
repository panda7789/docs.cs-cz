---
title: IMetaDataEmit2::SaveDeltaToMemory – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SaveDeltaToMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDeltaToMemory
helpviewer_keywords:
- SaveDeltaToMemory method [.NET Framework metadata]
- IMetaDataEmit2::SaveDeltaToMemory method [.NET Framework metadata]
ms.assetid: e2146726-0084-4c9e-a2d2-e8d461b13b21
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fa95a737747e9153eb844cddd8e0684585b9108b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049970"
---
# <a name="imetadataemit2savedeltatomemory-method"></a><span data-ttu-id="05ac9-102">IMetaDataEmit2::SaveDeltaToMemory – metoda</span><span class="sxs-lookup"><span data-stu-id="05ac9-102">IMetaDataEmit2::SaveDeltaToMemory Method</span></span>
<span data-ttu-id="05ac9-103">Uloží změny z aktuální relace edit-and-continue do paměti.</span><span class="sxs-lookup"><span data-stu-id="05ac9-103">Saves changes from the current edit-and-continue session to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05ac9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05ac9-104">Syntax</span></span>  
  
```  
HRESULT SaveDeltaToMemory (  
    [out] void        *pbData,   
    [in]  ULONG       cbData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05ac9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="05ac9-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="05ac9-106">[out] Adresa ve kterém se má začít psát metadata delta.</span><span class="sxs-lookup"><span data-stu-id="05ac9-106">[out] The address at which to begin writing the metadata delta.</span></span>  
  
 `cbData`  
 <span data-ttu-id="05ac9-107">[in] Velikost změny.</span><span class="sxs-lookup"><span data-stu-id="05ac9-107">[in] The size of the changes.</span></span> <span data-ttu-id="05ac9-108">Použití [imetadataemit2::getdeltasavesize –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md) k určení velikosti.</span><span class="sxs-lookup"><span data-stu-id="05ac9-108">Use [IMetaDataEmit2::GetDeltaSaveSize](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md) to determine the size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05ac9-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="05ac9-109">Requirements</span></span>  
 <span data-ttu-id="05ac9-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05ac9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05ac9-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="05ac9-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="05ac9-112">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="05ac9-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="05ac9-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05ac9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05ac9-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="05ac9-114">See also</span></span>

- [<span data-ttu-id="05ac9-115">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05ac9-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="05ac9-116">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="05ac9-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
