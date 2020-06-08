---
title: ICorProfilerAssemblyReferenceProvider::AddAssemblyReference – metoda
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerAssemblyReferenceProvider.AddAssemblyReference
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 3d5af8e7-c337-48f4-9fa6-97c83878b9b1
topic_type:
- apiref
ms.openlocfilehash: 6d732c6c2871cc5e042b8504db26aabb19963f8c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500504"
---
# <a name="icorprofilerassemblyreferenceprovideraddassemblyreference-method"></a><span data-ttu-id="98625-102">ICorProfilerAssemblyReferenceProvider::AddAssemblyReference – metoda</span><span class="sxs-lookup"><span data-stu-id="98625-102">ICorProfilerAssemblyReferenceProvider::AddAssemblyReference Method</span></span>
<span data-ttu-id="98625-103">[Podporované v .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="98625-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="98625-104">Informuje modul CLR (Common Language Runtime) s odkazem na sestavení, který Profiler plánuje přidat do zpětného volání [ICorProfilerCallback:: ModuleLoadFinished –](icorprofilercallback-moduleloadfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="98625-104">Informs the common language runtime (CLR) of an assembly reference that the profiler plans to add in the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98625-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="98625-105">Syntax</span></span>  
  
```cpp
HRESULT AddAssemblyReference(  
        const COR_PRF_ASSEMBLY_REFERENCE_INFO* pAssemblyRefInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98625-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="98625-106">Parameters</span></span>

- `pAssemblyRefInfo`

  <span data-ttu-id="98625-107">Ukazatel na [COR_PRF_ASSEMBLY_REFERENCE_INFO](cor-prf-assembly-reference-info-structure.md) strukturu, která poskytuje CLR s informacemi o odkazech na sestavení, které by měly vzít v úvahu při provádění procházení ukončení odkazu na sestavení.</span><span class="sxs-lookup"><span data-stu-id="98625-107">A pointer to a [COR_PRF_ASSEMBLY_REFERENCE_INFO](cor-prf-assembly-reference-info-structure.md) structure that provides the CLR with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="98625-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="98625-108">Remarks</span></span>  
 <span data-ttu-id="98625-109">Profiler volá tuto metodu pro každé cílové sestavení, které plánuje odkaz ze sestavení zadaného v `wszAssemblyPath` argumentu zpětného volání [ICorProfilerCallback6:: GetAssemblyReferences –](icorprofilercallback6-getassemblyreferences-method.md) .</span><span class="sxs-lookup"><span data-stu-id="98625-109">The profiler calls this method for each target assembly it plans to reference from the assembly specified in the `wszAssemblyPath` argument of the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="98625-110">Objekt rozhraní [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) je předán zpětnému volání [ICorProfilerCallback6:: GetAssemblyReferences –](icorprofilercallback6-getassemblyreferences-method.md) profileru spolu s cestou k sestavení a názvem v `wszAssemblyPath` argumentu.</span><span class="sxs-lookup"><span data-stu-id="98625-110">The [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) interface object is passed to the profiler's [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback, along with the assembly path and name in the `wszAssemblyPath` argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98625-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="98625-111">Requirements</span></span>  
 <span data-ttu-id="98625-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98625-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98625-113">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="98625-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="98625-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="98625-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98625-115">**Verze .NET Framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98625-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98625-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="98625-116">See also</span></span>

- [<span data-ttu-id="98625-117">Rozhraní ICorProfilerAssemblyReferenceProvider</span><span class="sxs-lookup"><span data-stu-id="98625-117">ICorProfilerAssemblyReferenceProvider Interface</span></span>](icorprofilerassemblyreferenceprovider-interface.md)
- [<span data-ttu-id="98625-118">Metoda GetAssemblyReferences</span><span class="sxs-lookup"><span data-stu-id="98625-118">GetAssemblyReferences Method</span></span>](icorprofilercallback6-getassemblyreferences-method.md)
- [<span data-ttu-id="98625-119">ModuleLoadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="98625-119">ModuleLoadFinished Method</span></span>](icorprofilercallback-moduleloadfinished-method.md)
