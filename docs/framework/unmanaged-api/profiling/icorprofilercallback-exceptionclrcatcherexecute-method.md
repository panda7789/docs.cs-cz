---
title: "ICorProfilerCallback::ExceptionCLRCatcherExecute – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionCLRCatcherExecute
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionCLRCatcherExecute
helpviewer_keywords:
- ExceptionCLRCatcherExecute method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionCLRCatcherExecute method [.NET Framework profiling]
ms.assetid: aaac8f98-5cf4-42c7-b04b-556cce367e36
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b63f428cd75ed98d30e4b6ecca69dbe3b5b5656d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackexceptionclrcatcherexecute-method"></a><span data-ttu-id="aa930-102">ICorProfilerCallback::ExceptionCLRCatcherExecute – metoda</span><span class="sxs-lookup"><span data-stu-id="aa930-102">ICorProfilerCallback::ExceptionCLRCatcherExecute Method</span></span>
<span data-ttu-id="aa930-103">Voláno, když `catch` blokovat pro výjimku je spustit v rámci modul CLR (CLR) sám sebe.</span><span class="sxs-lookup"><span data-stu-id="aa930-103">Called when a `catch` block for an exception is executed inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="aa930-104">Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="aa930-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa930-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aa930-105">Syntax</span></span>  
  
```  
HRESULT ExceptionCLRCatcherExecute();  
```  
  
## <a name="requirements"></a><span data-ttu-id="aa930-106">Požadavky</span><span class="sxs-lookup"><span data-stu-id="aa930-106">Requirements</span></span>  
 <span data-ttu-id="aa930-107">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa930-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa930-108">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="aa930-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="aa930-109">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aa930-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aa930-110">**Verze rozhraní .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="aa930-110">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa930-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="aa930-111">See Also</span></span>  
 [<span data-ttu-id="aa930-112">Icorprofilercallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="aa930-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="aa930-113">Exceptionclrcatcherfound – metoda</span><span class="sxs-lookup"><span data-stu-id="aa930-113">ExceptionCLRCatcherFound Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherfound-method.md)
