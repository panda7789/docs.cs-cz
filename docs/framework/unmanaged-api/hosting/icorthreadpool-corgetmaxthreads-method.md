---
title: ICorThreadpool::CorGetMaxThreads – metoda
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorGetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorGetMaxThreads
helpviewer_keywords:
- CorGetMaxThreads method [.NET Framework hosting]
- ICorThreadpool::CorGetMaxThreads method [.NET Framework hosting]
ms.assetid: 2861533a-cda0-47b3-b716-0d363505289b
topic_type:
- apiref
ms.openlocfilehash: 46ffdb21c1f3b501cc28afffc224349887af5644
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762745"
---
# <a name="icorthreadpoolcorgetmaxthreads-method"></a><span data-ttu-id="68bd9-102">ICorThreadpool::CorGetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="68bd9-102">ICorThreadpool::CorGetMaxThreads Method</span></span>
<span data-ttu-id="68bd9-103">Tato metoda podporuje infrastrukturu .NET Framework a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="68bd9-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68bd9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68bd9-104">Syntax</span></span>  
  
```cpp  
HRESULT CorGetMaxThreads (  
    [out] DWORD *MaxWorkerThreads,  
    [out] DWORD *MaxIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="68bd9-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="68bd9-105">Requirements</span></span>  
 <span data-ttu-id="68bd9-106">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68bd9-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68bd9-107">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="68bd9-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="68bd9-108">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="68bd9-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="68bd9-109">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68bd9-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68bd9-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="68bd9-110">See also</span></span>

- [<span data-ttu-id="68bd9-111">ICorThreadpool – rozhraní</span><span class="sxs-lookup"><span data-stu-id="68bd9-111">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
