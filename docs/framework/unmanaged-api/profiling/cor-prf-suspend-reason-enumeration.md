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
ms.openlocfilehash: 1036ecbdb735b95c0ad6897c1545e3bd8cb6c3a9
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867071"
---
# <a name="cor_prf_suspend_reason-enumeration"></a>COR_PRF_SUSPEND_REASON – výčet
Označuje důvod, proč je modul runtime pozastaven.  
  
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
|`COR_PRF_FIELD_SUSPEND_OTHER`|Modul runtime je pozastaven z nespecifikovaného důvodu.|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC`|Modul runtime je pozastaven na obsluhu žádosti o uvolnění paměti.<br /><br /> Zpětná volání související s uvolňováním paměti nastávají mezi zpětnými voláními [ICorProfilerCallback:: RuntimeSuspendFinished –](icorprofilercallback-runtimesuspendfinished-method.md) a [ICorProfilerCallback:: RuntimeResumeStarted –](icorprofilercallback-runtimeresumestarted-method.md) .|  
|`COR_PRF_FIELD_SUSPEND_FOR_APPDOMAIN_SHUTDOWN`|Modul runtime je pozastaven, aby bylo možné vypnout `AppDomain`.<br /><br /> I když je modul runtime pozastaven, modul runtime určí, která vlákna jsou v `AppDomain`, která se vypíná a která se nastaví pro přerušení při obnovení. Během tohoto pozastavení neexistují žádná zpětná volání specifická pro `AppDomain`.|  
|`COR_PRF_FIELD_SUSPEND_FOR_CODE_PITCHING`|Modul runtime je pozastaven, aby mohlo dojít k rozteči kódu.<br /><br /> Rozteč kódu platí pouze v případě, že je kompilátor JIT (just-in-time) aktivní se zapnutým příznakem pro rozteč kódu. Zpětná volání pro rozteč kódu se vyskytují mezi `ICorProfilerCallback::RuntimeSuspendFinished` a `ICorProfilerCallback::RuntimeResumeStarted` zpětná volání. **Poznámka:**  Kompilátor JIT CLR nemění funkce v .NET Framework verze 2,0, takže se tato hodnota nepoužívá v 2,0.|  
|`COR_PRF_FIELD_SUSPEND_FOR_SHUTDOWN`|Modul runtime je pozastaven, aby mohl být vypnut. Aby bylo možné operaci dokončit, je nutné pozastavit všechna vlákna.|  
|`COR_PRF_FIELD_SUSPEND_FOR_INPROC_DEBUGGER`|Modul runtime je pozastaven pro vnitroprocesové ladění.|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC_PREP`|Modul runtime je pozastaven pro přípravu na uvolnění paměti.|  
|`COR_PRF_SUSPEND_FOR_REJIT`|Modul runtime je pozastaven pro rekompilaci JIT.|  
  
## <a name="remarks"></a>Poznámky  
 Všechna vlákna modulu runtime, která jsou v nespravovaném kódu, mohou pokračovat v běhu, dokud se nepokusí znovu zadat modul runtime. v takovém případě budou také pozastaveny, dokud modul runtime nebude pokračovat. To platí také pro nová vlákna, která vstupují do modulu runtime. Všechna vlákna v modulu runtime jsou okamžitě pozastavena, pokud jsou v kódu přerušitelné, nebo se po zobrazení výzvy k tomu, že mají přístup ke kódu přerušitelné, pozastaví.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro profilaci](profiling-enumerations.md)
