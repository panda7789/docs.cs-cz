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
ms.openlocfilehash: 62ea982f30a6a73648d9bf36722c0b5a49a68896
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420744"
---
# <a name="logginglevelenum-enumeration"></a>LoggingLevelEnum – výčet
Označuje úroveň závažnosti popisné zprávy, která je zapsána do protokolu událostí, když spravované vlákno zaznamená událost.  
  
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
|`LTraceLevel1`|Zpráva je úroveň trasování 1.|  
|`LTraceLevel2`|Zpráva je úroveň trasování 2.|  
|`LTraceLevel3`|Zpráva je úroveň trasování 3.|  
|`LTraceLevel4`|Zpráva je úroveň trasování 4.|  
|`LStatusLevel0`|Zpráva je úroveň stavu 0.|  
|`LStatusLevel1`|Zpráva je úroveň stavu 1.|  
|`LStatusLevel2`|Zpráva je úroveň stavu 2.|  
|`LStatusLevel3`|Zpráva je stavová úroveň 3.|  
|`LStatusLevel4`|Zpráva je úroveň stavu 4.|  
|`LWarningLevel`|Zpráva je úroveň upozornění.|  
|`LErrorLevel`|Zpráva je úroveň chyby.|  
|`LPanicLevel`|Zpráva je nenouzová úroveň.|  
  
## <a name="remarks"></a>Poznámky  
 Modul CLR (Common Language Runtime) volá metodu [ICorDebugManagedCallback:: LogMessage –](icordebugmanagedcallback-logmessage-method.md) , která oznamuje ladicímu programu, že spravované vlákno zaznamenalo událost. Modul CLR předá hodnotu `LoggingLevelEnum` výčtu, aby označoval úroveň závažnosti zprávy, kterou spravované vlákno zapsalo do protokolu událostí.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Diagnostics.EventLog>
- [Ladění výčtů](debugging-enumerations.md)
