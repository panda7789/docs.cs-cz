---
title: Událost Trasování událostí pro Windows výjimky Thrown_V1
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3f0e968053c87319bf90bf3de0f21d750ec899ab
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447626"
---
# <a name="exception-thrown_v1-etw-event"></a>Událost Trasování událostí pro Windows výjimky Thrown_V1
This event captures information about the exceptions that are thrown.  
  
 The following table shows the keyword under which the event is raised, and the level of the event. (For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)  
  
|Keyword for raising the event|Level|  
|-----------------------------------|-----------|  
|`ExceptionKeyword` (0x8000)|Warning (2)|  
  
 The following table shows event information.  
  
|Událost|Event ID|Raised when|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|80|A managed exception is thrown.|  
  
 The following table shows event data.  
  
|Field name|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|Exception Type|win:UnicodeString|Type of the exception; for example, `System.NullReferenceException`.|  
|Exception Message|win:UnicodeString|Actual exception message.|  
|EIPCodeThrow|win:Pointer|Instruction pointer where exception occurred.|  
|ExceptionHR|win:UInt32|Exception [HRESULT](https://docs.microsoft.com/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).|  
|ExceptionFlags|win:UInt16|0x01: HasInnerException (see [CLR ETW Events](clr-etw-events.md) in the Visual Basic documentation).<br /><br /> 0x02: IsNestedException.<br /><br /> 0x04: IsRethrownException.<br /><br /> 0x08: IsCorruptedStateException (indicates that the process state is corrupt; see [Handling Corrupted State Exceptions](https://docs.microsoft.com/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).<br /><br /> 0x10: IsCLSCompliant (an exception that derives from <xref:System.Exception> is CLS-compliant; otherwise, it is not CLS-compliant).|  
|ClrInstanceID|win:UInt16|Unique ID for the instance of CLR or CoreCLR.|  
  
## <a name="see-also"></a>Viz také:

- [Události Trasování událostí pro Windows v CLR](clr-etw-events.md)
