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
ms.openlocfilehash: 64d9db09b3e604247ab6a26cdca9eca22adbaace
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976301"
---
# <a name="icordebugenumskip-method"></a><span data-ttu-id="3ae82-102">ICorDebugEnum::Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="3ae82-102">ICorDebugEnum::Skip Method</span></span>
<span data-ttu-id="3ae82-103">Přesune kurzor do výčtu směrem nahoru podle zadaného počtu položek.</span><span class="sxs-lookup"><span data-stu-id="3ae82-103">Moves the cursor forward in the enumeration by the specified number of items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ae82-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ae82-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip (  
    [in] ULONG celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3ae82-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3ae82-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="3ae82-106">pro Počet položek, o které se má přesunout kurzor vpřed</span><span class="sxs-lookup"><span data-stu-id="3ae82-106">[in] The number of items by which to move the cursor forward.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ae82-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3ae82-107">Requirements</span></span>  
 <span data-ttu-id="3ae82-108">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ae82-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ae82-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3ae82-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3ae82-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3ae82-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3ae82-111">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ae82-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ae82-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="3ae82-112">See also</span></span>

- [<span data-ttu-id="3ae82-113">ICorDebugEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3ae82-113">ICorDebugEnum Interface</span></span>](icordebugenum-interface1.md)
