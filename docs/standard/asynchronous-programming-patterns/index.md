---
title: Vzory asynchronního programování
ms.date: 10/16/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous design patterns, .NET
- .NET Framework, asynchronous design patterns
ms.assetid: 4ece5c0b-f8fe-4114-9862-ac02cfe5a5d7
ms.openlocfilehash: e1efe9c3eb57f317def91e527506c358eb086679
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160050"
---
# <a name="asynchronous-programming-patterns"></a>Vzory asynchronního programování

Rozhraní .NET poskytuje tři vzory pro provádění asynchronních operací:  

- **Asynchronní vzor založený na úlohách (TAP),** který používá jednu metodu k reprezentaci zahájení a dokončení asynchronní operace. Tap byl zaveden v rozhraní .NET Framework 4. **Je to doporučený přístup k asynchronnímu programování v rozhraní .NET.** [Asynchronní](../../csharp/language-reference/keywords/async.md) a [čekat](../../csharp/language-reference/operators/await.md) klíčová slova v jazyce C# a [Async](../../visual-basic/language-reference/modifiers/async.md) a [Await](../../visual-basic/language-reference/operators/await-operator.md) operátory v jazyce Visual Basic přidat jazykovou podporu pro TAP. Další informace naleznete [v tématu Asynchronní vzor založený na úlohách (TAP).](task-based-asynchronous-pattern-tap.md)  

- **Asynchronní vzor založený na událostech (EAP),** což je starší model založený na událostech pro poskytování asynchronního chování. Vyžaduje metodu, která `Async` má příponu a jednu nebo více `EventArg`událostí, typy delegátů obslužné rutiny událostí a odvozené typy. EAP byl zaveden v rozhraní .NET Framework 2.0. Již se nedoporučuje pro nový vývoj. Další informace naleznete [v tématu Asynchronní vzor založený na událostech (EAP).](event-based-asynchronous-pattern-eap.md)  

- **Vzor asynchronního programovacího modelu (APM)** (nazývaný také <xref:System.IAsyncResult> vzor), <xref:System.IAsyncResult> což je starší model, který používá rozhraní k zajištění asynchronního chování. V tomto vzoru `Begin` vyžadují synchronní `End` operace a `BeginWrite` metody `EndWrite` (například a implementovat operaci asynchronního zápisu). Tento vzor se již nedoporučuje pro nový vývoj. Další informace naleznete [v tématu Asynchronní programovací model (APM)](asynchronous-programming-model-apm.md).  
  
## <a name="comparison-of-patterns"></a>Porovnání vzorů

Pro rychlé porovnání, jak tři vzory model asynchronní `Read` operace, zvažte metodu, která čte zadané množství dat do zadané vyrovnávací paměti začíná na zadaný posun:  
  
```csharp  
public class MyClass  
{  
    public int Read(byte [] buffer, int offset, int count);  
}  
```  

Protějšek TAP této metody by `ReadAsync` vystavit následující jednu metodu:  
  
```csharp
public class MyClass  
{  
    public Task<int> ReadAsync(byte [] buffer, int offset, int count);  
}  
```

Protějšek EAP by vystavit následující sadu typů a členů:  
  
```csharp  
public class MyClass  
{  
    public void ReadAsync(byte [] buffer, int offset, int count);  
    public event ReadCompletedEventHandler ReadCompleted;  
}  
```  
  
Protějšek APM by `BeginRead` `EndRead` vystavit a metody:  
  
```csharp  
public class MyClass  
{  
    public IAsyncResult BeginRead(  
        byte [] buffer, int offset, int count,
        AsyncCallback callback, object state);  
    public int EndRead(IAsyncResult asyncResult);  
}  
```  

## <a name="see-also"></a>Viz také

- [Asynchronní do hloubky](../async-in-depth.md)
- [Asynchronní programování v C #](../../csharp/async.md)
- [Asynchronní programování ve F #](../../fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)
- [Asynchronní programování s asynchronní a čeká (Visual Basic)](../../visual-basic/programming-guide/concepts/async/index.md)
