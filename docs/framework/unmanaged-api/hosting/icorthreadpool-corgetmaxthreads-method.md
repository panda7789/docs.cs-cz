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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c25f39cf64f462ac319803354e6a2a54ea482b9e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436933"
---
# <a name="icorthreadpoolcorgetmaxthreads-method"></a><span data-ttu-id="22142-102">ICorThreadpool::CorGetMaxThreads – metoda</span><span class="sxs-lookup"><span data-stu-id="22142-102">ICorThreadpool::CorGetMaxThreads Method</span></span>
<span data-ttu-id="22142-103">Tato metoda podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="22142-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22142-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22142-104">Syntax</span></span>  
  
```  
HRESULT CorGetMaxThreads (  
    [out] DWORD *MaxWorkerThreads,  
    [out] DWORD *MaxIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="22142-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="22142-105">Requirements</span></span>  
 <span data-ttu-id="22142-106">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22142-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22142-107">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="22142-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="22142-108">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="22142-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="22142-109">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22142-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22142-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="22142-110">See Also</span></span>  
 [<span data-ttu-id="22142-111">ICorThreadpool – rozhraní</span><span class="sxs-lookup"><span data-stu-id="22142-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
