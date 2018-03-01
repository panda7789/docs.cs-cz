---
title: "ICorProfilerCallback::ExceptionCLRCatcherExecute – metoda"
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
- ICorProfilerCallback.ExceptionCLRCatcherExecute
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCLRCatcherExecute
helpviewer_keywords:
- ExceptionCLRCatcherExecute method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionCLRCatcherExecute method [.NET Framework profiling]
ms.assetid: aaac8f98-5cf4-42c7-b04b-556cce367e36
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c5d278fa196836d18b8515bee5af1946b2ca4d74
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackexceptionclrcatcherexecute-method"></a><span data-ttu-id="dbe3f-102">ICorProfilerCallback::ExceptionCLRCatcherExecute – metoda</span><span class="sxs-lookup"><span data-stu-id="dbe3f-102">ICorProfilerCallback::ExceptionCLRCatcherExecute Method</span></span>
<span data-ttu-id="dbe3f-103">Voláno, když `catch` blokovat pro výjimku je spustit v rámci modul CLR (CLR) sám sebe.</span><span class="sxs-lookup"><span data-stu-id="dbe3f-103">Called when a `catch` block for an exception is executed inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="dbe3f-104">Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="dbe3f-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbe3f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dbe3f-105">Syntax</span></span>  
  
```  
HRESULT ExceptionCLRCatcherExecute();  
```  
  
## <a name="requirements"></a><span data-ttu-id="dbe3f-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dbe3f-106">Requirements</span></span>  
 <span data-ttu-id="dbe3f-107">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbe3f-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbe3f-108">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dbe3f-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dbe3f-109">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dbe3f-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dbe3f-110">**Verze rozhraní .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="dbe3f-110">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbe3f-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="dbe3f-111">See Also</span></span>  
 [<span data-ttu-id="dbe3f-112">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dbe3f-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="dbe3f-113">ExceptionCLRCatcherFound – metoda</span><span class="sxs-lookup"><span data-stu-id="dbe3f-113">ExceptionCLRCatcherFound Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherfound-method.md)
