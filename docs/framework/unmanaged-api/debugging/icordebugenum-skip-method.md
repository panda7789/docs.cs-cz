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
ms.openlocfilehash: 1e2d7a344cabb1ab816e4fe696ebb47276397ec3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774553"
---
# <a name="icordebugenumskip-method"></a><span data-ttu-id="02f6e-102">ICorDebugEnum::Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="02f6e-102">ICorDebugEnum::Skip Method</span></span>
<span data-ttu-id="02f6e-103">Přesune kurzor vpřed o zadaný počet položek ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="02f6e-103">Moves the cursor forward in the enumeration by the specified number of items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02f6e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="02f6e-104">Syntax</span></span>  
  
```  
HRESULT Skip (  
    [in] ULONG celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="02f6e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="02f6e-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="02f6e-106">[in] Počet položek, podle kterého se má přesunout kurzor vpřed.</span><span class="sxs-lookup"><span data-stu-id="02f6e-106">[in] The number of items by which to move the cursor forward.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02f6e-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="02f6e-107">Requirements</span></span>  
 <span data-ttu-id="02f6e-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02f6e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02f6e-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="02f6e-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="02f6e-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="02f6e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="02f6e-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02f6e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02f6e-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="02f6e-112">See also</span></span>

- [<span data-ttu-id="02f6e-113">Icordebugenum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="02f6e-113">ICorDebugEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-interface1.md)
