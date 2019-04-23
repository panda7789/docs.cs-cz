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
ms.openlocfilehash: b640a6dee9ae50278d6a844d20d21eae156e9dd7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59200958"
---
# <a name="icorprofilercallbackexceptionclrcatcherexecute-method"></a><span data-ttu-id="cc7b4-102">ICorProfilerCallback::ExceptionCLRCatcherExecute – metoda</span><span class="sxs-lookup"><span data-stu-id="cc7b4-102">ICorProfilerCallback::ExceptionCLRCatcherExecute Method</span></span>
<span data-ttu-id="cc7b4-103">Voláno, když `catch` block pro provedení výjimku v rámci common language runtime (CLR), samotného.</span><span class="sxs-lookup"><span data-stu-id="cc7b4-103">Called when a `catch` block for an exception is executed inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="cc7b4-104">Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="cc7b4-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc7b4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc7b4-105">Syntax</span></span>  
  
```  
HRESULT ExceptionCLRCatcherExecute();  
```  
  
## <a name="requirements"></a><span data-ttu-id="cc7b4-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cc7b4-106">Requirements</span></span>  
 <span data-ttu-id="cc7b4-107">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc7b4-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc7b4-108">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cc7b4-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cc7b4-109">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc7b4-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc7b4-110">**Verze rozhraní .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="cc7b4-110">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc7b4-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cc7b4-111">See also</span></span>

- [<span data-ttu-id="cc7b4-112">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cc7b4-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="cc7b4-113">ExceptionCLRCatcherFound – metoda</span><span class="sxs-lookup"><span data-stu-id="cc7b4-113">ExceptionCLRCatcherFound Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherfound-method.md)
