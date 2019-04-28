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
ms.openlocfilehash: 98fee786a7acb87598baabed62067b599907bede
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61599140"
---
# <a name="corprfmoduleflags-enumeration"></a>COR_PRF_MODULE_FLAGS – výčet
Určuje vlastnosti modulu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
