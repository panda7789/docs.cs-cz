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
ms.openlocfilehash: 12e7faa8d9fee7698de9d9734f522d818f225c84
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500816"
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
  
## <a name="members"></a>Členové  
  
|Člen|Description|  
|------------|-----------------|  
|COR_PRF_MODULE_DISK|Modul se načetl z disku.|  
|COR_PRF_MODULE_NGEN|Modul byl vygenerován pomocí generátoru nativních bitových kopií (Ngen. exe).|  
|COR_PRF_MODULE_DYNAMIC|Modul byl vytvořen metodami v <xref:System.Reflection.Emit?displayProperty=nameWithType> oboru názvů.|  
|COR_PRF_MODULE_COLLECTIBLE|Doba života modulu je spravovaná systémem uvolňování paměti.|  
|COR_PRF_MODULE_RESOURCE|Modul neobsahuje žádná metadata a používá se výhradně jako prostředek. Spravovaný ekvivalent tohoto bitu je <xref:System.Reflection.Module.IsResource%2A?displayProperty=nameWithType> metoda.|  
|COR_PRF_MODULE_FLAT_LAYOUT|Rozložení modulu v paměti je ploché, není namapované. Pokud modul obsahuje tuto bitovou sadu, profilery, které čtou informace přímo z hlavičky přenositelného spustitelného souboru (PE), budou muset být opatrní při interpretaci relativních virtuálních adres (RVA) v hlavičce.|  
|COR_PRF_MODULE_WINDOWS_RUNTIME|Příznak typu prostředí Windows Runtime obsahu je nastaven v metadatech pro sestavení tohoto modulu. Toto je případ pro všechny moduly metadat systému Windows (. winmd).|  
  
## <a name="remarks"></a>Poznámky  
 Bity z COR_PRF_MODULE_FLAGS jsou vráceny do profileru v `pdwModuleFlags` parametru Output metody [ICorProfilerInfo3:: GetModuleInfo2 –](icorprofilerinfo3-getmoduleinfo2-method.md) . Některé kombinace dvou nebo více příznaků jsou možné, ale ne všechny kombinace jsou možné.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro profilaci](profiling-enumerations.md)
