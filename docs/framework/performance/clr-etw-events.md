---
title: "Události ETW CLR"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CLR ETW events
- ETW, common language runtime
- ETW, CLR events
ms.assetid: ef2b31c3-7426-43e7-9924-92339b96556d
caps.latest.revision: "45"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 17701ee1ddbb1056c9b06b2467c4ce10b91271ff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="clr-etw-events"></a>Události ETW CLR
Témata v této části popisují trasování událostí pro události systému Windows (ETW). Každá událost má přidružené klíčového slova a úrovně, které jsou popsány v [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md) tématu. Modul CLR má dva poskytovatelé pro události:  
  
-   Poskytovatel modulu runtime, který vyvolává události v závislosti na tom, které jsou povolené klíčová slova (kategorie událostí). Poskytovatel modulu runtime CLR GUID je e13c0d23-ccbc-4e12-931b-d9cc2eee27e4.  
  
-   Sekvence daneho poskytovatele, který má speciální používá. Sekvence daneho zprostředkovatel CLR GUID je a669021c-c450-4609-a035-5af59af4df18.  
  
 Další informace o poskytovateli najdete v tématu [CLR ETW – zprostředkovatelé](../../../docs/framework/performance/clr-etw-providers.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Události běhových informací](../../../docs/framework/performance/runtime-information-etw-events.md)  
 Zaznamená informace o modulu runtime, SKU, číslo verze, způsobem, ve kterém byla aktivovaná modul runtime, včetně parametrů příkazového řádku, který byl spuštěn s, identifikátor GUID (pokud existuje) a další relevantní informace.  
  
 [Událost výjimky Thrown_V1](../../../docs/framework/performance/exception-thrown-v1-etw-event.md)  
 Zaznamená informace o výjimkách, které jsou vydány.  
  
 [Kolizní události](../../../docs/framework/performance/contention-etw-events.md)  
 Zaznamená informace o kolizí pro monitorování zámky nebo nativní zámky, které používá modul runtime.  
  
 [Události fondu vláken](../../../docs/framework/performance/thread-pool-etw-events.md)  
 Zaznamená informace o přístup z více vláken fondy pracovních procesů a fondy vláken vstupně-výstupní operace.  
  
 [Události zavaděče](../../../docs/framework/performance/loader-etw-events.md)  
 Zaznamená informace o načítání a uvolnění domény aplikace, sestavení a moduly.  
  
 [Události metod](../../../docs/framework/performance/method-etw-events.md)  
 Zaznamená informace o metodách CLR pro překlad symbol.  
  
 [Události kolekce paměti](../../../docs/framework/performance/garbage-collection-etw-events.md)  
 Zaznamená informace týkající se uvolňování paměti, která vám pomůžou ladění a Diagnostika.  
  
 [JIT – události trasování (CLR)](../../../docs/framework/performance/jit-tracing-etw-events.md)  
 Zaznamená informace o právě za běhu (JIT) vložené a volání tail.  
  
 [Události interoperability](../../../docs/framework/performance/interop-etw-events.md)  
 Zaznamená informace o Microsoft (MSIL intermediate language) se zakázaným inzerováním generování a ukládání do mezipaměti.  
  
 [Události ARM](../../../docs/framework/performance/application-domain-resource-monitoring-arm-etw-events.md)  
 Zachycení podrobné diagnostické informace týkající se stavu služby domény aplikace.  
  
 [Události zabezpečení](../../../docs/framework/performance/security-etw-events.md)  
 Zaznamená informace o silným názvem a ověření Authenticode.  
  
 [Událost zásobníku](../../../docs/framework/performance/stack-etw-event.md)  
 Zaznamená informace, které se používá s jinými událostmi ke generování trasování zásobníku po je aktivována událost.  
  
## <a name="see-also"></a>Viz také  
 [Vylepšení ladění a optimalizace výkonu pomocí trasování událostí pro Windows](http://go.microsoft.com/fwlink/?LinkId=179696)  
 [Blog výkonu Windows](http://go.microsoft.com/fwlink/?LinkId=179509)  
 [Řízení přihlašování rozhraní .NET Framework](../../../docs/framework/performance/controlling-logging.md)  
 [Poskytovatelé Trasování událostí pro Windows v CLR](../../../docs/framework/performance/clr-etw-providers.md)  
 [Klíčová slova a úrovně Trasování událostí pro Windows v CLR](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)  
 [Události Trasování událostí pro Windows v CLR (Common Language Runtime)](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
