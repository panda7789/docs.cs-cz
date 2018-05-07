---
title: Událost Trasování událostí pro Windows výjimky Thrown_V1
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dafa5846f779276ab81e8e30e7c7a50b9fbff853
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="exception-thrownv1-etw-event"></a>Událost Trasování událostí pro Windows výjimky Thrown_V1
Tato událost zaznamená informace o výjimky, které jsou vydány.  
  
 Následující tabulka uvádí klíčové slovo, pod kterým je událost vyvolána a úroveň události. (Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|– Klíčové slovo za vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`ExceptionKeyword` (0x8000)|Upozornění (2)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá, když|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|80|Spravované výjimky je vyvolána.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|Typ výjimky|Win: UnicodeString|Typ výjimky; například `System.NullReferenceException`.|  
|Zpráva o výjimce|Win: UnicodeString|Zpráva o výjimce skutečný.|  
|EIPCodeThrow|Win: ukazatele|Ukazatel instrukce, kde došlo k výjimce.|  
|ExceptionHR|Win: UInt32|Výjimka [HRESULT](http://go.microsoft.com/fwlink/?LinkId=179679).|  
|Příznaky výjimky|Win: UInt16|0x01: HasInnerException (viz [události ETW CLR](../../../docs/framework/performance/clr-etw-events.md) v dokumentaci k jazyka Visual Basic).<br /><br /> 0x02: IsNestedException.<br /><br /> 0x04: IsRethrownException.<br /><br /> 0x08: IsCorruptedStateException (označuje, že je poškozený stav procesu; viz [zpracování poškozený stav výjimky](http://go.microsoft.com/fwlink/?LinkId=179681) na webu MSDN).<br /><br /> 0x10: IsCLSCompliant (výjimku, která je odvozena z <xref:System.Exception> je kompatibilní se specifikací CLS, jinak hodnota není kompatibilní se specifikací CLS).|  
|ClrInstanceID|Win: UInt16|Jedinečné ID pro instanci CLR nebo CoreCLR.|  
  
## <a name="see-also"></a>Viz také  
 [Události Trasování událostí pro Windows v CLR](../../../docs/framework/performance/clr-etw-events.md)
