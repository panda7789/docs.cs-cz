---
title: Struktura COR_PRF_ASSEMBLY_REFERENCE_INFO
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
ms.assetid: c8c1d916-8d1a-4f82-8128-9fd3732383fc
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4b5889f8e0b0dc8faab76f637e2fcf03853709bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corprfassemblyreferenceinfo-structure"></a><span data-ttu-id="e6f2d-102">Struktura COR_PRF_ASSEMBLY_REFERENCE_INFO</span><span class="sxs-lookup"><span data-stu-id="e6f2d-102">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>
<span data-ttu-id="e6f2d-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="e6f2d-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="e6f2d-104">Poskytuje modul common language runtime s informacemi o odkaz na sestavení, který ho měli zvážit při procházení uzavření odkaz na sestavení.</span><span class="sxs-lookup"><span data-stu-id="e6f2d-104">Provides the common language runtime with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6f2d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6f2d-105">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_ASSEMBLY_REFERENCE_INFO {  
    void* pbPublicKeyOrToken;  
    ULONG cbPublicKeyOrToken;  
    LPCWSTR szName;  
    ASSEMBLYMETADATA* pMetaData;  
    void* pbHashValue;  
    ULONG cbHashValue;  
    DWORD dwAssemblyRefFlags;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="e6f2d-106">Členové</span><span class="sxs-lookup"><span data-stu-id="e6f2d-106">Members</span></span>  
  
|<span data-ttu-id="e6f2d-107">Člen</span><span class="sxs-lookup"><span data-stu-id="e6f2d-107">Member</span></span>|<span data-ttu-id="e6f2d-108">Popis</span><span class="sxs-lookup"><span data-stu-id="e6f2d-108">Description</span></span>|  
|------------|-----------------|  
|`pbPublicKeyOrToken`|<span data-ttu-id="e6f2d-109">Ukazatel na veřejné klíče nebo s tokenem sestavení.</span><span class="sxs-lookup"><span data-stu-id="e6f2d-109">A pointer to the public key or token of the assembly.</span></span>|  
|`cbPublicKeyOrToken`|<span data-ttu-id="e6f2d-110">Počet bajtů v veřejný klíč nebo na tokenu.</span><span class="sxs-lookup"><span data-stu-id="e6f2d-110">The number of bytes in the public key or token.</span></span>|  
|`szName`|<span data-ttu-id="e6f2d-111">Název sestavení, které se odkazuje.</span><span class="sxs-lookup"><span data-stu-id="e6f2d-111">The name of the assembly that is referenced.</span></span>|  
|`pMetaData`|<span data-ttu-id="e6f2d-112">Ukazatel na metadata sestavení.</span><span class="sxs-lookup"><span data-stu-id="e6f2d-112">A pointer to the assembly's metadata.</span></span>|  
|`pbHashValue`|<span data-ttu-id="e6f2d-113">Ukazatel na binární rozsáhlý objekt hash (binární rozsáhlý OBJEKT).</span><span class="sxs-lookup"><span data-stu-id="e6f2d-113">A pointer to a hash binary large object (BLOB).</span></span>|  
|`cbHashValue`|<span data-ttu-id="e6f2d-114">Počet bajtů hash objektů BLOB.</span><span class="sxs-lookup"><span data-stu-id="e6f2d-114">The number of bytes in the hash BLOB.</span></span>|  
|`dwAssemblyRefFlags`|<span data-ttu-id="e6f2d-115">Příznaky sestavení.</span><span class="sxs-lookup"><span data-stu-id="e6f2d-115">The assembly's flags.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6f2d-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e6f2d-116">Remarks</span></span>  
 <span data-ttu-id="e6f2d-117">`COR_PRF_EX_CLAUSE_INFO` Struktura je naplněn profileru při deklaruje odkazy na další sestavení, které modul common language runtime měli zvážit při procházení uzavření odkaz na sestavení.</span><span class="sxs-lookup"><span data-stu-id="e6f2d-117">The `COR_PRF_EX_CLAUSE_INFO` structure is populated by the profiler when it declares additional assembly references that the common language runtime should consider when performing an assembly reference closure walk.</span></span>  
  
 <span data-ttu-id="e6f2d-118">Pokud profileru zaregistruje [icorprofilercallback6::getassemblyreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) metoda zpětného volání, modul runtime předá cestu a název sestavení, která má být načten, spolu s odkazy [ ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) rozhraní objektu do dané metody.</span><span class="sxs-lookup"><span data-stu-id="e6f2d-118">If the profiler registers for the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback method, the runtime passes the path and name of the assembly to be loaded, along with a pointer to an [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) interface object to that method.</span></span> <span data-ttu-id="e6f2d-119">Potom můžete volat profileru [icorprofilerassemblyreferenceprovider::addassemblyreference –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) metoda s `COR_PRF_ASSEMBLY_REFERENCE_INFO` objekt pro každý cíl sestavení se plánuje odkazovat z sestavení zadané v [ Icorprofilercallback6::getassemblyreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="e6f2d-119">The profiler can then call the [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) method with a `COR_PRF_ASSEMBLY_REFERENCE_INFO` object for each target assembly it plans to reference from the assembly specified in the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6f2d-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e6f2d-120">Requirements</span></span>  
 <span data-ttu-id="e6f2d-121">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6f2d-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6f2d-122">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e6f2d-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e6f2d-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e6f2d-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e6f2d-124">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6f2d-124">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6f2d-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="e6f2d-125">See Also</span></span>  
 [<span data-ttu-id="e6f2d-126">Struktury pro profilaci</span><span class="sxs-lookup"><span data-stu-id="e6f2d-126">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)  
 [<span data-ttu-id="e6f2d-127">GetAssemblyReferences – metoda</span><span class="sxs-lookup"><span data-stu-id="e6f2d-127">GetAssemblyReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)  
 [<span data-ttu-id="e6f2d-128">AddAssemblyReference – metoda</span><span class="sxs-lookup"><span data-stu-id="e6f2d-128">AddAssemblyReference Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)
