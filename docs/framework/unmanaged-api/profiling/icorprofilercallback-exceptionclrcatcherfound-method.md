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
ms.openlocfilehash: ef5122d49c428af4faa27f3827a5c60721ef0f74
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435824"
---
# <a name="icorprofilercallbackexceptionclrcatcherfound-method"></a><span data-ttu-id="c2992-102">ICorProfilerCallback::ExceptionCLRCatcherFound – metoda</span><span class="sxs-lookup"><span data-stu-id="c2992-102">ICorProfilerCallback::ExceptionCLRCatcherFound Method</span></span>
<span data-ttu-id="c2992-103">Volá se, když se v samotném modulu CLR (Common Language Runtime) najde blok `catch` pro výjimku.</span><span class="sxs-lookup"><span data-stu-id="c2992-103">Called when a `catch` block for an exception is found inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="c2992-104">Tato metoda je zastaralá ve verzi .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="c2992-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2992-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c2992-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCLRCatcherFound();  
```  
  
## <a name="requirements"></a><span data-ttu-id="c2992-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c2992-106">Requirements</span></span>  
 <span data-ttu-id="c2992-107">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2992-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2992-108">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c2992-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c2992-109">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c2992-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2992-110">**Verze .NET Framework:** 1,0</span><span class="sxs-lookup"><span data-stu-id="c2992-110">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2992-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c2992-111">See also</span></span>

- [<span data-ttu-id="c2992-112">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c2992-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="c2992-113">ExceptionCLRCatcherExecute – metoda</span><span class="sxs-lookup"><span data-stu-id="c2992-113">ExceptionCLRCatcherExecute Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherexecute-method.md)
