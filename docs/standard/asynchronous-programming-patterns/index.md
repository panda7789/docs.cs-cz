---
title: Vzorce asynchronního programování
ms.date: 10/16/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous design patterns, .NET
- .NET Framework, asynchronous design patterns
ms.assetid: 4ece5c0b-f8fe-4114-9862-ac02cfe5a5d7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36798fabcd42cf7e04b0a6f288736503eecad88b
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2019
ms.locfileid: "70169128"
---
# <a name="asynchronous-programming-patterns"></a>Vzorce asynchronního programování

.NET nabízí tři vzory pro provádění asynchronních operací:  

- **Asynchronní vzor založený na úlohách (klepněte)** , který používá jedinou metodu představující zahájení a dokončení asynchronní operace. Klepněte na zavedený .NET Framework 4. **Je to doporučený přístup k asynchronnímu programování v rozhraní .NET.** Klíčová slova [](../../csharp/language-reference/operators/await.md) [Async](../../csharp/language-reference/keywords/async.md) a await C# v a operátory [Async](../../visual-basic/language-reference/modifiers/async.md) a [await](../../visual-basic/language-reference/operators/await-operator.md) v Visual Basic přidat jazykovou podporu pro klepněte. Další informace najdete v tématu [asynchronní vzor založený na úlohách (klepněte)](task-based-asynchronous-pattern-tap.md).  

- Asynchronní vzor založený na událostech **(EAP)** , což je starší model založený na událostech pro zajištění asynchronního chování. Vyžaduje metodu, která má `Async` příponu a jednu nebo více událostí, typy delegátů události a `EventArg`odvozené typy. Protokol EAP byl představený v .NET Framework 2,0. Už se nedoporučuje pro nový vývoj. Další informace najdete v tématu [asynchronní vzor založený na událostech (EAP)](event-based-asynchronous-pattern-eap.md).  

- Vzor **asynchronního programovacího modelu (APM)** (označuje <xref:System.IAsyncResult> se také jako vzor), což je starší <xref:System.IAsyncResult> model, který používá rozhraní k zajištění asynchronního chování. `Begin` V tomto vzoru vyžadují synchronní operace a `End` `BeginWrite` metody (například a `EndWrite` k implementaci asynchronní operace zápisu). Tento model se už nedoporučuje pro nový vývoj. Další informace najdete v tématu [asynchronní programovací model (APM)](asynchronous-programming-model-apm.md).  
  
## <a name="comparison-of-patterns"></a>Porovnání vzorů

Chcete-li rychle porovnat, jak tři vzory modelují asynchronní operace, zvažte `Read` metodu, která načte zadané množství dat do zadané vyrovnávací paměti počínaje zadaným posunem:  
  
```csharp  
public class MyClass  
{  
    public int Read(byte [] buffer, int offset, int count);  
}  
```  

Klepnutí na protějšek této metody vystaví následující jedinou `ReadAsync` metodu:  
  
```csharp
public class MyClass  
{  
    public Task<int> ReadAsync(byte [] buffer, int offset, int count);  
}  
```

Protějšek protokolu EAP vystaví následující sadu typů a členů:  
  
```csharp  
public class MyClass  
{  
    public void ReadAsync(byte [] buffer, int offset, int count);  
    public event ReadCompletedEventHandler ReadCompleted;  
}  
```  
  
Protějšek APM by vystavoval `BeginRead` metody `EndRead` a:  
  
```csharp  
public class MyClass  
{  
    public IAsyncResult BeginRead(  
        byte [] buffer, int offset, int count,   
        AsyncCallback callback, object state);  
    public int EndRead(IAsyncResult asyncResult);  
}  
```  

## <a name="see-also"></a>Viz také:

- [Asynchronní v hloubkě](../async-in-depth.md)
- [Asynchronní programování vC#](../../csharp/async.md)
- [Asynchronní programování vF#](../../fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)
- [Asynchronní programování s modifikátorem Async a operátoru Await (Visual Basic)](../../visual-basic/programming-guide/concepts/async/index.md)
