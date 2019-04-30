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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61927839"
---
# <a name="igchostcollect-method"></a><span data-ttu-id="c95ff-102">IGCHost::Collect – metoda</span><span class="sxs-lookup"><span data-stu-id="c95ff-102">IGCHost::Collect Method</span></span>
<span data-ttu-id="c95ff-103">Vynutí kolekce vyskytují pro danou generaci bez ohledu na stav v aktuální kolekci uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="c95ff-103">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c95ff-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c95ff-104">Syntax</span></span>  
  
```  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c95ff-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c95ff-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="c95ff-106">[in] Generování, na kterém chcete provést uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="c95ff-106">[in] The generation on which to perform the garbage collection.</span></span> <span data-ttu-id="c95ff-107">Hodnota -1 označuje, že všech generací projdou uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="c95ff-107">A value of -1 indicates that all generations will undergo a garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c95ff-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c95ff-108">Requirements</span></span>  
 <span data-ttu-id="c95ff-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c95ff-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c95ff-110">**Záhlaví:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="c95ff-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="c95ff-111">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c95ff-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c95ff-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c95ff-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c95ff-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c95ff-113">See also</span></span>

- [<span data-ttu-id="c95ff-114">IGCHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c95ff-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
