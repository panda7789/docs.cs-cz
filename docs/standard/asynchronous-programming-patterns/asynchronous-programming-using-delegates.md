---
title: "Asynchronní programování pomocí delegátů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 596d2be26318b782423653b4eb3f43c1f9fc4b92
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="asynchronous-programming-using-delegates"></a>Asynchronní programování pomocí delegátů
Delegáti umožňují volání v asynchronním režimu synchronní metody. Při volání delegáta synchronně, `Invoke` metoda volá metodu cíl přímo na aktuální vlákno. Pokud `BeginInvoke` metoda je volána, common language runtime (CLR) zařadí do fronty požadavek a vrátí okamžitě volajícímu. Cílové metody se asynchronně volá na vlákno z fondu vláken. Původní podproces, který odeslal požadavek, je zdarma chcete pokračovat v provádění paralelně s cílové metody. Pokud metoda zpětného volání byla zadána ve volání `BeginInvoke` metoda, metoda zpětného volání je volána při ukončení cílové metody. Metoda zpětného volání `EndInvoke` metoda získá návratovou hodnotu a vstupu a výstupu nebo jen výstupní parametry. Pokud žádná metoda zpětného volání je zadána při volání metody `BeginInvoke`, `EndInvoke` lze volat z vlákna, která se nazývá `BeginInvoke`.  
  
> [!IMPORTANT]
>  Kompilátory by měl emitování delegát třídy s `Invoke`, `BeginInvoke`, a `EndInvoke` metod pomocí delegáta specifikovaných uživatelem. `BeginInvoke` a `EndInvoke` metody by měla být dekorované jako nativní. Protože tyto metody jsou označeny jako nativní, modul CLR automaticky poskytuje implementaci při načítání, třída. Zavaděč zajistí, že nejsou přepsat.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Asynchronní volání synchronních metod](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 Popisuje použití delegátů pro asynchronní volání do metody obyčejnou a obsahuje příklady jednoduchého kódu, které se zobrazí čtyři způsoby čekání na asynchronní volání vrátit.  
  
## <a name="related-sections"></a>Související oddíly  
 [Asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 Popisuje asynchronní programování s rozhraním .NET Framework.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Delegate>
