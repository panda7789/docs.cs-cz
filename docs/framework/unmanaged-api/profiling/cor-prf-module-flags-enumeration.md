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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f94867db6908f0999604511d9782b6f5abfb5e77
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752048"
---
# <a name="corprfmoduleflags-enumeration"></a>COR_PRF_MODULE_FLAGS – výčet
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
  
|Člen|Popis|  
|------------|-----------------|  
|COR_PRF_MODULE_DISK|Byl modul načten z disku.|  
|COR_PRF_MODULE_NGEN|V modulu vygeneroval Native Image Generator (Ngen.exe).|  
|COR_PRF_MODULE_DYNAMIC|Modul byl vytvořen pomocí jiných metod v <xref:System.Reflection.Emit?displayProperty=nameWithType> oboru názvů.|  
|COR_PRF_MODULE_COLLECTIBLE|Životnost modulu se spravuje přes systému uvolňování paměti.|  
|COR_PRF_MODULE_RESOURCE|Modul obsahuje žádná metadata a používá výhradně jako prostředek. Spravované ekvivalent tento bit je <xref:System.Reflection.Module.IsResource%2A?displayProperty=nameWithType> metody.|  
|COR_PRF_MODULE_FLAT_LAYOUT|Rozložení modulu v paměti je plochý, není namapována. Pokud modul je tento bit nastaven, profilovací programy, které čtou informace přímo z přenosné záhlaví spustitelného souboru (PE) bude muset být opatrní při interpretaci relativních virtuálních adres (RVA) v záhlaví.|  
|COR_PRF_MODULE_WINDOWS_RUNTIME|Příznak prostředí Windows Runtime typu obsahu je nastaven v metadatech pro tento modul sestavení. To platí pro všechny moduly metadat Windows (.winmd).|  
  
## <a name="remarks"></a>Poznámky  
 Bitů z cor_prf_module_flags – se vrátíte do okna profilování v `pdwModuleFlags` výstupní parametr z [icorprofilerinfo3::getmoduleinfo2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md) metody. Některé kombinací dvou nebo více příznaků je možné, ale ne všechny kombinace jsou možné.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
