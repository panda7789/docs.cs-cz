---
title: Událost Trasování událostí pro Windows výjimky Thrown_V1
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 91abd9e6f31380b7e8cd3df1a14aa5c5722901ba
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046517"
---
# <a name="exception-thrown_v1-etw-event"></a>Událost Trasování událostí pro Windows výjimky Thrown_V1
Tato událost zachycuje informace o vyvolaných výjimkách.  
  
 Následující tabulka ukazuje klíčové slovo, pod kterým je událost vyvolána, a úroveň události. (Další informace najdete v tématu [klíčová slova a úrovně CLR ETW](clr-etw-keywords-and-levels.md).)  
  
|Klíčové slovo pro vyvolání události|Level|  
|-----------------------------------|-----------|  
|`ExceptionKeyword` (0x8000)|Upozornění (2)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|80|Je vyvolána spravovaná výjimka.|  
  
 V následující tabulce jsou uvedena data události.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|Typ výjimky|win:UnicodeString|Typ výjimky; například `System.NullReferenceException`.|  
|Zpráva o výjimce|win:UnicodeString|Skutečná zpráva výjimky|  
|EIPCodeThrow|win:Pointer|Ukazatel na instrukci, kde došlo k výjimce.|  
|ExceptionHR|Win: UInt32|Výjimka [HRESULT](https://go.microsoft.com/fwlink/?LinkId=179679).|  
|ExceptionFlags|Win: UInt16|0x01: HasInnerException (viz [události CLR ETW](clr-etw-events.md) v dokumentaci k Visual Basic).<br /><br /> 0x02 IsNestedException.<br /><br /> 0x04: IsRethrownException.<br /><br /> 0x08: IsCorruptedStateException (označuje, že stav procesu je poškozený. viz [manipulace s poškozenými výjimkami stavu](https://go.microsoft.com/fwlink/?LinkId=179681) na webu MSDN).<br /><br /> 0x10 IsCLSCompliant (výjimka, která je odvozena <xref:System.Exception> z je kompatibilní se specifikací CLS; v opačném případě není kompatibilní se specifikací CLS).|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
## <a name="see-also"></a>Viz také:

- [Události Trasování událostí pro Windows v CLR](clr-etw-events.md)
