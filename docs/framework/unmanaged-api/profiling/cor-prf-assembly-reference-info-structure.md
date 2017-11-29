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
ms.openlocfilehash: 000a338400efa0d70e690f585518304a8b525346
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Struktury pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)  
 [Metoda GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)  
 [Metoda AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)
