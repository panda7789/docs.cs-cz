---
title: Struktura COR_PRF_ASSEMBLY_REFERENCE_INFO
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: c8c1d916-8d1a-4f82-8128-9fd3732383fc
ms.openlocfilehash: 861b31e5621e9a7b40403d249c6a5c8c4ac25db8
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501037"
---
# <a name="cor_prf_assembly_reference_info-structure"></a><span data-ttu-id="ed918-102">Struktura COR_PRF_ASSEMBLY_REFERENCE_INFO</span><span class="sxs-lookup"><span data-stu-id="ed918-102">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>
<span data-ttu-id="ed918-103">[Podporované v .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="ed918-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="ed918-104">Poskytuje modul CLR (Common Language Runtime) informace o odkazech na sestavení, které by měly být zváženy při provádění procházení ukončení odkazu na sestavení.</span><span class="sxs-lookup"><span data-stu-id="ed918-104">Provides the common language runtime with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed918-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ed918-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="ed918-106">Členové</span><span class="sxs-lookup"><span data-stu-id="ed918-106">Members</span></span>  
  
|<span data-ttu-id="ed918-107">Člen</span><span class="sxs-lookup"><span data-stu-id="ed918-107">Member</span></span>|<span data-ttu-id="ed918-108">Description</span><span class="sxs-lookup"><span data-stu-id="ed918-108">Description</span></span>|  
|------------|-----------------|  
|`pbPublicKeyOrToken`|<span data-ttu-id="ed918-109">Ukazatel na veřejný klíč nebo token sestavení.</span><span class="sxs-lookup"><span data-stu-id="ed918-109">A pointer to the public key or token of the assembly.</span></span>|  
|`cbPublicKeyOrToken`|<span data-ttu-id="ed918-110">Počet bajtů ve veřejném klíči nebo tokenu.</span><span class="sxs-lookup"><span data-stu-id="ed918-110">The number of bytes in the public key or token.</span></span>|  
|`szName`|<span data-ttu-id="ed918-111">Název sestavení, na které se odkazuje.</span><span class="sxs-lookup"><span data-stu-id="ed918-111">The name of the assembly that is referenced.</span></span>|  
|`pMetaData`|<span data-ttu-id="ed918-112">Ukazatel na metadata sestavení.</span><span class="sxs-lookup"><span data-stu-id="ed918-112">A pointer to the assembly's metadata.</span></span>|  
|`pbHashValue`|<span data-ttu-id="ed918-113">Ukazatel na binární rozsáhlý objekt hash (BLOB).</span><span class="sxs-lookup"><span data-stu-id="ed918-113">A pointer to a hash binary large object (BLOB).</span></span>|  
|`cbHashValue`|<span data-ttu-id="ed918-114">Počet bajtů v objektu BLOB hash.</span><span class="sxs-lookup"><span data-stu-id="ed918-114">The number of bytes in the hash BLOB.</span></span>|  
|`dwAssemblyRefFlags`|<span data-ttu-id="ed918-115">Příznaky sestavení.</span><span class="sxs-lookup"><span data-stu-id="ed918-115">The assembly's flags.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ed918-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ed918-116">Remarks</span></span>  
 <span data-ttu-id="ed918-117">`COR_PRF_EX_CLAUSE_INFO`Struktura je vyplněna profilerem při deklaraci dalších odkazů na sestavení, které by měl při provádění procházení uzavření odkazu na sestavení zvážit modul common language runtime.</span><span class="sxs-lookup"><span data-stu-id="ed918-117">The `COR_PRF_EX_CLAUSE_INFO` structure is populated by the profiler when it declares additional assembly references that the common language runtime should consider when performing an assembly reference closure walk.</span></span>  
  
 <span data-ttu-id="ed918-118">Pokud profiler registruje pro metodu zpětného volání [ICorProfilerCallback6:: GetAssemblyReferences –](icorprofilercallback6-getassemblyreferences-method.md) , modul runtime předá cestu a název sestavení, které mají být načteny, spolu s ukazatelem na objekt rozhraní [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) k této metodě.</span><span class="sxs-lookup"><span data-stu-id="ed918-118">If the profiler registers for the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback method, the runtime passes the path and name of the assembly to be loaded, along with a pointer to an [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) interface object to that method.</span></span> <span data-ttu-id="ed918-119">Profiler pak může zavolat metodu [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference –](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) s `COR_PRF_ASSEMBLY_REFERENCE_INFO` objektem pro každé cílové sestavení, které plánuje odkaz na odkaz ze sestavení zadaného ve zpětném volání [ICorProfilerCallback6:: GetAssemblyReferences –](icorprofilercallback6-getassemblyreferences-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ed918-119">The profiler can then call the [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) method with a `COR_PRF_ASSEMBLY_REFERENCE_INFO` object for each target assembly it plans to reference from the assembly specified in the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed918-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ed918-120">Requirements</span></span>  
 <span data-ttu-id="ed918-121">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed918-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed918-122">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ed918-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ed918-123">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ed918-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ed918-124">**Verze .NET Framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed918-124">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed918-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ed918-125">See also</span></span>

- [<span data-ttu-id="ed918-126">Struktury pro profilaci</span><span class="sxs-lookup"><span data-stu-id="ed918-126">Profiling Structures</span></span>](profiling-structures.md)
- [<span data-ttu-id="ed918-127">Metoda GetAssemblyReferences</span><span class="sxs-lookup"><span data-stu-id="ed918-127">GetAssemblyReferences Method</span></span>](icorprofilercallback6-getassemblyreferences-method.md)
- [<span data-ttu-id="ed918-128">Metoda AddAssemblyReference</span><span class="sxs-lookup"><span data-stu-id="ed918-128">AddAssemblyReference Method</span></span>](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)
