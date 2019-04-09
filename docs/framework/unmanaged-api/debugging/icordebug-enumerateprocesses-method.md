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
ms.openlocfilehash: 7bc82c506cf7e223e672a62ca74b215cac870e50
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59123825"
---
# <a name="icordebugenumerateprocesses-method"></a><span data-ttu-id="e9220-102">ICorDebug::EnumerateProcesses – metoda</span><span class="sxs-lookup"><span data-stu-id="e9220-102">ICorDebug::EnumerateProcesses Method</span></span>
<span data-ttu-id="e9220-103">Získá enumerátor pro procesy, které jsou právě laděny.</span><span class="sxs-lookup"><span data-stu-id="e9220-103">Gets an enumerator for the processes that are being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9220-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9220-104">Syntax</span></span>  
  
```  
HRESULT EnumerateProcesses (  
    [out] ICorDebugProcessEnum      **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9220-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9220-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="e9220-106">Ukazatel na adresu icordebugprocessenum – objekt, který je enumerátor pro procesy, které jsou právě laděny.</span><span class="sxs-lookup"><span data-stu-id="e9220-106">A pointer to the address of an ICorDebugProcessEnum object that is the enumerator for the processes being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9220-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e9220-107">Requirements</span></span>  
 <span data-ttu-id="e9220-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9220-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9220-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e9220-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e9220-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9220-110">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="e9220-111">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="e9220-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e9220-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e9220-112">See also</span></span>

- [<span data-ttu-id="e9220-113">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e9220-113">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
