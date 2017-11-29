---
title: "LoggingLevelEnum – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: LoggingLevelEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: LoggingLevelEnum
helpviewer_keywords: LoggingLevelEnum enumeration [.NET Framework debugging]
ms.assetid: 09daac08-005a-46b2-beab-408d0820c5e5
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1f6041f429c057cea9607df34ec5691be84e2d3c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Diagnostics.EventLog>  
 [Ladění výčtů](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
