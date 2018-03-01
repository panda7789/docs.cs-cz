---
title: "ICorDebug::EnumerateProcesses – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4ffabcc97a4af33fc859cd096e671f98d52e89e1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugenumerateprocesses-method"></a><span data-ttu-id="1c4c8-102">ICorDebug::EnumerateProcesses – metoda</span><span class="sxs-lookup"><span data-stu-id="1c4c8-102">ICorDebug::EnumerateProcesses Method</span></span>
<span data-ttu-id="1c4c8-103">Získá enumerátor pro procesy, které se právě ladí.</span><span class="sxs-lookup"><span data-stu-id="1c4c8-103">Gets an enumerator for the processes that are being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c4c8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1c4c8-104">Syntax</span></span>  
  
```  
HRESULT EnumerateProcesses (  
    [out] ICorDebugProcessEnum      **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1c4c8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1c4c8-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="1c4c8-106">Ukazatel na adresu ICorDebugProcessEnum objekt, který je enumerátor pro procesy laděné.</span><span class="sxs-lookup"><span data-stu-id="1c4c8-106">A pointer to the address of an ICorDebugProcessEnum object that is the enumerator for the processes being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c4c8-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1c4c8-107">Requirements</span></span>  
 <span data-ttu-id="1c4c8-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c4c8-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c4c8-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1c4c8-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1c4c8-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c4c8-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c4c8-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c4c8-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c4c8-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="1c4c8-112">See Also</span></span>  
 [<span data-ttu-id="1c4c8-113">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1c4c8-113">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
