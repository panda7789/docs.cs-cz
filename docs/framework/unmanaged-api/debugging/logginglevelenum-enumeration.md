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
ms.openlocfilehash: 331065d4aae82c66b9ebd82e99427501c3ba8a98
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="logginglevelenum-enumeration"></a>LoggingLevelEnum – výčet
Určuje úroveň závažnosti popisný zprávu, která se zapíšou do protokolu událostí, když spravované vlákno protokoluje nějakou událost.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|`LTraceLevel1`|Zpráva je úroveň trasování 1.|  
|`LTraceLevel2`|Zpráva je úroveň trasování 2.|  
|`LTraceLevel3`|Zpráva je úroveň trasování 3.|  
|`LTraceLevel4`|Zpráva je úroveň trasování 4.|  
|`LStatusLevel0`|Zpráva je úroveň stav 0.|  
|`LStatusLevel1`|Zpráva je stav úrovně 1.|  
|`LStatusLevel2`|Zpráva je stav úroveň 2.|  
|`LStatusLevel3`|Zpráva je stav úroveň 3.|  
|`LStatusLevel4`|Zpráva je stav úroveň 4.|  
|`LWarningLevel`|Zpráva je úroveň pro upozornění.|  
|`LErrorLevel`|Zpráva je úroveň chyby.|  
|`LPanicLevel`|Zpráva je tísňový úroveň.|  
  
## <a name="remarks"></a>Poznámky  
 Modul CLR (CLR) volání [icordebugmanagedcallback::logmessage –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md) metoda ladicího programu oznámit, že spravované vlákno se přihlásil událost. Modul CLR předá hodnotu `LoggingLevelEnum` výčtu označíte, úroveň závažnosti zprávu, která spravované vlákno napsali do protokolu událostí.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Diagnostics.EventLog>  
 [Výčty pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
