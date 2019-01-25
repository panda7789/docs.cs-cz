---
title: ICorProfilerInfo::EndInprocDebugging – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.EndInprocDebugging
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::EndInprocDebugging
helpviewer_keywords:
- ICorProfilerInfo::EndInprocDebugging method [.NET Framework profiling]
- EndInprocDebugging method [.NET Framework profiling]
ms.assetid: 35bc1188-9767-4141-8038-60ea015b99ac
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ea9acdb20392e1ded8695bc4d64ef87c6d0af9e2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54706664"
---
# <a name="icorprofilerinfoendinprocdebugging-method"></a><span data-ttu-id="f9a42-102">ICorProfilerInfo::EndInprocDebugging – metoda</span><span class="sxs-lookup"><span data-stu-id="f9a42-102">ICorProfilerInfo::EndInprocDebugging Method</span></span>
<span data-ttu-id="f9a42-103">Ukončí relaci ladění v procesu.</span><span class="sxs-lookup"><span data-stu-id="f9a42-103">Shuts down an in-process debugging session.</span></span> <span data-ttu-id="f9a42-104">Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="f9a42-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9a42-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f9a42-105">Syntax</span></span>  
  
```  
HRESULT EndInprocDebugging(  
    [in]  DWORD dwProfilerContext);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f9a42-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9a42-106">Parameters</span></span>  
 `dwProfilerContext`  
 <span data-ttu-id="f9a42-107">[in] Hodnota, která identifikuje relace ladění.</span><span class="sxs-lookup"><span data-stu-id="f9a42-107">[in] A value that identifies the debugging session.</span></span> <span data-ttu-id="f9a42-108">Tato hodnota musí být shodná se dostali [icorprofilerinfo::begininprocdebugging –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="f9a42-108">This value must be the same as that received in the [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9a42-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f9a42-109">Remarks</span></span>  
 <span data-ttu-id="f9a42-110">Je nutné volat [icorprofilerinfo::begininprocdebugging –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) a `EndInprocDebugging` v rámci stejné metody zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="f9a42-110">You must call [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) and `EndInprocDebugging` within the same callback method.</span></span>  
  
 <span data-ttu-id="f9a42-111">Ladění služby CLR nepodporuje omezené vnitroprocesové ladění v rozhraní .NET Framework verze 1.0 a 1.1.</span><span class="sxs-lookup"><span data-stu-id="f9a42-111">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="f9a42-112">Vnitroprocesové ladění povolit profiler použití kontroly části rozhraní API pro ladění.</span><span class="sxs-lookup"><span data-stu-id="f9a42-112">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="f9a42-113">Ale z důvodu zpětné vazby od zákazníků, vnitroprocesové ladění má byla odebrána z rozhraní .NET Framework verze 2.0 a jsme nahradili sadou funkcí, které jsou více tato rozhraní API profilování.</span><span class="sxs-lookup"><span data-stu-id="f9a42-113">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9a42-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f9a42-114">Requirements</span></span>  
 <span data-ttu-id="f9a42-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9a42-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9a42-116">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f9a42-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f9a42-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f9a42-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9a42-118">**Verze rozhraní .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="f9a42-118">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9a42-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f9a42-119">See also</span></span>
- [<span data-ttu-id="f9a42-120">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f9a42-120">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
