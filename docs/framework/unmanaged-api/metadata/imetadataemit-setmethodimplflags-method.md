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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 28c0aa37bdcae2a09a4d53f920efd3ffe7117bd3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59145168"
---
# <a name="imetadataemitsetmethodimplflags-method"></a><span data-ttu-id="57c82-102">IMetaDataEmit::SetMethodImplFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="57c82-102">IMetaDataEmit::SetMethodImplFlags Method</span></span>
<span data-ttu-id="57c82-103">Nastaví nebo aktualizuje podpis metadat implementace zděděné metody, na který odkazuje zadaný token.</span><span class="sxs-lookup"><span data-stu-id="57c82-103">Sets or updates the metadata signature of the inherited method implementation that is referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57c82-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="57c82-104">Syntax</span></span>  
  
```  
HRESULT SetMethodImplFlags (   
    [in]  mdMethodDef   md,   
    [in]  DWORD         dwImplFlags   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57c82-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="57c82-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="57c82-106">[in] Token metody změnit.</span><span class="sxs-lookup"><span data-stu-id="57c82-106">[in] The token for the method to be changed.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="57c82-107">[in] Kombinace hodnot [cormethodimpl –](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) výčet, který určuje funkce implementace metody.</span><span class="sxs-lookup"><span data-stu-id="57c82-107">[in] A combination of the values of the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration that specifies the method implementation features.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57c82-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="57c82-108">Requirements</span></span>  
 <span data-ttu-id="57c82-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57c82-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57c82-110">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="57c82-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="57c82-111">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="57c82-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="57c82-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57c82-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57c82-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="57c82-113">See also</span></span>

- [<span data-ttu-id="57c82-114">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="57c82-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="57c82-115">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="57c82-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
