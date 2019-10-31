---
title: Struktura COR_PRF_ASSEMBLY_REFERENCE_INFO
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: c8c1d916-8d1a-4f82-8128-9fd3732383fc
ms.openlocfilehash: ac7ddeed5694ad0ae6ef3d4a11fcb1fb23755b8e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123218"
---
# <a name="cor_prf_assembly_reference_info-structure"></a><span data-ttu-id="fa001-102">Struktura COR_PRF_ASSEMBLY_REFERENCE_INFO</span><span class="sxs-lookup"><span data-stu-id="fa001-102">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>
<span data-ttu-id="fa001-103">[Podporované v .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="fa001-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="fa001-104">Poskytuje modul CLR (Common Language Runtime) informace o odkazech na sestavení, které by měly být zváženy při provádění procházení ukončení odkazu na sestavení.</span><span class="sxs-lookup"><span data-stu-id="fa001-104">Provides the common language runtime with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa001-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fa001-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="fa001-106">Členové</span><span class="sxs-lookup"><span data-stu-id="fa001-106">Members</span></span>  
  
|<span data-ttu-id="fa001-107">Člen</span><span class="sxs-lookup"><span data-stu-id="fa001-107">Member</span></span>|<span data-ttu-id="fa001-108">Popis</span><span class="sxs-lookup"><span data-stu-id="fa001-108">Description</span></span>|  
|------------|-----------------|  
|`pbPublicKeyOrToken`|<span data-ttu-id="fa001-109">Ukazatel na veřejný klíč nebo token sestavení.</span><span class="sxs-lookup"><span data-stu-id="fa001-109">A pointer to the public key or token of the assembly.</span></span>|  
|`cbPublicKeyOrToken`|<span data-ttu-id="fa001-110">Počet bajtů ve veřejném klíči nebo tokenu.</span><span class="sxs-lookup"><span data-stu-id="fa001-110">The number of bytes in the public key or token.</span></span>|  
|`szName`|<span data-ttu-id="fa001-111">Název sestavení, na které se odkazuje.</span><span class="sxs-lookup"><span data-stu-id="fa001-111">The name of the assembly that is referenced.</span></span>|  
|`pMetaData`|<span data-ttu-id="fa001-112">Ukazatel na metadata sestavení.</span><span class="sxs-lookup"><span data-stu-id="fa001-112">A pointer to the assembly's metadata.</span></span>|  
|`pbHashValue`|<span data-ttu-id="fa001-113">Ukazatel na binární rozsáhlý objekt hash (BLOB).</span><span class="sxs-lookup"><span data-stu-id="fa001-113">A pointer to a hash binary large object (BLOB).</span></span>|  
|`cbHashValue`|<span data-ttu-id="fa001-114">Počet bajtů v objektu BLOB hash.</span><span class="sxs-lookup"><span data-stu-id="fa001-114">The number of bytes in the hash BLOB.</span></span>|  
|`dwAssemblyRefFlags`|<span data-ttu-id="fa001-115">Příznaky sestavení.</span><span class="sxs-lookup"><span data-stu-id="fa001-115">The assembly's flags.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa001-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fa001-116">Remarks</span></span>  
 <span data-ttu-id="fa001-117">Struktura `COR_PRF_EX_CLAUSE_INFO` je vyplněna profilerem při deklaraci dalších odkazů na sestavení, které by měl zvážit modul common language runtime, když je prováděno procházení uzavření odkazu na sestavení.</span><span class="sxs-lookup"><span data-stu-id="fa001-117">The `COR_PRF_EX_CLAUSE_INFO` structure is populated by the profiler when it declares additional assembly references that the common language runtime should consider when performing an assembly reference closure walk.</span></span>  
  
 <span data-ttu-id="fa001-118">Pokud profiler registruje pro metodu zpětného volání [ICorProfilerCallback6:: GetAssemblyReferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) , modul runtime předá cestu a název sestavení, které se má načíst, spolu s ukazatelem na [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) objekt rozhraní k této metodě.</span><span class="sxs-lookup"><span data-stu-id="fa001-118">If the profiler registers for the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback method, the runtime passes the path and name of the assembly to be loaded, along with a pointer to an [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) interface object to that method.</span></span> <span data-ttu-id="fa001-119">Profiler pak může zavolat metodu [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) s objektem `COR_PRF_ASSEMBLY_REFERENCE_INFO` pro každé cílové sestavení, které plánuje odkazovat ze sestavení určeného v [ICorProfilerCallback6:: GetAssemblyReferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="fa001-119">The profiler can then call the [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) method with a `COR_PRF_ASSEMBLY_REFERENCE_INFO` object for each target assembly it plans to reference from the assembly specified in the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa001-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fa001-120">Requirements</span></span>  
 <span data-ttu-id="fa001-121">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa001-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa001-122">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="fa001-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fa001-123">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="fa001-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa001-124">**Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa001-124">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa001-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fa001-125">See also</span></span>

- [<span data-ttu-id="fa001-126">Struktury pro profilaci</span><span class="sxs-lookup"><span data-stu-id="fa001-126">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
- [<span data-ttu-id="fa001-127">GetAssemblyReferences – metoda</span><span class="sxs-lookup"><span data-stu-id="fa001-127">GetAssemblyReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)
- [<span data-ttu-id="fa001-128">AddAssemblyReference – metoda</span><span class="sxs-lookup"><span data-stu-id="fa001-128">AddAssemblyReference Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)
