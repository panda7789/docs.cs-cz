---
title: ICorDebugEnum::Skip – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEnum.Skip
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum::Skip
helpviewer_keywords:
- ICorDebugEnum::Skip method [.NET Framework debugging]
- Skip method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: e925d88a-67a5-4f76-88b8-09cedeed0232
topic_type:
- apiref
ms.openlocfilehash: 5c9049edd6d139bff29d21b65f9c87ec3e6de1a6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782975"
---
# <a name="icordebugenumskip-method"></a><span data-ttu-id="96ce0-102">ICorDebugEnum::Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="96ce0-102">ICorDebugEnum::Skip Method</span></span>
<span data-ttu-id="96ce0-103">Přesune kurzor do výčtu směrem nahoru podle zadaného počtu položek.</span><span class="sxs-lookup"><span data-stu-id="96ce0-103">Moves the cursor forward in the enumeration by the specified number of items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96ce0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="96ce0-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip (  
    [in] ULONG celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96ce0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="96ce0-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="96ce0-106">pro Počet položek, o které se má přesunout kurzor vpřed</span><span class="sxs-lookup"><span data-stu-id="96ce0-106">[in] The number of items by which to move the cursor forward.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96ce0-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="96ce0-107">Requirements</span></span>  
 <span data-ttu-id="96ce0-108">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96ce0-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96ce0-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="96ce0-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="96ce0-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="96ce0-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96ce0-111">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96ce0-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96ce0-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="96ce0-112">See also</span></span>

- [<span data-ttu-id="96ce0-113">Rozhraní ICorDebugEnum</span><span class="sxs-lookup"><span data-stu-id="96ce0-113">ICorDebugEnum Interface</span></span>](icordebugenum-interface1.md)
