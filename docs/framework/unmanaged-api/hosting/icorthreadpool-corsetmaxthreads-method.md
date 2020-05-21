---
title: ICorThreadpool::CorSetMaxThreads – metoda
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorSetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSetMaxThreads
helpviewer_keywords:
- ICorThreadpool::CorSetMaxThreads method [.NET Framework hosting]
- CorSetMaxThreads method [.NET Framework hosting]
ms.assetid: 4a846238-df4e-4060-ba3b-5173f6a51e85
topic_type:
- apiref
ms.openlocfilehash: 7f972bcfedd028d85debbbd60968a57c4d64ee0c
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83760325"
---
# <a name="icorthreadpoolcorsetmaxthreads-method"></a><span data-ttu-id="0f347-102">ICorThreadpool::CorSetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="0f347-102">ICorThreadpool::CorSetMaxThreads Method</span></span>
<span data-ttu-id="0f347-103">Tato metoda podporuje infrastrukturu .NET Framework a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="0f347-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f347-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0f347-104">Syntax</span></span>  
  
```cpp  
HRESULT CorSetMaxThreads (  
    [in] DWORD MaxWorkerThreads,  
    [in] DWORD MaxIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="0f347-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0f347-105">Requirements</span></span>  
 <span data-ttu-id="0f347-106">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f347-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f347-107">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0f347-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0f347-108">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0f347-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0f347-109">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f347-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f347-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="0f347-110">See also</span></span>

- [<span data-ttu-id="0f347-111">ICorThreadpool – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0f347-111">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
