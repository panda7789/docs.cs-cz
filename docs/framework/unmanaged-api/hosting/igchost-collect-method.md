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
ms.openlocfilehash: e20ea6addc1ae3f99b4b3d65f532e0128ac160b3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134973"
---
# <a name="igchostcollect-method"></a><span data-ttu-id="da2cc-102">IGCHost::Collect – metoda</span><span class="sxs-lookup"><span data-stu-id="da2cc-102">IGCHost::Collect Method</span></span>
<span data-ttu-id="da2cc-103">Vynutí, aby se kolekce stala pro danou generaci, bez ohledu na stav aktuálního uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="da2cc-103">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da2cc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="da2cc-104">Syntax</span></span>  
  
```cpp  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da2cc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="da2cc-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="da2cc-106">pro Generování, na kterém má být provedeno uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="da2cc-106">[in] The generation on which to perform the garbage collection.</span></span> <span data-ttu-id="da2cc-107">Hodnota-1 označuje, že všechny generace budou podléhat uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="da2cc-107">A value of -1 indicates that all generations will undergo a garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da2cc-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="da2cc-108">Requirements</span></span>  
 <span data-ttu-id="da2cc-109">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da2cc-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da2cc-110">**Hlavička:** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="da2cc-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="da2cc-111">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="da2cc-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="da2cc-112">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da2cc-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da2cc-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="da2cc-113">See also</span></span>

- [<span data-ttu-id="da2cc-114">IGCHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="da2cc-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
