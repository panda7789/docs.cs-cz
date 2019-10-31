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
ms.openlocfilehash: 4e17e6a96a12b705cf455d70add7e12a30f5fa90
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121736"
---
# <a name="asynchronous-programming-using-delegates"></a>Asynchronní programování pomocí delegátů
Delegáti umožňují volat synchronní metodu asynchronním způsobem. Při synchronním volání delegáta volá metoda `Invoke` cílovou metodu přímo v aktuálním vlákně. Pokud je volána metoda `BeginInvoke`, modul CLR (Common Language Runtime) zařadí do fronty požadavek a okamžitě se vrátí volajícímu. Cílová metoda se volá asynchronně ve vlákně z fondu vláken. Původní vlákno, které odeslalo požadavek, je zdarma pro pokračování v provádění paralelně s cílovou metodou. Pokud byla metoda zpětného volání určena při volání metody `BeginInvoke`, je volána metoda zpětného volání při ukončení cílové metody. V metodě zpětného volání získá metoda `EndInvoke` návratovou hodnotu a všechny vstupně-výstupní nebo výstupní parametry. Pokud není zadána žádná metoda zpětného volání při volání `BeginInvoke`, `EndInvoke` lze volat z vlákna, které se nazývá `BeginInvoke`.  
  
> [!IMPORTANT]
> Kompilátory by měly generovat třídy delegátů pomocí `Invoke`, `BeginInvoke`a `EndInvoke` metod pomocí podpisu delegáta zadaného uživatelem. Metody `BeginInvoke` a `EndInvoke` by měly být dekorované jako nativní. Vzhledem k tomu, že jsou tyto metody označeny jako nativní, modul CLR automaticky poskytne implementaci v době načítání třídy. Zavaděč zajišťuje, že nejsou přepsány.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Asynchronní volání synchronních metod](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 Popisuje použití delegátů k asynchronnímu volání běžných metod a poskytuje jednoduché příklady kódu, které znázorňují čtyři způsoby čekání na vrácení asynchronního volání.  
  
## <a name="related-sections"></a>Související oddíly  
 [Asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 Popisuje asynchronní programování s .NET Framework.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Delegate>
