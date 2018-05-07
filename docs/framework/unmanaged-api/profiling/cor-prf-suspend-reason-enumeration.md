---
title: COR_PRF_SUSPEND_REASON – výčet
ms.date: 03/30/2017
api_name:
- COR_PRF_SUSPEND_REASON
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_SUSPEND_REASON
helpviewer_keywords:
- COR_PRF_SUSPEND_REASON enumeration [.NET Framework profiling]
ms.assetid: 75594833-bed3-47b2-a426-b75c5fe6fbcf
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2f4382c7fa85008de9e67ad21c467402bae4ac90
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="corprfsuspendreason-enumeration"></a>COR_PRF_SUSPEND_REASON – výčet
Určuje, z důvodu, že je pozastaveno modulu runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum {  
    COR_PRF_SUSPEND_OTHER                   = 0x00,  
    COR_PRF_SUSPEND_FOR_GC                  = 0x01,  
    COR_PRF_SUSPEND_FOR_APPDOMAIN_SHUTDOWN  = 0x02,  
    COR_PRF_SUSPEND_FOR_CODE_PITCHING       = 0x03,  
    COR_PRF_SUSPEND_FOR_SHUTDOWN            = 0x04,  
    COR_PRF_SUSPEND_FOR_INPROC_DEBUGGER     = 0x06,  
    COR_PRF_SUSPEND_FOR_GC_PREP             = 0x07,    COR_PRF_SUSPEND_FOR_REJIT               = 8  
} COR_PRF_SUSPEND_REASON;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`COR_PRF_FIELD_SUSPEND_OTHER`|Modul runtime je pozastaven z neznámého důvodu.|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC`|Modul runtime pozastavený, aby služba žádost kolekce paměti.<br /><br /> Zpětná volání související s kolekcí paměti dojde k mezi [icorprofilercallback::runtimesuspendfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) a [icorprofilercallback::runtimeresumestarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) zpětných volání.|  
|`COR_PRF_FIELD_SUSPEND_FOR_APPDOMAIN_SHUTDOWN`|Modul runtime je pozastaveno, aby `AppDomain` může být vypnut.<br /><br /> Modul runtime pozastaven, modul runtime určí vláken, které jsou v `AppDomain` který je právě vypnout a nastavit je k přerušení po jejich obnovení. Neexistují žádné `AppDomain`-konkrétní zpětná volání během této doby pozastavení.|  
|`COR_PRF_FIELD_SUSPEND_FOR_CODE_PITCHING`|Modul runtime je pozastaven, tak, aby pitching kódu může dojít.<br /><br /> Kód pitching vyplývá, pouze když kompilátoru za běhu (JIT) je aktivní s kód pitching povolena. Kód pitching zpětná volání dojít mezi `ICorProfilerCallback::RuntimeSuspendFinished` a `ICorProfilerCallback::RuntimeResumeStarted` zpětných volání. **Poznámka:** CLR JIT není pro představení funkce v rozhraní .NET Framework verze 2.0, tak tato hodnota se nepoužívá v 2.0.|  
|`COR_PRF_FIELD_SUSPEND_FOR_SHUTDOWN`|Modul runtime je pozastaven, tak, aby ho vypnout. Musíte ho pozastavit všechna vlákna k dokončení operace.|  
|`COR_PRF_FIELD_SUSPEND_FOR_INPROC_DEBUGGER`|Modul runtime je pozastavená v procesu ladění.|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC_PREP`|Příprava pro kolekci paměti je pozastaven modulem runtime.|  
|`COR_PRF_SUSPEND_FOR_REJIT`|Modul runtime je pozastaven pro opětovnou kompilaci JIT.|  
  
## <a name="remarks"></a>Poznámky  
 Všechna vlákna modulu runtime, které jsou v nespravovaném kódu je povoleno dále běžet až do snaží znovu zadat modulu runtime v bod, který se bude také pozastavuje, dokud nebude obnoví modulu runtime. To platí také pro nové vláken, která zadejte modulu runtime. Všechna vlákna v modulu runtime jsou buď okamžitě pozastaveno, pokud se dá přerušit kódu nebo požádáni, abyste pozastavit po uplynutí přerušitelné kódu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
