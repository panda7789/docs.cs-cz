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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c7d280cd20b8ff76efe977983e3e9f6da32990c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413956"
---
# <a name="icordebugenumskip-method"></a><span data-ttu-id="da785-102">ICorDebugEnum::Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="da785-102">ICorDebugEnum::Skip Method</span></span>
<span data-ttu-id="da785-103">Přesune kurzor dál o zadaný počet položek ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="da785-103">Moves the cursor forward in the enumeration by the specified number of items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da785-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="da785-104">Syntax</span></span>  
  
```  
HRESULT Skip (  
    [in] ULONG celt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="da785-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="da785-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="da785-106">[v] Počet položek, kterým se mají předat přesunutí kurzoru.</span><span class="sxs-lookup"><span data-stu-id="da785-106">[in] The number of items by which to move the cursor forward.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da785-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="da785-107">Requirements</span></span>  
 <span data-ttu-id="da785-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da785-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da785-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="da785-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="da785-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="da785-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da785-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da785-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da785-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="da785-112">See Also</span></span>  
 [<span data-ttu-id="da785-113">ICorDebugEnum – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="da785-113">ICorDebugEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-interface1.md)
