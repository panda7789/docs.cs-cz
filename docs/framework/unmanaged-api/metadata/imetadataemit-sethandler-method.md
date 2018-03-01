---
title: "IMetaDataEmit::SetHandler – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ccb35c12e1d9c2fade9d8760d0a2e39807c92de9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitsethandler-method"></a><span data-ttu-id="9d8f4-102">IMetaDataEmit::SetHandler – metoda</span><span class="sxs-lookup"><span data-stu-id="9d8f4-102">IMetaDataEmit::SetHandler Method</span></span>
<span data-ttu-id="9d8f4-103">Nastaví metodu, která odkazuje zadanou `IUnknown` ukazatel jako zpětné volání oznámení pro token přemapuje.</span><span class="sxs-lookup"><span data-stu-id="9d8f4-103">Sets the method referenced by the specified `IUnknown` pointer as a notification callback for token remaps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d8f4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d8f4-104">Syntax</span></span>  
  
```  
HRESULT SetHandler (   
    [in]  IUnknown    *pUnk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9d8f4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9d8f4-105">Parameters</span></span>  
 `pUnk`  
 <span data-ttu-id="9d8f4-106">[v] Obslužná rutina k registraci.</span><span class="sxs-lookup"><span data-stu-id="9d8f4-106">[in] The handler to register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d8f4-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9d8f4-107">Remarks</span></span>  
 <span data-ttu-id="9d8f4-108">Modul metadata odešle oznámení pomocí metody, které poskytuje `SetHandler`, na který nevydávají záznamy optimálního a který chcete optimalizovat uložené záznamy kompilátory.</span><span class="sxs-lookup"><span data-stu-id="9d8f4-108">The metadata engine sends notification by using the method that is provided by `SetHandler`, to compilers that do not generate records in an optimized way and that would like to optimize saved records.</span></span>  
  
 <span data-ttu-id="9d8f4-109">Pokud metoda zpětného volání není k dispozici prostřednictvím `SetHandler`, bude provedena žádná optimalizace na Uložit s výjimkou případů, kdy několik importovat obory byly sloučeny pomocí `IMapToken` na sloučení pro každý obor.</span><span class="sxs-lookup"><span data-stu-id="9d8f4-109">If the callback method is not provided through `SetHandler`, no optimization will be performed on save except where several import scopes have been merged using `IMapToken` on merge for each scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d8f4-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9d8f4-110">Requirements</span></span>  
 <span data-ttu-id="9d8f4-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d8f4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d8f4-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9d8f4-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9d8f4-113">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9d8f4-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9d8f4-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d8f4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d8f4-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="9d8f4-115">See Also</span></span>  
 [<span data-ttu-id="9d8f4-116">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9d8f4-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="9d8f4-117">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9d8f4-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
