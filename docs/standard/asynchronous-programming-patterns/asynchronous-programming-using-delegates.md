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
ms.openlocfilehash: 82e0a57c3d8e180456aed48886e38ca466db16c8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289964"
---
# <a name="asynchronous-programming-using-delegates"></a>Asynchronní programování pomocí delegátů
Delegáti umožňují volat synchronní metodu asynchronním způsobem. Při synchronním volání delegáta `Invoke` metoda volá cílovou metodu přímo v aktuálním vlákně. Pokud `BeginInvoke` je metoda volána, modul CLR (Common Language Runtime) zařadí do fronty požadavek a okamžitě se vrátí volajícímu. Cílová metoda se volá asynchronně ve vlákně z fondu vláken. Původní vlákno, které odeslalo požadavek, je zdarma pro pokračování v provádění paralelně s cílovou metodou. Pokud byla metoda zpětného volání určena při volání `BeginInvoke` metody, je volána metoda zpětného volání při ukončení cílové metody. V metodě zpětného volání `EndInvoke` Metoda získá vrácenou hodnotu a všechny vstupní/výstupní nebo výstupní parametry. Pokud při volání není zadána žádná metoda zpětného volání `BeginInvoke` , `EndInvoke` lze ji volat z vlákna, které je voláno `BeginInvoke` .  
  
> [!IMPORTANT]
> Kompilátory by měly generovat třídy delegátů pomocí `Invoke` `BeginInvoke` metod, a `EndInvoke` pomocí podpisu delegáta zadaného uživatelem. `BeginInvoke`Metody a `EndInvoke` by měly být dekorované jako nativní. Vzhledem k tomu, že jsou tyto metody označeny jako nativní, modul CLR automaticky poskytne implementaci v době načítání třídy. Zavaděč zajišťuje, že nejsou přepsány.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Asynchronní volání synchronních metod](calling-synchronous-methods-asynchronously.md)  
 Popisuje použití delegátů k asynchronnímu volání běžných metod a poskytuje jednoduché příklady kódu, které znázorňují čtyři způsoby čekání na vrácení asynchronního volání.  
  
## <a name="related-sections"></a>Související oddíly  
 [Asynchronní vzor založený na událostech (EAP)](event-based-asynchronous-pattern-eap.md)  
 Popisuje asynchronní programování s .NET Framework.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Delegate>
