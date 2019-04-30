---
title: Události ETW CLR
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: ef2b31c3-7426-43e7-9924-92339b96556d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cb7520518497b244be8be3751ca8a3063a02717a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788008"
---
# <a name="clr-etw-events"></a>Události ETW CLR
Témata v této části popisují trasování událostí pro Windows (ETW). Každá událost má související klíčového slova a úrovně, které jsou popsány v [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md) tématu. Modul CLR má dva poskytovatelé pro události:  
  
- Zprostředkovatel běhového prostředí, které vyvolává události v závislosti na tom, které jsou povolené klíčová slova (kategorie události). Identifikátor GUID zprostředkovatele CLR runtime je e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.  
  
- Zprostředkovatel doběhu, který má zvláštní účely. Identifikátor GUID zprostředkovatele doběhu modulu CLR je a669021c-c450-4609-a035-5af59af4df18.  
  
 Další informace o poskytovatelích najdete v tématu [CLR ETW – zprostředkovatelé](../../../docs/framework/performance/clr-etw-providers.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Události běhových informací](../../../docs/framework/performance/runtime-information-etw-events.md)  
 Zaznamenává informace o modulu runtime, včetně SKU, číslo verze, způsobem, ve kterém se aktivovala modul runtime, parametry příkazového řádku, který byl spuštěn s GUID (Pokud je k dispozici) a další relevantní informace.  
  
 [Událost výjimky Thrown_V1](../../../docs/framework/performance/exception-thrown-v1-etw-event.md)  
 Zaznamenává informace o výjimkách, které jsou vyvolány.  
  
 [Kolizní události](../../../docs/framework/performance/contention-etw-events.md)  
 Zaznamenává informace o počtu kolizí zámků monitorování nebo nativní zámky, které používá modul runtime.  
  
 [Události fondu vláken](../../../docs/framework/performance/thread-pool-etw-events.md)  
 Zaznamenává informace o vlákně fondy pracovních procesů a fondy vláken vstupně-výstupních operací.  
  
 [Události zavaděče](../../../docs/framework/performance/loader-etw-events.md)  
 Zaznamenává informace o načítání a uvolňování domény aplikace, sestavení a modulů.  
  
 [Události metod](../../../docs/framework/performance/method-etw-events.md)  
 Zaznamenává informace o metodách CLR pro rozlišení symbolů.  
  
 [Události kolekce paměti](../../../docs/framework/performance/garbage-collection-etw-events.md)  
 Zaznamenává informace týkající se uvolňování paměti, které vám pomůžou Diagnostika a ladění.  
  
 [JIT – události trasování (CLR)](../../../docs/framework/performance/jit-tracing-etw-events.md)  
 Zaznamenává informace o just-in-time (JIT) vkládání a volání funkce tail.  
  
 [Události interoperability](../../../docs/framework/performance/interop-etw-events.md)  
 Zaznamenává informace o Microsoft intermediate language (MSIL) zástupné procedury generování a ukládání do mezipaměti.  
  
 [Události ARM](../../../docs/framework/performance/application-domain-resource-monitoring-arm-etw-events.md)  
 Zachycení podrobných diagnostických informací týkajících se stavu domény aplikace.  
  
 [Události zabezpečení](../../../docs/framework/performance/security-etw-events.md)  
 Zaznamenává informace týkající se silným názvem a ověření pomocí technologie Authenticode.  
  
 [Událost zásobníku](../../../docs/framework/performance/stack-etw-event.md)  
 Zaznamenává informace, které slouží ke generování trasování zásobníku, poté, co je vyvolána událost s jinými událostmi.  
  
## <a name="see-also"></a>Viz také:

- [Vylepšení ladění a optimalizace výkonu pomocí trasování událostí pro Windows](https://go.microsoft.com/fwlink/?LinkId=179696)
- [Blog o Windows Performance](https://go.microsoft.com/fwlink/?LinkId=179509)
- [Řízení přihlašování rozhraní .NET Framework](../../../docs/framework/performance/controlling-logging.md)
- [Poskytovatelé Trasování událostí pro Windows v CLR](../../../docs/framework/performance/clr-etw-providers.md)
- [Klíčová slova a úrovně Trasování událostí pro Windows v CLR](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)
- [Události Trasování událostí pro Windows v CLR (Common Language Runtime)](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
