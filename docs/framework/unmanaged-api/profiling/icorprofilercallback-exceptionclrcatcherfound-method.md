---
title: ICorProfilerCallback::ExceptionCLRCatcherFound – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCLRCatcherFound
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCLRCatcherFound
helpviewer_keywords:
- ICorProfilerCallback::ExceptionCLRCatcherFound method [.NET Framework profiling]
- ExceptionCLRCatcherFound method [.NET Framework profiling]
ms.assetid: 73fe8b4b-8f9a-4ba5-a10c-b26521396a66
topic_type:
- apiref
ms.openlocfilehash: 4f4d53b086453adce38902518f2de3dde1f2812f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500244"
---
# <a name="icorprofilercallbackexceptionclrcatcherfound-method"></a><span data-ttu-id="9f265-102">ICorProfilerCallback::ExceptionCLRCatcherFound – metoda</span><span class="sxs-lookup"><span data-stu-id="9f265-102">ICorProfilerCallback::ExceptionCLRCatcherFound Method</span></span>
<span data-ttu-id="9f265-103">Volá se, když `catch` se v samotném modulu CLR (Common Language Runtime) najde blok pro výjimku.</span><span class="sxs-lookup"><span data-stu-id="9f265-103">Called when a `catch` block for an exception is found inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="9f265-104">Tato metoda je zastaralá ve verzi .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="9f265-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f265-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f265-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCLRCatcherFound();  
```  
  
## <a name="requirements"></a><span data-ttu-id="9f265-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9f265-106">Requirements</span></span>  
 <span data-ttu-id="9f265-107">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f265-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f265-108">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="9f265-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9f265-109">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9f265-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9f265-110">**Verze .NET Framework:** 1,0</span><span class="sxs-lookup"><span data-stu-id="9f265-110">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f265-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9f265-111">See also</span></span>

- [<span data-ttu-id="9f265-112">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9f265-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="9f265-113">ExceptionCLRCatcherExecute – metoda</span><span class="sxs-lookup"><span data-stu-id="9f265-113">ExceptionCLRCatcherExecute Method</span></span>](icorprofilercallback-exceptionclrcatcherexecute-method.md)
