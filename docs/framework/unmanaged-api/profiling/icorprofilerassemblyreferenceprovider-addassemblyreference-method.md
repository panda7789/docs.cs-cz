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
ms.openlocfilehash: 2357e5348192db5d41adfe1176300359440aeee3
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866725"
---
# <a name="icorprofilerassemblyreferenceprovideraddassemblyreference-method"></a><span data-ttu-id="f77c6-102">ICorProfilerAssemblyReferenceProvider::AddAssemblyReference – metoda</span><span class="sxs-lookup"><span data-stu-id="f77c6-102">ICorProfilerAssemblyReferenceProvider::AddAssemblyReference Method</span></span>
<span data-ttu-id="f77c6-103">[Podporované v .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="f77c6-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="f77c6-104">Informuje modul CLR (Common Language Runtime) s odkazem na sestavení, který Profiler plánuje přidat do zpětného volání [ICorProfilerCallback:: ModuleLoadFinished –](icorprofilercallback-moduleloadfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f77c6-104">Informs the common language runtime (CLR) of an assembly reference that the profiler plans to add in the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f77c6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f77c6-105">Syntax</span></span>  
  
```cpp
HRESULT AddAssemblyReference(  
        const COR_PRF_ASSEMBLY_REFERENCE_INFO* pAssemblyRefInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f77c6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f77c6-106">Parameters</span></span>

- `pAssemblyRefInfo`

  <span data-ttu-id="f77c6-107">Ukazatel na [COR_PRF_ASSEMBLY_REFERENCE_INFO](cor-prf-assembly-reference-info-structure.md) strukturu, která poskytuje CLR s informacemi o odkazech na sestavení, které by měly vzít v úvahu při provádění procházení ukončení odkazu na sestavení.</span><span class="sxs-lookup"><span data-stu-id="f77c6-107">A pointer to a [COR_PRF_ASSEMBLY_REFERENCE_INFO](cor-prf-assembly-reference-info-structure.md) structure that provides the CLR with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="f77c6-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f77c6-108">Remarks</span></span>  
 <span data-ttu-id="f77c6-109">Profiler volá tuto metodu pro každé cílové sestavení, které plánuje odkaz ze sestavení zadaného v argumentu `wszAssemblyPath` volání [ICorProfilerCallback6:: GetAssemblyReferences –](icorprofilercallback6-getassemblyreferences-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f77c6-109">The profiler calls this method for each target assembly it plans to reference from the assembly specified in the `wszAssemblyPath` argument of the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="f77c6-110">Objekt rozhraní [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) je předán zpětnému volání [ICorProfilerCallback6:: GetAssemblyReferences –](icorprofilercallback6-getassemblyreferences-method.md) profileru spolu s cestou a názvem sestavení v argumentu `wszAssemblyPath`.</span><span class="sxs-lookup"><span data-stu-id="f77c6-110">The [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) interface object is passed to the profiler's [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback, along with the assembly path and name in the `wszAssemblyPath` argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f77c6-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f77c6-111">Requirements</span></span>  
 <span data-ttu-id="f77c6-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f77c6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f77c6-113">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f77c6-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f77c6-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f77c6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f77c6-115">**Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f77c6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f77c6-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f77c6-116">See also</span></span>

- [<span data-ttu-id="f77c6-117">ICorProfilerAssemblyReferenceProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f77c6-117">ICorProfilerAssemblyReferenceProvider Interface</span></span>](icorprofilerassemblyreferenceprovider-interface.md)
- [<span data-ttu-id="f77c6-118">GetAssemblyReferences – metoda</span><span class="sxs-lookup"><span data-stu-id="f77c6-118">GetAssemblyReferences Method</span></span>](icorprofilercallback6-getassemblyreferences-method.md)
- [<span data-ttu-id="f77c6-119">ModuleLoadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="f77c6-119">ModuleLoadFinished Method</span></span>](icorprofilercallback-moduleloadfinished-method.md)
