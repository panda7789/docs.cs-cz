---
title: IMetaDataEmit::SetMethodImplFlags – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetMethodImplFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetMethodImplFlags
helpviewer_keywords:
- IMetaDataEmit::SetMethodImplFlags method [.NET Framework metadata]
- SetMethodImpFlags method [.NET Framework metadata]
ms.assetid: 4bc82d9b-9544-4be3-ba51-a2d4d806158a
topic_type:
- apiref
ms.openlocfilehash: b8755629cca27784609de8166dddf44ed1c82bdc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432536"
---
# <a name="imetadataemitsetmethodimplflags-method"></a><span data-ttu-id="0a2e0-102">IMetaDataEmit::SetMethodImplFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="0a2e0-102">IMetaDataEmit::SetMethodImplFlags Method</span></span>
<span data-ttu-id="0a2e0-103">Nastaví nebo aktualizuje podpis metadat zděděné implementace metody, na kterou odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="0a2e0-103">Sets or updates the metadata signature of the inherited method implementation that is referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a2e0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0a2e0-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodImplFlags (   
    [in]  mdMethodDef   md,   
    [in]  DWORD         dwImplFlags   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a2e0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0a2e0-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="0a2e0-106">pro Token pro metodu, která má být změněna.</span><span class="sxs-lookup"><span data-stu-id="0a2e0-106">[in] The token for the method to be changed.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="0a2e0-107">pro Kombinace hodnot výčtu [CorMethodImpl –](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) , která určuje funkce implementace metody.</span><span class="sxs-lookup"><span data-stu-id="0a2e0-107">[in] A combination of the values of the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration that specifies the method implementation features.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a2e0-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0a2e0-108">Requirements</span></span>  
 <span data-ttu-id="0a2e0-109">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a2e0-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a2e0-110">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="0a2e0-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0a2e0-111">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="0a2e0-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0a2e0-112">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a2e0-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a2e0-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0a2e0-113">See also</span></span>

- [<span data-ttu-id="0a2e0-114">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a2e0-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="0a2e0-115">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a2e0-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
