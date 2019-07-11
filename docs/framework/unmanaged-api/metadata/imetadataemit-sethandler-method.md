---
title: IMetaDataEmit::SetHandler – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetHandler
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetHandler
helpviewer_keywords:
- IMetaDataEmit::SetHandler method [.NET Framework metadata]
- SetHandler method [.NET Framework metadata]
ms.assetid: c6c1aaaf-e2cd-407c-b73e-fbe6ffd83bb3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d50198cc6156d5bec8b8302a4624b0b7411a9c2d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751101"
---
# <a name="imetadataemitsethandler-method"></a><span data-ttu-id="b92e0-102">IMetaDataEmit::SetHandler – metoda</span><span class="sxs-lookup"><span data-stu-id="b92e0-102">IMetaDataEmit::SetHandler Method</span></span>
<span data-ttu-id="b92e0-103">Nastaví metodu odkazuje zadaný `IUnknown` ukazatele jako zpětné volání oznámení pro token přemapování.</span><span class="sxs-lookup"><span data-stu-id="b92e0-103">Sets the method referenced by the specified `IUnknown` pointer as a notification callback for token remaps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b92e0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b92e0-104">Syntax</span></span>  
  
```cpp  
HRESULT SetHandler (   
    [in]  IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b92e0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b92e0-105">Parameters</span></span>  
 `pUnk`  
 <span data-ttu-id="b92e0-106">[in] Obslužná rutina k registraci.</span><span class="sxs-lookup"><span data-stu-id="b92e0-106">[in] The handler to register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b92e0-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b92e0-107">Remarks</span></span>  
 <span data-ttu-id="b92e0-108">Metadata modulu odešle oznámení pomocí metody, která je poskytována `SetHandler`, na kompilátory, které nejsou generovány záznamy optimálního a, který chcete optimalizovat uložené záznamy.</span><span class="sxs-lookup"><span data-stu-id="b92e0-108">The metadata engine sends notification by using the method that is provided by `SetHandler`, to compilers that do not generate records in an optimized way and that would like to optimize saved records.</span></span>  
  
 <span data-ttu-id="b92e0-109">Pokud metoda zpětného volání není k dispozici prostřednictvím `SetHandler`, bez optimalizace se provede na Uložit s výjimkou případů, kdy několik importovat obory byly sloučeny pomocí `IMapToken` na sloučení pro každý obor.</span><span class="sxs-lookup"><span data-stu-id="b92e0-109">If the callback method is not provided through `SetHandler`, no optimization will be performed on save except where several import scopes have been merged using `IMapToken` on merge for each scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b92e0-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b92e0-110">Requirements</span></span>  
 <span data-ttu-id="b92e0-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b92e0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b92e0-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b92e0-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b92e0-113">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b92e0-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b92e0-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b92e0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b92e0-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b92e0-115">See also</span></span>

- [<span data-ttu-id="b92e0-116">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b92e0-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="b92e0-117">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b92e0-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
