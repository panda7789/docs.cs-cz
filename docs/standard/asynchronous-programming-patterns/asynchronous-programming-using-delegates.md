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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73121736"
---
# <a name="asynchronous-programming-using-delegates"></a>Asynchronní programování pomocí delegátů
Delegáti umožňují volat synchronní metodu asynchronním způsobem. Při volání delegáta synchronně `Invoke` metoda volá cílovou metodu přímo v aktuálním vlákně. `BeginInvoke` Pokud je metoda volána, clr (CLR) společného jazyka zařadí požadavek do fronty a okamžitě se vrátí volajícímu. Cílová metoda se nazývá asynchronně ve vlákně z fondu vláken. Původní vlákno, které odeslal požadavek, je volně pokračovat v provádění souběžně s cílovou metodou. Pokud byla ve volání `BeginInvoke` metody zadána metoda zpětného volání, je při ukončení cílové metody volána metoda zpětného volání. V metodě zpětného `EndInvoke` volání metoda získá vrácenou hodnotu a všechny parametry input/output nebo pouze pro výstup. Pokud při volání `BeginInvoke`není zadána `EndInvoke` žádná metoda zpětného `BeginInvoke`volání , lze volat z vlákna, které volalo .  
  
> [!IMPORTANT]
> Kompilátory by měly vyzařovat delegované třídy s `Invoke`, `BeginInvoke`a `EndInvoke` metodami pomocí podpisu delegáta určeného uživatelem. Metody `BeginInvoke` `EndInvoke` a by měly být dekorovány jako nativní. Vzhledem k tomu, že tyto metody jsou označeny jako nativní, CLR automaticky poskytuje implementaci v době načítání třídy. Nakladač zajišťuje, že nejsou přepsány.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Asynchronní volání synchronních metod](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 Popisuje použití delegátů provést asynchronní volání běžné metody a poskytuje jednoduché příklady kódu, které ukazují čtyři způsoby čekání na asynchronní volání vrátit.  
  
## <a name="related-sections"></a>Související oddíly  
 [Asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 Popisuje asynchronní programování pomocí rozhraní .NET Framework.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Delegate>
