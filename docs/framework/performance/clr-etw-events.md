---
title: Události ETW CLR
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: ef2b31c3-7426-43e7-9924-92339b96556d
ms.openlocfilehash: e879dcf385acbc522c0a3573cfa374550ea23333
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77504134"
---
# <a name="clr-etw-events"></a>Události ETW CLR
Témata v této části popisují události trasování událostí pro Windows (ETW). Každá událost má přidružené klíčové slovo a úroveň, které jsou popsány v tématu [klíčová slova ETW a úrovně CLR](clr-etw-keywords-and-levels.md) . CLR má dva poskytovatele pro události:  
  
- Zprostředkovatel modulu runtime, který vyvolává události v závislosti na tom, která klíčová slova (kategorie událostí) jsou povolena. Identifikátor GUID zprostředkovatele modulu runtime CLR je e13c0d23-CCBC-4e12-931B-d9cc2eee27e4.  
  
- Poskytovatel doběhu, který má použití pro zvláštní účely. Identifikátor GUID zprostředkovatele doběhu CLR je A669021C-C450-4609-A035-5AF59AF4DF18.  
  
 Další informace o poskytovatelích najdete v tématu [Zprostředkovatelé CLR ETW](clr-etw-providers.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Události běhových informací](runtime-information-etw-events.md)  
 Zachycuje informace o modulu runtime, včetně SKU, čísla verze, způsobu, jakým byl aktivován modul runtime, parametry příkazového řádku, se kterými bylo spuštěno, identifikátor GUID (je-li k dispozici) a další relevantní informace.  
  
 [Událost výjimky Thrown_V1](exception-thrown-v1-etw-event.md)  
 Zachycuje informace o vyvolaných výjimkách.  
  
 [Kolizní události](contention-etw-events.md)  
 Zachycuje informace o sporu pro zámky monitoru nebo nativní zámky, které používá modul runtime.  
  
 [Události fondu vláken](thread-pool-etw-events.md)  
 Zachycuje informace o fondech pracovních vláken a fondech vláken v/v.  
  
 [Události zavaděče](loader-etw-events.md)  
 Zachycuje informace o načítání a uvolňování aplikačních domén, sestavení a modulů.  
  
 [Události metod](method-etw-events.md)  
 Zachycuje informace o metodách CLR pro rozlišení symbolů.  
  
 [Události kolekce paměti](garbage-collection-etw-events.md)  
 Zachycuje informace týkající se uvolňování paměti, které vám pomůžou diagnostikovat a ladit.  
  
 [JIT – události trasování (CLR)](jit-tracing-etw-events.md)  
 Zachycuje informace o vkládání za běhu a volání funkce tail.  
  
 [Události interoperability](interop-etw-events.md)  
 Zachycuje informace o generování a ukládání zástupných procedur v jazyce MSIL (Microsoft Intermediate Language).  
  
 [Události ARM](application-domain-resource-monitoring-arm-etw-events.md)  
 Zachycuje podrobné diagnostické informace o stavu domény aplikace.  
  
 [Události zabezpečení](security-etw-events.md)  
 Zachycuje informace o silném názvu a ověřování Authenticode.  
  
 [Událost zásobníku](stack-etw-event.md)  
 Zachycuje informace, které se používají s jinými událostmi k vygenerování trasování zásobníku po vyvolání události.  
  
## <a name="see-also"></a>Viz také

- [Vylepšení ladění a optimalizace výkonu pomocí ETW](https://docs.microsoft.com/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw)
- [Řízení přihlašování rozhraní .NET Framework](controlling-logging.md)
- [Poskytovatelé Trasování událostí pro Windows v CLR](clr-etw-providers.md)
- [Klíčová slova a úrovně Trasování událostí pro Windows v CLR](clr-etw-keywords-and-levels.md)
- [Události Trasování událostí pro Windows v CLR (Common Language Runtime)](etw-events-in-the-common-language-runtime.md)
