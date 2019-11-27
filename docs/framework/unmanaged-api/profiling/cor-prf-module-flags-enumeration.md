---
title: COR_PRF_MODULE_FLAGS – výčet
ms.date: 03/30/2017
api_name:
- COR_PRF_MODULE_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_MODULE_FLAGS
helpviewer_keywords:
- COR_PRF_MODULE_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 7bc3a938-0df1-4739-9ff1-89cff454b704
topic_type:
- apiref
ms.openlocfilehash: bdbf93ba4df50cf26538f0e527fdc3c982bb274e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447331"
---
# <a name="cor_prf_module_flags-enumeration"></a>COR_PRF_MODULE_FLAGS – výčet
Určuje vlastnosti modulu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum  
{  
    COR_PRF_MODULE_DISK             = 0x00000001,  
    COR_PRF_MODULE_NGEN             = 0x00000002,  
    COR_PRF_MODULE_DYNAMIC          = 0x00000004,  
    COR_PRF_MODULE_COLLECTIBLE      = 0x00000008,  
    COR_PRF_MODULE_RESOURCE         = 0x00000010,  
    COR_PRF_MODULE_FLAT_LAYOUT      = 0x00000020,  
    COR_PRF_MODULE_WINDOWS_RUNTIME  = 0x00000040  
}   COR_PRF_MODULE_FLAGS;  
```  
  
## <a name="members"></a>Members  
  
|Člen|Popis|  
|------------|-----------------|  
|COR_PRF_MODULE_DISK|Modul se načetl z disku.|  
|COR_PRF_MODULE_NGEN|Modul byl vygenerován pomocí generátoru nativních bitových kopií (Ngen. exe).|  
|COR_PRF_MODULE_DYNAMIC|Modul byl vytvořen metodami v oboru názvů <xref:System.Reflection.Emit?displayProperty=nameWithType>.|  
|COR_PRF_MODULE_COLLECTIBLE|Doba života modulu je spravovaná systémem uvolňování paměti.|  
|COR_PRF_MODULE_RESOURCE|Modul neobsahuje žádná metadata a používá se výhradně jako prostředek. Spravovaný ekvivalent tohoto bitu je <xref:System.Reflection.Module.IsResource%2A?displayProperty=nameWithType> metoda.|  
|COR_PRF_MODULE_FLAT_LAYOUT|Rozložení modulu v paměti je ploché, není namapované. Pokud modul obsahuje tuto bitovou sadu, profilery, které čtou informace přímo z hlavičky přenositelného spustitelného souboru (PE), budou muset být opatrní při interpretaci relativních virtuálních adres (RVA) v hlavičce.|  
|COR_PRF_MODULE_WINDOWS_RUNTIME|Příznak typu prostředí Windows Runtime obsahu je nastaven v metadatech pro sestavení tohoto modulu. Toto je případ pro všechny moduly metadat systému Windows (. winmd).|  
  
## <a name="remarks"></a>Poznámky  
 Bity z COR_PRF_MODULE_FLAGS jsou vráceny do profileru v parametru `pdwModuleFlags` Output metody [ICorProfilerInfo3:: GetModuleInfo2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md) . Některé kombinace dvou nebo více příznaků jsou možné, ale ne všechny kombinace jsou možné.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
