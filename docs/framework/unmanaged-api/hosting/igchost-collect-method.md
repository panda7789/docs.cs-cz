---
title: IGCHost::Collect – metoda
ms.date: 03/30/2017
api_name:
- IGCHost.Collect
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Collect
helpviewer_keywords:
- Collect method, IGCHost interface [.NET Framework hosting]
- IGCHost::Collect method [.NET Framework hosting]
ms.assetid: fc7d9448-3186-494d-9f0d-ea39717e9a82
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f911d99470b9870f5c42d4170a4024123c10e7f3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54511118"
---
# <a name="igchostcollect-method"></a><span data-ttu-id="b6b10-102">IGCHost::Collect – metoda</span><span class="sxs-lookup"><span data-stu-id="b6b10-102">IGCHost::Collect Method</span></span>
<span data-ttu-id="b6b10-103">Vynutí kolekce vyskytují pro danou generaci bez ohledu na stav v aktuální kolekci uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="b6b10-103">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6b10-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6b10-104">Syntax</span></span>  
  
```  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b6b10-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b6b10-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="b6b10-106">[in] Generování, na kterém chcete provést uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="b6b10-106">[in] The generation on which to perform the garbage collection.</span></span> <span data-ttu-id="b6b10-107">Hodnota -1 označuje, že všech generací projdou uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="b6b10-107">A value of -1 indicates that all generations will undergo a garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6b10-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b6b10-108">Requirements</span></span>  
 <span data-ttu-id="b6b10-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6b10-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6b10-110">**Záhlaví:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="b6b10-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="b6b10-111">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b6b10-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b6b10-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6b10-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6b10-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b6b10-113">See also</span></span>
- [<span data-ttu-id="b6b10-114">IGCHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b6b10-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
