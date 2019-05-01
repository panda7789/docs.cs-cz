---
title: Vzory asynchronního programování
ms.date: 10/16/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous design patterns, .NET
- .NET Framework, asynchronous design patterns
ms.assetid: 4ece5c0b-f8fe-4114-9862-ac02cfe5a5d7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 50d76aef201fead37923a65cfeead16638b09842
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62031171"
---
# <a name="asynchronous-programming-patterns"></a>Vzory asynchronního programování

.NET poskytuje tři vzory pro provádění asynchronních operací:  

- **Založený na úlohách asynchronního vzoru (TAP)**, který používá jedinou metodu k reprezentaci zahájení a dokončení asynchronní operace. Klepněte na byla zavedena v rozhraní .NET Framework 4. **Je doporučený postup pro asynchronní programování v rozhraní .NET.** [Asynchronní](~/docs/csharp/language-reference/keywords/async.md) a [await](~/docs/csharp/language-reference/keywords/await.md) klíčových slov v C# a [asynchronní](~/docs/visual-basic/language-reference/modifiers/async.md) a [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) operátory v jazyce Visual Basic přidejte jazyková podpora v nástroji TAP. Další informace najdete v tématu [úkolově orientovanou asynchronní vzor (TAP)](task-based-asynchronous-pattern-tap.md).  

- **Událost asynchronní vzor založený (EAP)**, který je založený na událostech starší model pro poskytování asynchronní chování. Vyžaduje metodu, která má `Async` příponu a jeden nebo více událostí, typy delegátu obslužné rutiny událostí, a `EventArg`-odvozené typy. EAP byla zavedena v rozhraní .NET Framework 2.0. Doporučuje se už pro vývoj nových projektů. Další informace najdete v tématu [události asynchronní vzor založený (EAP)](event-based-asynchronous-pattern-eap.md).  

- **Asynchronního programovacího modelu (APM)** vzor (také nazývané <xref:System.IAsyncResult> vzor), která je starší verze modelu, který používá <xref:System.IAsyncResult> rozhraní k poskytování asynchronní chování. V tomto vzoru synchronní operace vyžadují `Begin` a `End` metod (například `BeginWrite` a `EndWrite` implementace operace asynchronní zápis). Tento model už se nedoporučuje pro vývoj nových projektů. Další informace najdete v tématu [asynchronního programovacího modelu (APM)](asynchronous-programming-model-apm.md).  
  
## <a name="comparison-of-patterns"></a>Porovnávání vzorů

Rychlé porovnání jak tři vzory modelu asynchronních operací, vezměte v úvahu `Read` metodu, která načte zadaného množství dat do zadané vyrovnávací paměti, počínaje od určeného posunutí:  
  
```csharp  
public class MyClass  
{  
    public int Read(byte [] buffer, int offset, int count);  
}  
```  

TAP protějšek této metody by vystavovat následující jedním `ReadAsync` metody:  
  
```csharp
public class MyClass  
{  
    public Task<int> ReadAsync(byte [] buffer, int offset, int count);  
}  
```

Následující sada typů a členů by vystavit protějšek protokolu EAP:  
  
```csharp  
public class MyClass  
{  
    public void ReadAsync(byte [] buffer, int offset, int count);  
    public event ReadCompletedEventHandler ReadCompleted;  
}  
```  
  
APM protějšek by vystavit `BeginRead` a `EndRead` metody:  
  
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

- [Asynchronní do hloubky](../async-in-depth.md)
- [Asynchronní programování v jazyce C#](~/docs/csharp/async.md)
- [Asynchronní programování vF#](~/docs/fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)
- [Asynchronní programování pomocí modifikátoru Async a operátoru Await (Visual Basic)](~/docs/visual-basic/programming-guide/concepts/async/index.md)
