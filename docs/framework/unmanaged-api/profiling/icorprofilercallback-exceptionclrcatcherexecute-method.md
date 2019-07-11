---
title: ICorProfilerCallback::ExceptionCLRCatcherExecute – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2a17776b38d7e16b39f966e0d83d50a7d004d4c3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776066"
---
# <a name="icorprofilercallbackexceptionclrcatcherexecute-method"></a><span data-ttu-id="95a2d-102">ICorProfilerCallback::ExceptionCLRCatcherExecute – metoda</span><span class="sxs-lookup"><span data-stu-id="95a2d-102">ICorProfilerCallback::ExceptionCLRCatcherExecute Method</span></span>
<span data-ttu-id="95a2d-103">Voláno, když `catch` block pro provedení výjimku v rámci common language runtime (CLR), samotného.</span><span class="sxs-lookup"><span data-stu-id="95a2d-103">Called when a `catch` block for an exception is executed inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="95a2d-104">Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="95a2d-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95a2d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95a2d-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCLRCatcherExecute();  
```  
  
## <a name="requirements"></a><span data-ttu-id="95a2d-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="95a2d-106">Requirements</span></span>  
 <span data-ttu-id="95a2d-107">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95a2d-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95a2d-108">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="95a2d-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="95a2d-109">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="95a2d-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="95a2d-110">**Verze rozhraní .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="95a2d-110">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95a2d-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="95a2d-111">See also</span></span>

- [<span data-ttu-id="95a2d-112">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="95a2d-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="95a2d-113">ExceptionCLRCatcherFound – metoda</span><span class="sxs-lookup"><span data-stu-id="95a2d-113">ExceptionCLRCatcherFound Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherfound-method.md)
