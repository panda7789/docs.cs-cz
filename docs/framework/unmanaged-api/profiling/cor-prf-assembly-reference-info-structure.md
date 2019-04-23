---
title: Struktura COR_PRF_ASSEMBLY_REFERENCE_INFO
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: c8c1d916-8d1a-4f82-8128-9fd3732383fc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 99fa1cc05ee583cf1bd59235fcd9821d1c92d21f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59101429"
---
# <a name="corprfassemblyreferenceinfo-structure"></a><span data-ttu-id="4ef73-102">Struktura COR_PRF_ASSEMBLY_REFERENCE_INFO</span><span class="sxs-lookup"><span data-stu-id="4ef73-102">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>
<span data-ttu-id="4ef73-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="4ef73-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="4ef73-104">Modul common language runtime poskytuje informace o odkaz na sestavení, byste měli zvážit při procházení uzavření odkaz sestavení.</span><span class="sxs-lookup"><span data-stu-id="4ef73-104">Provides the common language runtime with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ef73-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4ef73-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="4ef73-106">Členové</span><span class="sxs-lookup"><span data-stu-id="4ef73-106">Members</span></span>  
  
|<span data-ttu-id="4ef73-107">Člen</span><span class="sxs-lookup"><span data-stu-id="4ef73-107">Member</span></span>|<span data-ttu-id="4ef73-108">Popis</span><span class="sxs-lookup"><span data-stu-id="4ef73-108">Description</span></span>|  
|------------|-----------------|  
|`pbPublicKeyOrToken`|<span data-ttu-id="4ef73-109">Ukazatel na veřejný klíč nebo token sestavení.</span><span class="sxs-lookup"><span data-stu-id="4ef73-109">A pointer to the public key or token of the assembly.</span></span>|  
|`cbPublicKeyOrToken`|<span data-ttu-id="4ef73-110">Počet bajtů v veřejný klíč nebo token.</span><span class="sxs-lookup"><span data-stu-id="4ef73-110">The number of bytes in the public key or token.</span></span>|  
|`szName`|<span data-ttu-id="4ef73-111">Název sestavení, na který odkazuje.</span><span class="sxs-lookup"><span data-stu-id="4ef73-111">The name of the assembly that is referenced.</span></span>|  
|`pMetaData`|<span data-ttu-id="4ef73-112">Ukazatel na metadata sestavení.</span><span class="sxs-lookup"><span data-stu-id="4ef73-112">A pointer to the assembly's metadata.</span></span>|  
|`pbHashValue`|<span data-ttu-id="4ef73-113">Ukazatel na binární rozsáhlý objekt hash (objektů BLOB).</span><span class="sxs-lookup"><span data-stu-id="4ef73-113">A pointer to a hash binary large object (BLOB).</span></span>|  
|`cbHashValue`|<span data-ttu-id="4ef73-114">Počet bajtů v objekt BLOB algoritmu hash.</span><span class="sxs-lookup"><span data-stu-id="4ef73-114">The number of bytes in the hash BLOB.</span></span>|  
|`dwAssemblyRefFlags`|<span data-ttu-id="4ef73-115">Příznaky sestavení.</span><span class="sxs-lookup"><span data-stu-id="4ef73-115">The assembly's flags.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ef73-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4ef73-116">Remarks</span></span>  
 <span data-ttu-id="4ef73-117">`COR_PRF_EX_CLAUSE_INFO` Struktura je vyplněn profiler při deklaruje odkazy na další sestavení, které modul common language runtime měli zvážit při procházení uzavření odkaz sestavení.</span><span class="sxs-lookup"><span data-stu-id="4ef73-117">The `COR_PRF_EX_CLAUSE_INFO` structure is populated by the profiler when it declares additional assembly references that the common language runtime should consider when performing an assembly reference closure walk.</span></span>  
  
 <span data-ttu-id="4ef73-118">Pokud profiler zaregistruje [icorprofilercallback6::getassemblyreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) metoda zpětného volání, modul runtime předá cestu a název sestavení, který se má načíst, spolu s ukazatelem na [ ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) objektu rozhraní k této metodě.</span><span class="sxs-lookup"><span data-stu-id="4ef73-118">If the profiler registers for the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback method, the runtime passes the path and name of the assembly to be loaded, along with a pointer to an [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) interface object to that method.</span></span> <span data-ttu-id="4ef73-119">Profiler pak volat [icorprofilerassemblyreferenceprovider::addassemblyreference –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) metody `COR_PRF_ASSEMBLY_REFERENCE_INFO` objekt pro každý cíl sestavení má odkazovat ze sestavení zadaná v [ Icorprofilercallback6::getassemblyreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="4ef73-119">The profiler can then call the [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) method with a `COR_PRF_ASSEMBLY_REFERENCE_INFO` object for each target assembly it plans to reference from the assembly specified in the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ef73-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4ef73-120">Requirements</span></span>  
 <span data-ttu-id="4ef73-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ef73-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ef73-122">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4ef73-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4ef73-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4ef73-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4ef73-124">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ef73-124">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ef73-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4ef73-125">See also</span></span>

- [<span data-ttu-id="4ef73-126">Struktury pro profilaci</span><span class="sxs-lookup"><span data-stu-id="4ef73-126">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
- [<span data-ttu-id="4ef73-127">GetAssemblyReferences – metoda</span><span class="sxs-lookup"><span data-stu-id="4ef73-127">GetAssemblyReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)
- [<span data-ttu-id="4ef73-128">AddAssemblyReference – metoda</span><span class="sxs-lookup"><span data-stu-id="4ef73-128">AddAssemblyReference Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)
