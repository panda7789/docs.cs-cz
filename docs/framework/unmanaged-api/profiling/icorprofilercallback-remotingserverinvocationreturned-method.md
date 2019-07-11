---
title: ICorProfilerCallback::RemotingServerInvocationReturned – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingServerInvocationReturned
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerInvocationReturned
helpviewer_keywords:
- ICorProfilerCallback::RemotingServerInvocationReturned method [.NET Framework profiling]
- RemotingServerInvocationReturned method [.NET Framework profiling]
ms.assetid: a4de6805-e159-4280-99e5-3390c86166d0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 731907d69f3257306c536d73112300ffd5225538
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782897"
---
# <a name="icorprofilercallbackremotingserverinvocationreturned-method"></a><span data-ttu-id="f41dd-102">ICorProfilerCallback::RemotingServerInvocationReturned – metoda</span><span class="sxs-lookup"><span data-stu-id="f41dd-102">ICorProfilerCallback::RemotingServerInvocationReturned Method</span></span>
<span data-ttu-id="f41dd-103">Proces dokončení volání metody v reakci na žádost o vzdálené metody vyvolání upozornění profileru.</span><span class="sxs-lookup"><span data-stu-id="f41dd-103">Notifies the profiler that the process has finished invoking a method in response to a remote method invocation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f41dd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f41dd-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingServerInvocationReturned();  
```  
  
## <a name="requirements"></a><span data-ttu-id="f41dd-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f41dd-105">Requirements</span></span>  
 <span data-ttu-id="f41dd-106">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f41dd-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f41dd-107">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f41dd-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f41dd-108">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f41dd-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f41dd-109">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f41dd-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f41dd-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f41dd-110">See also</span></span>

- [<span data-ttu-id="f41dd-111">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f41dd-111">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
