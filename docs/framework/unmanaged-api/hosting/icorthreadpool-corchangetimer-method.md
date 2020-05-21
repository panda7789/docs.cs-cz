---
title: ICorThreadpool::CorChangeTimer – metoda
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorChangeTimer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorChangeTimer
helpviewer_keywords:
- CorChangeTimer method [.NET Framework hosting]
- ICorThreadpool::CorChangeTimer method [.NET Framework hosting]
ms.assetid: 82b03a59-5a87-43ed-9b75-e04b256e1a46
topic_type:
- apiref
ms.openlocfilehash: e2174afe0ee96bd153b7b40c73c0185d9058a0dc
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83760324"
---
# <a name="icorthreadpoolcorchangetimer-method"></a><span data-ttu-id="3dd1a-102">ICorThreadpool::CorChangeTimer – metoda</span><span class="sxs-lookup"><span data-stu-id="3dd1a-102">ICorThreadpool::CorChangeTimer Method</span></span>
<span data-ttu-id="3dd1a-103">Tato metoda podporuje infrastrukturu .NET Framework a není určena pro použití přímo v kódu.</span><span class="sxs-lookup"><span data-stu-id="3dd1a-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dd1a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3dd1a-104">Syntax</span></span>  
  
```cpp  
HRESULT CorChangeTimer (  
    [in]  HANDLE Timer,
    [in]  ULONG  DueTime,
    [in]  ULONG  Period,  
    [out] BOOL*  result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="3dd1a-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3dd1a-105">Requirements</span></span>  
 <span data-ttu-id="3dd1a-106">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3dd1a-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3dd1a-107">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3dd1a-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3dd1a-108">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3dd1a-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3dd1a-109">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3dd1a-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dd1a-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="3dd1a-110">See also</span></span>

- [<span data-ttu-id="3dd1a-111">ICorThreadpool – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3dd1a-111">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
