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
ms.openlocfilehash: 5ec4fe2a8e949cf6e9aa0ce68f4d4e49b72170b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177440"
---
# <a name="imetadataemit2savedeltatomemory-method"></a><span data-ttu-id="410a5-102">IMetaDataEmit2::SaveDeltaToMemory – metoda</span><span class="sxs-lookup"><span data-stu-id="410a5-102">IMetaDataEmit2::SaveDeltaToMemory Method</span></span>
<span data-ttu-id="410a5-103">Uloží změny z aktuální relace úprav a pokračovat do paměti.</span><span class="sxs-lookup"><span data-stu-id="410a5-103">Saves changes from the current edit-and-continue session to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="410a5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="410a5-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveDeltaToMemory (  
    [out] void        *pbData,
    [in]  ULONG       cbData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="410a5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="410a5-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="410a5-106">[out] Adresa, na které chcete začít psát delta metadat.</span><span class="sxs-lookup"><span data-stu-id="410a5-106">[out] The address at which to begin writing the metadata delta.</span></span>  
  
 `cbData`  
 <span data-ttu-id="410a5-107">[v] Velikost změn.</span><span class="sxs-lookup"><span data-stu-id="410a5-107">[in] The size of the changes.</span></span> <span data-ttu-id="410a5-108">Použijte [IMetaDataEmit2::GetDeltaSaveSize](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md) k určení velikosti.</span><span class="sxs-lookup"><span data-stu-id="410a5-108">Use [IMetaDataEmit2::GetDeltaSaveSize](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md) to determine the size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="410a5-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="410a5-109">Requirements</span></span>  
 <span data-ttu-id="410a5-110">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="410a5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="410a5-111">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="410a5-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="410a5-112">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="410a5-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="410a5-113">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="410a5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="410a5-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="410a5-114">See also</span></span>

- [<span data-ttu-id="410a5-115">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="410a5-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="410a5-116">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="410a5-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
