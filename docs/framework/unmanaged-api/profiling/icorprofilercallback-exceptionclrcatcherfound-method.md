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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 683cec06cd4c2fdef310126adc2921c858ca5687
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776025"
---
# <a name="icorprofilercallbackexceptionclrcatcherfound-method"></a><span data-ttu-id="a1929-102">ICorProfilerCallback::ExceptionCLRCatcherFound – metoda</span><span class="sxs-lookup"><span data-stu-id="a1929-102">ICorProfilerCallback::ExceptionCLRCatcherFound Method</span></span>
<span data-ttu-id="a1929-103">Voláno, když `catch` block pro výjimku se nachází uvnitř common language runtime (CLR), samotného.</span><span class="sxs-lookup"><span data-stu-id="a1929-103">Called when a `catch` block for an exception is found inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="a1929-104">Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="a1929-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1929-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1929-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCLRCatcherFound();  
```  
  
## <a name="requirements"></a><span data-ttu-id="a1929-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a1929-106">Requirements</span></span>  
 <span data-ttu-id="a1929-107">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1929-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1929-108">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a1929-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a1929-109">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1929-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1929-110">**Verze rozhraní .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="a1929-110">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1929-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a1929-111">See also</span></span>

- [<span data-ttu-id="a1929-112">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a1929-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="a1929-113">ExceptionCLRCatcherExecute – metoda</span><span class="sxs-lookup"><span data-stu-id="a1929-113">ExceptionCLRCatcherExecute Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherexecute-method.md)
