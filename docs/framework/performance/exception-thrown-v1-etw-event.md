---
title: Událost Trasování událostí pro Windows výjimky Thrown_V1
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 865b7b16d5807bd9161855f453128a63c84eab96
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43400819"
---
# <a name="exception-thrownv1-etw-event"></a>Událost Trasování událostí pro Windows výjimky Thrown_V1
Tato událost zaznamená informace o výjimkách, které jsou vyvolány.  
  
 V následující tabulce jsou uvedeny klíčové slovo, pod kterým se vyvolá událost a úroveň události. (Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Klíčové slovo pro vyvolání události|úroveň|  
|-----------------------------------|-----------|  
|`ExceptionKeyword` (0x8000)|Upozornění (2)|  
  
 V následující tabulce jsou uvedeny informace o události.  
  
|Událost|ID události|Vyvolá se, když|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|80|Spravovaná výjimka je vyvolána.|  
  
 Následující tabulka zobrazuje data událostí.  
  
|Název pole|Datový typ|Popis|  
|----------------|---------------|-----------------|  
|Typ výjimky|Windows: UnicodeString|Typ výjimky; například `System.NullReferenceException`.|  
|Zpráva o výjimce|Windows: UnicodeString|Zpráva o výjimce skutečný.|  
|EIPCodeThrow|Windows: ukazatele|Ukazatele na instrukci kde došlo k výjimce.|  
|ExceptionHR|Windows: UInt32|Výjimka [HRESULT](https://go.microsoft.com/fwlink/?LinkId=179679).|  
|Příznaky výjimky|Windows: UInt16|0x01: HasInnerException (viz [CLR ETW Events](../../../docs/framework/performance/clr-etw-events.md) dokumentace jazyka Visual Basic).<br /><br /> 0x02: IsNestedException.<br /><br /> 0x04: IsRethrownException.<br /><br /> 0x08: IsCorruptedStateException (vyplývá, že stav procesu je poškozen, naleznete v tématu [zpracování výjimek poškozený stav](https://go.microsoft.com/fwlink/?LinkId=179681) na webové stránce MSDN).<br /><br /> 0x10: IsCLSCompliant (výjimku, která je odvozena z <xref:System.Exception> je kompatibilní se Specifikací CLS; v opačném případě není kompatibilní se Specifikací CLS).|  
|ClrInstanceID|Windows: UInt16|Jedinečné ID instance CLR nebo CoreCLR.|  
  
## <a name="see-also"></a>Viz také  
 [Události Trasování událostí pro Windows v CLR](../../../docs/framework/performance/clr-etw-events.md)
