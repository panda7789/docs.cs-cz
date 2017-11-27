---
title: "IGCHost::Collect – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCHost.Collect
api_location: mscoree.dll
api_type: COM
f1_keywords: Collect
helpviewer_keywords:
- Collect method, IGCHost interface [.NET Framework hosting]
- IGCHost::Collect method [.NET Framework hosting]
ms.assetid: fc7d9448-3186-494d-9f0d-ea39717e9a82
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d97a988db48cc9bfdf8cf1e260c28e0169eb73f9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="igchostcollect-method"></a><span data-ttu-id="093cc-102">IGCHost::Collect – metoda</span><span class="sxs-lookup"><span data-stu-id="093cc-102">IGCHost::Collect Method</span></span>
<span data-ttu-id="093cc-103">Vynutí kolekci vyskytují pro danou generaci, bez ohledu na stav v aktuální kolekci paměti.</span><span class="sxs-lookup"><span data-stu-id="093cc-103">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="093cc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="093cc-104">Syntax</span></span>  
  
```  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="093cc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="093cc-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="093cc-106">[v] Generování, na které se má provést uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="093cc-106">[in] The generation on which to perform the garbage collection.</span></span> <span data-ttu-id="093cc-107">Hodnota -1 označuje, že všechny generace určitým uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="093cc-107">A value of -1 indicates that all generations will undergo a garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="093cc-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="093cc-108">Requirements</span></span>  
 <span data-ttu-id="093cc-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="093cc-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="093cc-110">**Záhlaví:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="093cc-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="093cc-111">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="093cc-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="093cc-112">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="093cc-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="093cc-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="093cc-113">See Also</span></span>  
 [<span data-ttu-id="093cc-114">Igchost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="093cc-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
