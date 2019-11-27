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
ms.openlocfilehash: 09b1b81bde486db67acede99e0d67ff85cb01bae
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447765"
---
# <a name="icorprofilerinfoendinprocdebugging-method"></a><span data-ttu-id="dac4c-102">ICorProfilerInfo::EndInprocDebugging – metoda</span><span class="sxs-lookup"><span data-stu-id="dac4c-102">ICorProfilerInfo::EndInprocDebugging Method</span></span>
<span data-ttu-id="dac4c-103">Ukončí relaci ladění v procesu.</span><span class="sxs-lookup"><span data-stu-id="dac4c-103">Shuts down an in-process debugging session.</span></span> <span data-ttu-id="dac4c-104">Tato metoda je zastaralá ve verzi .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="dac4c-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dac4c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dac4c-105">Syntax</span></span>  
  
```cpp  
HRESULT EndInprocDebugging(  
    [in]  DWORD dwProfilerContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dac4c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="dac4c-106">Parameters</span></span>  
 `dwProfilerContext`  
 <span data-ttu-id="dac4c-107">pro Hodnota, která identifikuje relaci ladění.</span><span class="sxs-lookup"><span data-stu-id="dac4c-107">[in] A value that identifies the debugging session.</span></span> <span data-ttu-id="dac4c-108">Tato hodnota musí být stejná jako ta, která byla přijata v metodě [ICorProfilerInfo:: BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) .</span><span class="sxs-lookup"><span data-stu-id="dac4c-108">This value must be the same as that received in the [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dac4c-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dac4c-109">Remarks</span></span>  
 <span data-ttu-id="dac4c-110">Je nutné volat [ICorProfilerInfo:: BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) a `EndInprocDebugging` v rámci stejné metody zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="dac4c-110">You must call [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) and `EndInprocDebugging` within the same callback method.</span></span>  
  
 <span data-ttu-id="dac4c-111">Služba ladění CLR podporuje omezené vnitroprocesové ladění v .NET Framework verzích 1,0 a 1,1.</span><span class="sxs-lookup"><span data-stu-id="dac4c-111">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="dac4c-112">Ladění v rámci procesu povolilo profiler pro použití kontrolních částí rozhraní API pro ladění.</span><span class="sxs-lookup"><span data-stu-id="dac4c-112">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="dac4c-113">Z důvodu zpětné vazby od zákazníků jsme ale vnitroprocesové ladění odebrali z .NET Framework ve verzi 2,0 a nahradili sadu funkcí, která je v souladu s rozhraním API profilování.</span><span class="sxs-lookup"><span data-stu-id="dac4c-113">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dac4c-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dac4c-114">Requirements</span></span>  
 <span data-ttu-id="dac4c-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dac4c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dac4c-116">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="dac4c-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dac4c-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="dac4c-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dac4c-118">**Verze .NET Framework:** 1,0</span><span class="sxs-lookup"><span data-stu-id="dac4c-118">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dac4c-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dac4c-119">See also</span></span>

- [<span data-ttu-id="dac4c-120">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dac4c-120">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
