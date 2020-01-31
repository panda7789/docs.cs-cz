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
ms.openlocfilehash: 8a15843e9169442d89996375ee85f62b38f92e30
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864255"
---
# <a name="icorprofilerinfoendinprocdebugging-method"></a><span data-ttu-id="b9bea-102">ICorProfilerInfo::EndInprocDebugging – metoda</span><span class="sxs-lookup"><span data-stu-id="b9bea-102">ICorProfilerInfo::EndInprocDebugging Method</span></span>
<span data-ttu-id="b9bea-103">Ukončí relaci ladění v procesu.</span><span class="sxs-lookup"><span data-stu-id="b9bea-103">Shuts down an in-process debugging session.</span></span> <span data-ttu-id="b9bea-104">Tato metoda je zastaralá ve verzi .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="b9bea-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9bea-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b9bea-105">Syntax</span></span>  
  
```cpp  
HRESULT EndInprocDebugging(  
    [in]  DWORD dwProfilerContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9bea-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b9bea-106">Parameters</span></span>  
 `dwProfilerContext`  
 <span data-ttu-id="b9bea-107">pro Hodnota, která identifikuje relaci ladění.</span><span class="sxs-lookup"><span data-stu-id="b9bea-107">[in] A value that identifies the debugging session.</span></span> <span data-ttu-id="b9bea-108">Tato hodnota musí být stejná jako ta, která byla přijata v metodě [ICorProfilerInfo:: BeginInprocDebugging](icorprofilerinfo-begininprocdebugging-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b9bea-108">This value must be the same as that received in the [ICorProfilerInfo::BeginInprocDebugging](icorprofilerinfo-begininprocdebugging-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9bea-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b9bea-109">Remarks</span></span>  
 <span data-ttu-id="b9bea-110">Je nutné volat [ICorProfilerInfo:: BeginInprocDebugging](icorprofilerinfo-begininprocdebugging-method.md) a `EndInprocDebugging` v rámci stejné metody zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="b9bea-110">You must call [ICorProfilerInfo::BeginInprocDebugging](icorprofilerinfo-begininprocdebugging-method.md) and `EndInprocDebugging` within the same callback method.</span></span>  
  
 <span data-ttu-id="b9bea-111">Služba ladění CLR podporuje omezené vnitroprocesové ladění v .NET Framework verzích 1,0 a 1,1.</span><span class="sxs-lookup"><span data-stu-id="b9bea-111">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="b9bea-112">Ladění v rámci procesu povolilo profiler pro použití kontrolních částí rozhraní API pro ladění.</span><span class="sxs-lookup"><span data-stu-id="b9bea-112">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="b9bea-113">Z důvodu zpětné vazby od zákazníků jsme ale vnitroprocesové ladění odebrali z .NET Framework ve verzi 2,0 a nahradili sadu funkcí, která je v souladu s rozhraním API profilování.</span><span class="sxs-lookup"><span data-stu-id="b9bea-113">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9bea-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b9bea-114">Requirements</span></span>  
 <span data-ttu-id="b9bea-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9bea-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9bea-116">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b9bea-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b9bea-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b9bea-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9bea-118">**Verze .NET Framework:** 1,0</span><span class="sxs-lookup"><span data-stu-id="b9bea-118">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9bea-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b9bea-119">See also</span></span>

- [<span data-ttu-id="b9bea-120">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b9bea-120">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
