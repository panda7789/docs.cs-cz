---
title: LoggingLevelEnum – výčet
ms.date: 03/30/2017
api_name:
- LoggingLevelEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- LoggingLevelEnum
helpviewer_keywords:
- LoggingLevelEnum enumeration [.NET Framework debugging]
ms.assetid: 09daac08-005a-46b2-beab-408d0820c5e5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9659dd835bb60adf8471f73ed45b6588cf15126f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752595"
---
# <a name="logginglevelenum-enumeration"></a>LoggingLevelEnum – výčet
Určuje úroveň závažnosti popisnou zprávou, která jsou zapsána do protokolu událostí při spravovaným vláknem se zaprotokoluje událost.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum LoggingLevelEnum {  
    LTraceLevel0 = 0,  
    LTraceLevel1,  
    LTraceLevel2,  
    LTraceLevel3,  
    LTraceLevel4,  
    LStatusLevel0 = 20,  
    LStatusLevel1,  
    LStatusLevel2,  
    LStatusLevel3,  
    LStatusLevel4,  
    LWarningLevel = 40,  
    LErrorLevel = 50,  
    LPanicLevel = 100  
} LoggingLevelEnum;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`LTraceLevel0`|Zpráva je úroveň trasování 0.|  
|`LTraceLevel1`|Zpráva je 1 úroveň trasování.|  
|`LTraceLevel2`|Zpráva je úroveň trasování 2.|  
|`LTraceLevel3`|Úroveň trasování 3 je zpráva.|  
|`LTraceLevel4`|Úroveň trasování 4 je zpráva.|  
|`LStatusLevel0`|Zpráva je úroveň stav 0.|  
|`LStatusLevel1`|Zpráva je stav úrovně 1.|  
|`LStatusLevel2`|Zpráva je stav úrovně 2.|  
|`LStatusLevel3`|Zpráva je stav úrovně 3.|  
|`LStatusLevel4`|Úroveň stavu 4 je zpráva.|  
|`LWarningLevel`|Zpráva je úroveň pro upozornění.|  
|`LErrorLevel`|Zpráva je úrovně chyby.|  
|`LPanicLevel`|Zpráva je tísňový úroveň.|  
  
## <a name="remarks"></a>Poznámky  
 Common language runtime (CLR) zavolá [icordebugmanagedcallback::logmessage –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md) metoda oznámit ladicího programu, že má spravovaným vláknem protokoluje událost. Modul CLR předá hodnotu `LoggingLevelEnum` výčet označující úroveň závažnosti zprávy, která spravované vlákno zapsáno do protokolu událostí.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Diagnostics.EventLog>
- [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
