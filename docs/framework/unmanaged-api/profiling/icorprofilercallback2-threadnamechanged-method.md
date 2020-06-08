---
title: ICorProfilerCallback2::ThreadNameChanged – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.ThreadNameChanged
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::ThreadNameChanged
helpviewer_keywords:
- ThreadNameChanged method [.NET Framework profiling]
- ICorProfilerCallback2::ThreadNameChanged method [.NET Framework profiling]
ms.assetid: c8bbd76d-a9ff-44f2-87a6-be052819da36
topic_type:
- apiref
ms.openlocfilehash: 3eb108ed20d0fd1287cb82eb4d552206aeae15d4
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499724"
---
# <a name="icorprofilercallback2threadnamechanged-method"></a><span data-ttu-id="dbf57-102">ICorProfilerCallback2::ThreadNameChanged – metoda</span><span class="sxs-lookup"><span data-stu-id="dbf57-102">ICorProfilerCallback2::ThreadNameChanged Method</span></span>
<span data-ttu-id="dbf57-103">Upozorní profiler kódu, že se změnil název vlákna.</span><span class="sxs-lookup"><span data-stu-id="dbf57-103">Notifies the code profiler that the name of a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbf57-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dbf57-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadNameChanged(  
    [in] ThreadID threadId,  
    [in] ULONG cchName,  
    [in] WCHAR name[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dbf57-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dbf57-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="dbf57-106">pro ID vlákna</span><span class="sxs-lookup"><span data-stu-id="dbf57-106">[in] The ID of the thread.</span></span>  
  
 `cchName`  
 <span data-ttu-id="dbf57-107">pro Délka nového názvu vlákna.</span><span class="sxs-lookup"><span data-stu-id="dbf57-107">[in] The length of the new name of the thread.</span></span>  
  
 `name`  
 <span data-ttu-id="dbf57-108">pro Nový název vlákna.</span><span class="sxs-lookup"><span data-stu-id="dbf57-108">[in] The new name of the thread.</span></span> <span data-ttu-id="dbf57-109">Název není zakončený hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="dbf57-109">The name is not null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbf57-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dbf57-110">Requirements</span></span>  
 <span data-ttu-id="dbf57-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbf57-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbf57-112">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="dbf57-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dbf57-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="dbf57-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dbf57-114">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbf57-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbf57-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dbf57-115">See also</span></span>

- [<span data-ttu-id="dbf57-116">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dbf57-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="dbf57-117">ICorProfilerCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dbf57-117">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
