---
title: ICorProfilerCallback::RemotingServerInvocationStarted – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingServerInvocationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerInvocationStarted
helpviewer_keywords:
- RemotingServerInvocationStarted method [.NET Framework profiling]
- ICorProfilerCallback::RemotingServerInvocationStarted method [.NET Framework profiling]
ms.assetid: 86051a11-ad8e-4ace-9a11-ff0f982a5e11
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 091851a5729d496fb030f5d09402f524ca712ae6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54556545"
---
# <a name="icorprofilercallbackremotingserverinvocationstarted-method"></a><span data-ttu-id="5d19c-102">ICorProfilerCallback::RemotingServerInvocationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="5d19c-102">ICorProfilerCallback::RemotingServerInvocationStarted Method</span></span>
<span data-ttu-id="5d19c-103">Oznámí profileru, že proces je volání metody v reakci na žádost o vzdálené metody volání.</span><span class="sxs-lookup"><span data-stu-id="5d19c-103">Notifies the profiler that the process is invoking a method in response to a remote method invocation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d19c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5d19c-104">Syntax</span></span>  
  
```  
HRESULT RemotingServerInvocationStarted();  
```  
  
## <a name="requirements"></a><span data-ttu-id="5d19c-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5d19c-105">Requirements</span></span>  
 <span data-ttu-id="5d19c-106">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d19c-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d19c-107">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5d19c-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5d19c-108">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5d19c-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d19c-109">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d19c-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d19c-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5d19c-110">See also</span></span>
- [<span data-ttu-id="5d19c-111">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5d19c-111">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
