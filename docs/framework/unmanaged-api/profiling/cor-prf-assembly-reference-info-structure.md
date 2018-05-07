---
title: Struktura COR_PRF_ASSEMBLY_REFERENCE_INFO
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: c8c1d916-8d1a-4f82-8128-9fd3732383fc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: be32718ca392ce1712b8ce9f2e33a8f602ccb242
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="corprfassemblyreferenceinfo-structure"></a>Struktura COR_PRF_ASSEMBLY_REFERENCE_INFO
[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]  
  
 Poskytuje modul common language runtime s informacemi o odkaz na sestavení, který ho měli zvážit při procházení uzavření odkaz na sestavení.  
  
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
|`pbPublicKeyOrToken`|Ukazatel na veřejné klíče nebo s tokenem sestavení.|  
|`cbPublicKeyOrToken`|Počet bajtů v veřejný klíč nebo na tokenu.|  
|`szName`|Název sestavení, které se odkazuje.|  
|`pMetaData`|Ukazatel na metadata sestavení.|  
|`pbHashValue`|Ukazatel na binární rozsáhlý objekt hash (binární rozsáhlý OBJEKT).|  
|`cbHashValue`|Počet bajtů hash objektů BLOB.|  
|`dwAssemblyRefFlags`|Příznaky sestavení.|  
  
## <a name="remarks"></a>Poznámky  
 `COR_PRF_EX_CLAUSE_INFO` Struktura je naplněn profileru při deklaruje odkazy na další sestavení, které modul common language runtime měli zvážit při procházení uzavření odkaz na sestavení.  
  
 Pokud profileru zaregistruje [icorprofilercallback6::getassemblyreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) metoda zpětného volání, modul runtime předá cestu a název sestavení, která má být načten, spolu s odkazy [ ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) rozhraní objektu do dané metody. Potom můžete volat profileru [icorprofilerassemblyreferenceprovider::addassemblyreference –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) metoda s `COR_PRF_ASSEMBLY_REFERENCE_INFO` objekt pro každý cíl sestavení se plánuje odkazovat z sestavení zadané v [ Icorprofilercallback6::getassemblyreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) zpětného volání.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Struktury pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)  
 [GetAssemblyReferences – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)  
 [AddAssemblyReference – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)
