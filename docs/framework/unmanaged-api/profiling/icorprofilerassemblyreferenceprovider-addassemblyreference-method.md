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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 09ce4f3a293e7870ddadf4ad6ee2c15de10f4594
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61598530"
---
# <a name="icorprofilerassemblyreferenceprovideraddassemblyreference-method"></a><span data-ttu-id="0c9b0-102">ICorProfilerAssemblyReferenceProvider::AddAssemblyReference – metoda</span><span class="sxs-lookup"><span data-stu-id="0c9b0-102">ICorProfilerAssemblyReferenceProvider::AddAssemblyReference Method</span></span>
<span data-ttu-id="0c9b0-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="0c9b0-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="0c9b0-104">Informuje o odkaz na sestavení, která profiler má v plánu přidat common language runtime (CLR) [icorprofilercallback::moduleloadfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="0c9b0-104">Informs the common language runtime (CLR) of an assembly reference that the profiler plans to add in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c9b0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0c9b0-105">Syntax</span></span>  
  
```cpp
HRESULT AddAssemblyReference(  
        const COR_PRF_ASSEMBLY_REFERENCE_INFO* pAssemblyRefInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c9b0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="0c9b0-106">Parameters</span></span>  
 <span data-ttu-id="0c9b0-107">pAssemblyRefInfo</span><span class="sxs-lookup"><span data-stu-id="0c9b0-107">pAssemblyRefInfo</span></span>  
 <span data-ttu-id="0c9b0-108">Ukazatel [COR_PRF_ASSEMBLY_REFERENCE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md) struktura, která poskytuje informace o odkaz na sestavení, byste měli zvážit při procházení uzavření odkaz sestavení CLR.</span><span class="sxs-lookup"><span data-stu-id="0c9b0-108">A pointer to a [COR_PRF_ASSEMBLY_REFERENCE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md) structure that provides the CLR with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c9b0-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0c9b0-109">Remarks</span></span>  
 <span data-ttu-id="0c9b0-110">Profiler volá tuto metodu pro každý cíl sestavení má odkazovat ze sestavení zadaná v `wszAssemblyPath` argument [icorprofilercallback6::getassemblyreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="0c9b0-110">The profiler calls this method for each target assembly it plans to reference from the assembly specified in the `wszAssemblyPath` argument of the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="0c9b0-111">[ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) rozhraní objekt je předán profileru [icorprofilercallback6::getassemblyreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) zpětné volání, cesta k sestavení a název `wszAssemblyPath` argument.</span><span class="sxs-lookup"><span data-stu-id="0c9b0-111">The [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) interface object is passed to the profiler's [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback, along with the assembly path and name in the `wszAssemblyPath` argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c9b0-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0c9b0-112">Requirements</span></span>  
 <span data-ttu-id="0c9b0-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c9b0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c9b0-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0c9b0-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0c9b0-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0c9b0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c9b0-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c9b0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c9b0-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0c9b0-117">See also</span></span>

- [<span data-ttu-id="0c9b0-118">ICorProfilerAssemblyReferenceProvider – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0c9b0-118">ICorProfilerAssemblyReferenceProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)
- [<span data-ttu-id="0c9b0-119">GetAssemblyReferences – metoda</span><span class="sxs-lookup"><span data-stu-id="0c9b0-119">GetAssemblyReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)
- [<span data-ttu-id="0c9b0-120">ModuleLoadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="0c9b0-120">ModuleLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
