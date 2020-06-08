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
ms.openlocfilehash: b79c8dd9f27805e00535dde53c6ee9f5ee457b42
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500260"
---
# <a name="icorprofilercallbackexceptionclrcatcherexecute-method"></a><span data-ttu-id="35fcb-102">ICorProfilerCallback::ExceptionCLRCatcherExecute – metoda</span><span class="sxs-lookup"><span data-stu-id="35fcb-102">ICorProfilerCallback::ExceptionCLRCatcherExecute Method</span></span>
<span data-ttu-id="35fcb-103">Volá se, když se v rámci `catch` samotného modulu CLR (Common Language Runtime) spustí blok pro výjimku.</span><span class="sxs-lookup"><span data-stu-id="35fcb-103">Called when a `catch` block for an exception is executed inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="35fcb-104">Tato metoda je zastaralá ve verzi .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="35fcb-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35fcb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="35fcb-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCLRCatcherExecute();  
```  
  
## <a name="requirements"></a><span data-ttu-id="35fcb-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="35fcb-106">Requirements</span></span>  
 <span data-ttu-id="35fcb-107">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35fcb-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35fcb-108">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="35fcb-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="35fcb-109">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="35fcb-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="35fcb-110">**Verze .NET Framework:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="35fcb-110">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35fcb-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="35fcb-111">See also</span></span>

- [<span data-ttu-id="35fcb-112">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="35fcb-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="35fcb-113">ExceptionCLRCatcherFound – metoda</span><span class="sxs-lookup"><span data-stu-id="35fcb-113">ExceptionCLRCatcherFound Method</span></span>](icorprofilercallback-exceptionclrcatcherfound-method.md)
