---
title: Asynchronní programování pomocí delegátů
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- BeginInvoke method
- asynchronous programming, delegates
- asynchronous delegates
- calling synchronous methods in asynchronous manner
- EndInvoke method
- calling asynchronous methods
- delegates [.NET Framework], asynchronous
- synchronous calling in asynchronous manner
ms.assetid: 38a345ca-6963-4436-9608-5c9defef9c64
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce77e57eb049c031ed506e8812fff59ba97a978e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950865"
---
# <a name="asynchronous-programming-using-delegates"></a>Asynchronní programování pomocí delegátů
Delegáti umožňují volat synchronní metodu asynchronním způsobem. Při synchronním `Invoke` volání delegáta metoda volá cílovou metodu přímo v aktuálním vlákně. Pokud je `BeginInvoke` metoda volána, modul CLR (Common Language Runtime) zařadí do fronty požadavek a okamžitě se vrátí volajícímu. Cílová metoda se volá asynchronně ve vlákně z fondu vláken. Původní vlákno, které odeslalo požadavek, je zdarma pro pokračování v provádění paralelně s cílovou metodou. Pokud byla metoda zpětného volání určena při volání `BeginInvoke` metody, je volána metoda zpětného volání při ukončení cílové metody. V metodě `EndInvoke` zpětného volání metoda získá vrácenou hodnotu a všechny vstupní/výstupní nebo výstupní parametry. Pokud při volání `BeginInvoke`není zadána žádná metoda zpětného `EndInvoke` volání, lze ji volat z vlákna, `BeginInvoke`které je voláno.  
  
> [!IMPORTANT]
> Kompilátory by měly generovat třídy delegátů pomocí `Invoke`metod `EndInvoke` , `BeginInvoke`a pomocí podpisu delegáta zadaného uživatelem. Metody `BeginInvoke` a`EndInvoke` by měly být dekorované jako nativní. Vzhledem k tomu, že jsou tyto metody označeny jako nativní, modul CLR automaticky poskytne implementaci v době načítání třídy. Zavaděč zajišťuje, že nejsou přepsány.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Asynchronní volání synchronních metod](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 Popisuje použití delegátů k asynchronnímu volání běžných metod a poskytuje jednoduché příklady kódu, které znázorňují čtyři způsoby čekání na vrácení asynchronního volání.  
  
## <a name="related-sections"></a>Související oddíly  
 [Asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 Popisuje asynchronní programování s .NET Framework.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Delegate>
