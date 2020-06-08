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
  
|Člen|Description|  
|------------|-----------------|  
|`pbPublicKeyOrToken`|Ukazatel na veřejný klíč nebo token sestavení.|  
|`cbPublicKeyOrToken`|Počet bajtů ve veřejném klíči nebo tokenu.|  
|`szName`|Název sestavení, na které se odkazuje.|  
|`pMetaData`|Ukazatel na metadata sestavení.|  
|`pbHashValue`|Ukazatel na binární rozsáhlý objekt hash (BLOB).|  
|`cbHashValue`|Počet bajtů v objektu BLOB hash.|  
|`dwAssemblyRefFlags`|Příznaky sestavení.|  
  
## <a name="remarks"></a>Poznámky  
 `COR_PRF_EX_CLAUSE_INFO`Struktura je vyplněna profilerem při deklaraci dalších odkazů na sestavení, které by měl při provádění procházení uzavření odkazu na sestavení zvážit modul common language runtime.  
  
 Pokud profiler registruje pro metodu zpětného volání [ICorProfilerCallback6:: GetAssemblyReferences –](icorprofilercallback6-getassemblyreferences-method.md) , modul runtime předá cestu a název sestavení, které mají být načteny, spolu s ukazatelem na objekt rozhraní [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) k této metodě. Profiler pak může zavolat metodu [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference –](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) s `COR_PRF_ASSEMBLY_REFERENCE_INFO` objektem pro každé cílové sestavení, které plánuje odkaz na odkaz ze sestavení zadaného ve zpětném volání [ICorProfilerCallback6:: GetAssemblyReferences –](icorprofilercallback6-getassemblyreferences-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro profilaci](profiling-structures.md)
- [Metoda GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md)
- [Metoda AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)
