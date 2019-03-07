---
title: ICorDebug::EnumerateProcesses – metoda
ms.date: 03/30/2017
api_name:
- ICorDebug.EnumerateProcesses
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- EnumerateProcesses
helpviewer_keywords:
- EnumerateProcesses method [.NET Framework debugging]
- ICorDebug::EnumerateProcesses method [.NET Framework debugging]
ms.assetid: ba25d166-1d28-4f1d-aca2-de298bbca669
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ecf5160a7ceb7a4d2f1d64d83f573f8450966dc0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57476669"
---
# <a name="icordebugenumerateprocesses-method"></a><span data-ttu-id="56ce4-102">ICorDebug::EnumerateProcesses – metoda</span><span class="sxs-lookup"><span data-stu-id="56ce4-102">ICorDebug::EnumerateProcesses Method</span></span>
<span data-ttu-id="56ce4-103">Získá enumerátor pro procesy, které jsou právě laděny.</span><span class="sxs-lookup"><span data-stu-id="56ce4-103">Gets an enumerator for the processes that are being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56ce4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56ce4-104">Syntax</span></span>  
  
```  
HRESULT EnumerateProcesses (  
    [out] ICorDebugProcessEnum      **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56ce4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="56ce4-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="56ce4-106">Ukazatel na adresu icordebugprocessenum – objekt, který je enumerátor pro procesy, které jsou právě laděny.</span><span class="sxs-lookup"><span data-stu-id="56ce4-106">A pointer to the address of an ICorDebugProcessEnum object that is the enumerator for the processes being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56ce4-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="56ce4-107">Requirements</span></span>  
 <span data-ttu-id="56ce4-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56ce4-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56ce4-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="56ce4-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="56ce4-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="56ce4-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56ce4-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56ce4-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56ce4-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="56ce4-112">See also</span></span>
- [<span data-ttu-id="56ce4-113">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="56ce4-113">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
