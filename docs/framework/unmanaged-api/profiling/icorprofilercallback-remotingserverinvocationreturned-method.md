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
ms.openlocfilehash: c121e403d116581ce3fa823d5d8cadbb2a58e296
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445782"
---
# <a name="icorprofilercallbackremotingserverinvocationreturned-method"></a><span data-ttu-id="82972-102">ICorProfilerCallback::RemotingServerInvocationReturned – metoda</span><span class="sxs-lookup"><span data-stu-id="82972-102">ICorProfilerCallback::RemotingServerInvocationReturned Method</span></span>
<span data-ttu-id="82972-103">Upozorní profileru, že proces skončil voláním metody v reakci na požadavek na vyvolání vzdálené metody.</span><span class="sxs-lookup"><span data-stu-id="82972-103">Notifies the profiler that the process has finished invoking a method in response to a remote method invocation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82972-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82972-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingServerInvocationReturned();  
```  
  
## <a name="requirements"></a><span data-ttu-id="82972-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="82972-105">Requirements</span></span>  
 <span data-ttu-id="82972-106">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82972-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82972-107">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="82972-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="82972-108">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="82972-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82972-109">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82972-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82972-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="82972-110">See also</span></span>

- [<span data-ttu-id="82972-111">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="82972-111">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
