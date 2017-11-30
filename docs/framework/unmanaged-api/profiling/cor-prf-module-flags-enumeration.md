---
title: "COR_PRF_MODULE_FLAGS – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_MODULE_FLAGS
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_MODULE_FLAGS
helpviewer_keywords: COR_PRF_MODULE_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 7bc3a938-0df1-4739-9ff1-89cff454b704
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 54a8ee366431360f7b653b48f4ce407a35f8465b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
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
|COR_PRF_MODULE_DISK|Modul byl načten z disku.|  
|COR_PRF_MODULE_NGEN|Modul vygenerovalo generátor (Ngen.exe).|  
|COR_PRF_MODULE_DYNAMIC|Modul byl vytvořen pomocí jiných metod v <xref:System.Reflection.Emit?displayProperty=nameWithType> oboru názvů.|  
|COR_PRF_MODULE_COLLECTIBLE|Doba platnosti modulu spravuje uvolňování paměti.|  
|COR_PRF_MODULE_RESOURCE|Modul obsahuje žádná metadata. a používá výhradně jako prostředek. Je spravovaný ekvivalent tento bit <xref:System.Reflection.Module.IsResource%2A?displayProperty=nameWithType> metoda.|  
|COR_PRF_MODULE_FLAT_LAYOUT|Modulu rozložení v paměti je plochý, není namapované. Pokud modul má tento bit do nastavený, profilery, které čtou informace přímo z přenosné hlavičky spustitelného souboru (PE) bude muset být opatrní při interpretaci relativní virtuální adresy (RVAs) v hlavičce.|  
|COR_PRF_MODULE_WINDOWS_RUNTIME|Příznak prostředí Windows Runtime typ obsahu je nastaven v metadatech pro tento modul sestavení. To platí pro všechny moduly metadat Windows (.winmd).|  
  
## <a name="remarks"></a>Poznámky  
 Služba BITS z COR_PRF_MODULE_FLAGS se vrátíte na profileru v `pdwModuleFlags` výstupní parametr [icorprofilerinfo3::getmoduleinfo2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md) metoda. Některé kombinací dvou nebo více příznaků je možné, ale ne všechny kombinace jsou možné.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Profilace výčtů](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
