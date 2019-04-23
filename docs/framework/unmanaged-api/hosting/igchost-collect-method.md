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
ms.openlocfilehash: fdacb454783cfb8f90ea5a73807f0a199e16475d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59154775"
---
# <a name="igchostcollect-method"></a><span data-ttu-id="b988a-102">IGCHost::Collect – metoda</span><span class="sxs-lookup"><span data-stu-id="b988a-102">IGCHost::Collect Method</span></span>
<span data-ttu-id="b988a-103">Vynutí kolekce vyskytují pro danou generaci bez ohledu na stav v aktuální kolekci uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="b988a-103">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b988a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b988a-104">Syntax</span></span>  
  
```  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b988a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b988a-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="b988a-106">[in] Generování, na kterém chcete provést uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="b988a-106">[in] The generation on which to perform the garbage collection.</span></span> <span data-ttu-id="b988a-107">Hodnota -1 označuje, že všech generací projdou uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="b988a-107">A value of -1 indicates that all generations will undergo a garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b988a-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b988a-108">Requirements</span></span>  
 <span data-ttu-id="b988a-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b988a-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b988a-110">**Záhlaví:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="b988a-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="b988a-111">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b988a-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b988a-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b988a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b988a-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b988a-113">See also</span></span>

- [<span data-ttu-id="b988a-114">IGCHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b988a-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
