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
ms.openlocfilehash: bad5372af1d771dc93a20e61090ef84126f3e1eb
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48033321"
---
# <a name="asynchronous-programming-using-delegates"></a>Asynchronní programování pomocí delegátů
Delegáty umožňují volání v asynchronním režimu synchronní metody. Při volání delegáta synchronně, `Invoke` metoda volá metodu cíl přímo u aktuálního vlákna. Pokud `BeginInvoke` metoda je volána, common language runtime (CLR) zařadí do fronty požadavek a okamžitě vrací volajícímu. Cílové metody je volána asynchronně na vlákně z fondu podprocesů. Původní podproces, který danou žádost odeslal, je zdarma má pokračovat provedením souběžně s cílovou metodu. Pokud byl zadán metody zpětného volání při volání `BeginInvoke` metody, metody zpětného volání je volána, když skončí cílové metody. V metodě zpětného volání `EndInvoke` metoda získá návratovou hodnotu a vstup/výstup nebo jen pro výstupní parametry. Pokud žádná metoda zpětného volání je zadán při volání metody `BeginInvoke`, `EndInvoke` lze volat z vlákna, která se nazývá `BeginInvoke`.  
  
> [!IMPORTANT]
>  Kompilátory by měly vydávat třídy delegáta s `Invoke`, `BeginInvoke`, a `EndInvoke` metod pomocí delegáta specifikovaných uživatelem. `BeginInvoke` a `EndInvoke` metody by měly být doplněny jako nativní. Protože tyto metody jsou označeny jako nativní, modul CLR automaticky poskytuje implementaci v okamžiku načtení třídy. Zavaděč zajistí, že nejsou přepsána.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Asynchronní volání synchronních metod](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 Tento článek popisuje použití delegátů pro asynchronní volání běžné metody a poskytuje příklady jednoduchého kódu, které ukazují čtyři způsoby čekání na asynchronní volání k vrácení.  
  
## <a name="related-sections"></a>Související oddíly  
 [Asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 Popisuje asynchronní programování s rozhraním .NET Framework.  
  
## <a name="see-also"></a>Viz také:

* <xref:System.Delegate>
