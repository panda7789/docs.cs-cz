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
# <a name="cor_prf_assembly_reference_info-structure"></a>Struktura COR_PRF_ASSEMBLY_REFERENCE_INFO
[Podporované v .NET Framework 4.5.2 a novějších verzích]  
  
 Poskytuje modul CLR (Common Language Runtime) informace o odkazech na sestavení, které by měly být zváženy při provádění procházení ukončení odkazu na sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
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
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`pbPublicKeyOrToken`|Ukazatel na veřejný klíč nebo token sestavení.|  
|`cbPublicKeyOrToken`|Počet bajtů ve veřejném klíči nebo tokenu.|  
|`szName`|Název sestavení, na které se odkazuje.|  
|`pMetaData`|Ukazatel na metadata sestavení.|  
|`pbHashValue`|Ukazatel na binární rozsáhlý objekt hash (BLOB).|  
|`cbHashValue`|Počet bajtů v objektu BLOB hash.|  
|`dwAssemblyRefFlags`|Příznaky sestavení.|  
  
## <a name="remarks"></a>Poznámky  
 Struktura `COR_PRF_EX_CLAUSE_INFO` je vyplněna profilerem při deklaraci dalších odkazů na sestavení, které by měl zvážit modul common language runtime, když je prováděno procházení uzavření odkazu na sestavení.  
  
 Pokud profiler registruje pro metodu zpětného volání [ICorProfilerCallback6:: GetAssemblyReferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) , modul runtime předá cestu a název sestavení, které se má načíst, spolu s ukazatelem na [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) objekt rozhraní k této metodě. Profiler pak může zavolat metodu [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) s objektem `COR_PRF_ASSEMBLY_REFERENCE_INFO` pro každé cílové sestavení, které plánuje odkazovat ze sestavení určeného v [ICorProfilerCallback6:: GetAssemblyReferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) zpětné volání.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
- [GetAssemblyReferences – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)
- [AddAssemblyReference – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)
