---
title: ICorThreadpool::CorDeleteTimer – metoda
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorDeleteTimer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorDeleteTimer
helpviewer_keywords:
- ICorThreadpool::CorDeleteTimer method [.NET Framework hosting]
- CorDeleteTimer method [.NET Framework hosting]
ms.assetid: 74847c35-7ca1-466a-b750-b25e7b03d100
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 098c23dd0ddff4342aa4cefbaa4e149ed95a1cb3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59178344"
---
# <a name="icorthreadpoolcordeletetimer-method"></a><span data-ttu-id="c1e3e-102">ICorThreadpool::CorDeleteTimer – metoda</span><span class="sxs-lookup"><span data-stu-id="c1e3e-102">ICorThreadpool::CorDeleteTimer Method</span></span>
<span data-ttu-id="c1e3e-103">Tato metoda podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="c1e3e-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1e3e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c1e3e-104">Syntax</span></span>  
  
```  
HRESULT CorDeleteTimer (  
    [in]  HANDLE Timer,  
    [in]  HANDLE CompletionEvent,  
    [out] BOOL*  result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="c1e3e-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c1e3e-105">Requirements</span></span>  
 <span data-ttu-id="c1e3e-106">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1e3e-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1e3e-107">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c1e3e-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c1e3e-108">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c1e3e-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c1e3e-109">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1e3e-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1e3e-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c1e3e-110">See also</span></span>

- [<span data-ttu-id="c1e3e-111">ICorThreadpool – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c1e3e-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
