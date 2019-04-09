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
ms.openlocfilehash: ac0e5db4a87b49d631bad4411f03fae8c1199aea
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125629"
---
# <a name="imetadataemitsethandler-method"></a><span data-ttu-id="99455-102">IMetaDataEmit::SetHandler – metoda</span><span class="sxs-lookup"><span data-stu-id="99455-102">IMetaDataEmit::SetHandler Method</span></span>
<span data-ttu-id="99455-103">Nastaví metodu odkazuje zadaný `IUnknown` ukazatele jako zpětné volání oznámení pro token přemapování.</span><span class="sxs-lookup"><span data-stu-id="99455-103">Sets the method referenced by the specified `IUnknown` pointer as a notification callback for token remaps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99455-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="99455-104">Syntax</span></span>  
  
```  
HRESULT SetHandler (   
    [in]  IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99455-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="99455-105">Parameters</span></span>  
 `pUnk`  
 <span data-ttu-id="99455-106">[in] Obslužná rutina k registraci.</span><span class="sxs-lookup"><span data-stu-id="99455-106">[in] The handler to register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99455-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="99455-107">Remarks</span></span>  
 <span data-ttu-id="99455-108">Metadata modulu odešle oznámení pomocí metody, která je poskytována `SetHandler`, na kompilátory, které nejsou generovány záznamy optimálního a, který chcete optimalizovat uložené záznamy.</span><span class="sxs-lookup"><span data-stu-id="99455-108">The metadata engine sends notification by using the method that is provided by `SetHandler`, to compilers that do not generate records in an optimized way and that would like to optimize saved records.</span></span>  
  
 <span data-ttu-id="99455-109">Pokud metoda zpětného volání není k dispozici prostřednictvím `SetHandler`, bez optimalizace se provede na Uložit s výjimkou případů, kdy několik importovat obory byly sloučeny pomocí `IMapToken` na sloučení pro každý obor.</span><span class="sxs-lookup"><span data-stu-id="99455-109">If the callback method is not provided through `SetHandler`, no optimization will be performed on save except where several import scopes have been merged using `IMapToken` on merge for each scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99455-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="99455-110">Requirements</span></span>  
 <span data-ttu-id="99455-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99455-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99455-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="99455-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="99455-113">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="99455-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="99455-114">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="99455-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="99455-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="99455-115">See also</span></span>

- [<span data-ttu-id="99455-116">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="99455-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="99455-117">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="99455-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
