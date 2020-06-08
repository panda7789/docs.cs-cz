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
ms.openlocfilehash: 8a6f11996425c92d9b0e3123ee2d3a064739454b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492750"
---
# <a name="imetadataemit2savedeltatomemory-method"></a><span data-ttu-id="db182-102">IMetaDataEmit2::SaveDeltaToMemory – metoda</span><span class="sxs-lookup"><span data-stu-id="db182-102">IMetaDataEmit2::SaveDeltaToMemory Method</span></span>
<span data-ttu-id="db182-103">Uloží změny z aktuální relace úprav a pokračování do paměti.</span><span class="sxs-lookup"><span data-stu-id="db182-103">Saves changes from the current edit-and-continue session to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db182-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db182-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveDeltaToMemory (  
    [out] void        *pbData,
    [in]  ULONG       cbData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db182-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="db182-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="db182-106">mimo Adresa, na které se má začít zapisovat rozdíl metadat</span><span class="sxs-lookup"><span data-stu-id="db182-106">[out] The address at which to begin writing the metadata delta.</span></span>  
  
 `cbData`  
 <span data-ttu-id="db182-107">pro Velikost změn</span><span class="sxs-lookup"><span data-stu-id="db182-107">[in] The size of the changes.</span></span> <span data-ttu-id="db182-108">K určení velikosti použijte [IMetaDataEmit2:: GetDeltaSaveSize –](imetadataemit2-getdeltasavesize-method.md) .</span><span class="sxs-lookup"><span data-stu-id="db182-108">Use [IMetaDataEmit2::GetDeltaSaveSize](imetadataemit2-getdeltasavesize-method.md) to determine the size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db182-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="db182-109">Requirements</span></span>  
 <span data-ttu-id="db182-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db182-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db182-111">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="db182-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="db182-112">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="db182-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="db182-113">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db182-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db182-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="db182-114">See also</span></span>

- [<span data-ttu-id="db182-115">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="db182-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="db182-116">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="db182-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
