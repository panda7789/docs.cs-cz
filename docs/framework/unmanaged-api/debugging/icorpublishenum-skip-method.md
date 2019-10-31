---
title: ICorPublishEnum::Skip – metoda
ms.date: 03/30/2017
api_name:
- ICorPublishEnum.Skip
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum::Skip
helpviewer_keywords:
- ICorPublishEnum::Skip method [.NET Framework debugging]
- Skip method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 1680ec06-4ab0-447e-93ad-cdb8693fde5c
topic_type:
- apiref
ms.openlocfilehash: eb9e5bdf85c6d487fd82422522854076c03e2288
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140451"
---
# <a name="icorpublishenumskip-method"></a><span data-ttu-id="c2ef8-102">ICorPublishEnum::Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="c2ef8-102">ICorPublishEnum::Skip Method</span></span>
<span data-ttu-id="c2ef8-103">Přesune kurzor do výčtu směrem nahoru podle zadaného počtu položek.</span><span class="sxs-lookup"><span data-stu-id="c2ef8-103">Moves the cursor forward in the enumeration by the specified number of items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2ef8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c2ef8-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2ef8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c2ef8-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="c2ef8-106">pro Počet položek, o které se má přesunout kurzor vpřed</span><span class="sxs-lookup"><span data-stu-id="c2ef8-106">[in] The number of items by which to move the cursor forward.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2ef8-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c2ef8-107">Requirements</span></span>  
 <span data-ttu-id="c2ef8-108">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2ef8-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2ef8-109">**Hlavička:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="c2ef8-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="c2ef8-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c2ef8-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2ef8-111">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2ef8-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2ef8-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c2ef8-112">See also</span></span>

- [<span data-ttu-id="c2ef8-113">ICorPublishEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c2ef8-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)
