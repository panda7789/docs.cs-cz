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
ms.openlocfilehash: e084bc957eca9474078ed5ca3aef0276361dbe1b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745537"
---
# <a name="corprfsuspendreason-enumeration"></a>COR_PRF_SUSPEND_REASON – výčet
Označuje, že je pozastavený, modul runtime důvod.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
|`COR_PRF_FIELD_SUSPEND_OTHER`|Modul runtime je pozastaven z neznámého důvodu nezdařila.|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC`|Modul runtime je pozastavený, k plnění požadavků kolekce uvolnění paměti.<br /><br /> Zpětná volání související s kolekcí uvolnění paměti, ke kterým dochází mezi [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) a [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) zpětná volání.|  
|`COR_PRF_FIELD_SUSPEND_FOR_APPDOMAIN_SHUTDOWN`|Modul runtime je pozastavený, tak, aby `AppDomain` můžete vypnout.<br /><br /> Modul runtime je pozastaven, modul runtime se určit, která vlákna jsou v `AppDomain` , který je právě vypnout a nastavit je na zrušení po jejich obnovení. Neexistují žádné `AppDomain`-konkrétní zpětná volání během této doby pozastavení.|  
|`COR_PRF_FIELD_SUSPEND_FOR_CODE_PITCHING`|Modul runtime je pozastavený, aby mohla probíhat pitching kódu.<br /><br /> Kód pitching vyplývá, pouze pokud kompilátor just-in-time (JIT) je aktivní s kódem pitching povolené. Kód pitching zpětná volání, ke kterým dochází mezi `ICorProfilerCallback::RuntimeSuspendFinished` a `ICorProfilerCallback::RuntimeResumeStarted` zpětná volání. **Poznámka:**  CLR JIT není představení funkcí v rozhraní .NET Framework verze 2.0, takže tato hodnota se používá ve verzi 2.0.|  
|`COR_PRF_FIELD_SUSPEND_FOR_SHUTDOWN`|Modul runtime je pozastavený, takže můžete vypnout. Se musí pozastavit všechna vlákna do dokončení operace.|  
|`COR_PRF_FIELD_SUSPEND_FOR_INPROC_DEBUGGER`|Modul runtime je pozastaven vnitroprocesové ladění.|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC_PREP`|Modul runtime je pozastavený, příprava pro uvolnění paměti.|  
|`COR_PRF_SUSPEND_FOR_REJIT`|Modul runtime je pozastaven rekompilace JIT.|  
  
## <a name="remarks"></a>Poznámky  
 Všechna vlákna modulu runtime, které jsou v nespravovaném kódu povoleno spuštění, dokud se pokusí znovu zadat modulu runtime, v tomto okamžiku se bude také být pozastaveno, dokud modul runtime bude pokračovat dál. To platí i pro nová vlákna, které zadejte modul runtime. Všechna vlákna v modulu runtime jsou pozastavena okamžitě, když jsou v paralelní kód nebo dotaz, pozastavit, když dosáhnou paralelní kód.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
