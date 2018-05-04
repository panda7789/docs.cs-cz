---
title: Vzory asynchronního programování
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous design patterns, .NET Framework
- .NET Framework, asynchronous design patterns
ms.assetid: 4ece5c0b-f8fe-4114-9862-ac02cfe5a5d7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 86ed48361e0868d9e2fa2b79b1c5fa8955018bef
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="asynchronous-programming-patterns"></a>Vzory asynchronního programování

Rozhraní .NET Framework poskytuje tři vzory pro provádění asynchronní operace:  
  
- Asynchronní vzor programovací Model (APM) (také nazývané <xref:System.IAsyncResult> vzor), které vyžadují asynchronních operací `Begin` a `End` metody (například `BeginWrite` a `EndWrite` pro operace asynchronní zápis). Tento vzor již není doporučeno pro nový vývoj. Další informace najdete v tématu [asynchronní programování modelu (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md).  
  
- Na základě událostí asynchronní vzor (EAP), který vyžaduje metodu, která má `Async` přípona a také vyžaduje jeden nebo více událostí, typy delegáta obslužných rutin událostí, a `EventArg`-odvozených typů. EAP byla zavedena v rozhraní .NET Framework 2.0. Doporučuje se už pro nový vývoj. Další informace najdete v tématu [na základě událostí asynchronní vzor (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).  
  
- Založený na úlohách asynchronní vzor (TAP), který používá jedinou metodu k reprezentaci na zahájení a ukončení asynchronní operace. Klepněte na byla zavedena v rozhraní .NET Framework 4 a je doporučeným přístupem k asynchronní programování v rozhraní .NET Framework. [Asynchronní](~/docs/csharp/language-reference/keywords/async.md) a [await](~/docs/csharp/language-reference/keywords/await.md) klíčová slova v jazyce C# a [asynchronní](~/docs/visual-basic/language-reference/modifiers/async.md) a [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) jazyková podpora pro klepněte na přidat operátory v jazyce Visual Basic. Další informace najdete v tématu [založený na úlohách asynchronní vzor (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).  
  
## <a name="comparing-patterns"></a>Porovnávání vzorů  

Rychlé porovnání jak jsou tři vzory modelu asynchronních operací, vezměte v úvahu `Read` metoda, která načte zadaného množství dat do zadané začínající na zadaný posun vyrovnávací paměti:  
  
```csharp  
public class MyClass  
{  
    public int Read(byte [] buffer, int offset, int count);  
}  
```  
  
APM protějšku této metody by vystavit `BeginRead` a `EndRead` metody:  
  
```csharp  
public class MyClass  
{  
    public IAsyncResult BeginRead(  
        byte [] buffer, int offset, int count,   
        AsyncCallback callback, object state);  
    public int EndRead(IAsyncResult asyncResult);  
}  
```  
  
EAP protějšku by vystavit následující sadu typy a členy:  
  
```csharp  
public class MyClass  
{  
    public void ReadAsync(byte [] buffer, int offset, int count);  
    public event ReadCompletedEventHandler ReadCompleted;  
}  
```  
  
Klepněte na protějšku by vystavit následující jedním `ReadAsync` metoda:  
  
```csharp  
public class MyClass  
{  
    public Task<int> ReadAsync(byte [] buffer, int offset, int count);  
}  
```  
  
Komplexní diskuzi o klepněte na APM a EAP najdete v části odkazů uvedených v následující části.  
  
## <a name="related-topics"></a>Související témata

| Název | Popis |
| ----- | ----------- |
| [Model asynchronního programování (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) | Popisuje starší model, který používá <xref:System.IAsyncResult> rozhraní zajistit asynchronní chování. Tento model již není doporučeno pro nový vývoj. |
| [Asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) | Popisuje starší verze modelu pro zajištění asynchronní chování na základě událostí. Tento model již není doporučeno pro nový vývoj. |
| [Asynchronní vzor založený na úlohách (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) | Popisuje nové asynchronní vzor na základě <xref:System.Threading.Tasks> oboru názvů. Tento model je doporučeným přístupem k asynchronní programování v rozhraní .NET Framework 4 a novější verze. |

## <a name="see-also"></a>Viz také

[Asynchronní programování v jazyce C#](~/docs/csharp/async.md)   
[Asynchronní programování v F #](~/docs/fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)   
[Asynchronní programování pomocí modifikátoru Async a operátoru Await (Visual Basic)](~/docs/visual-basic/programming-guide/concepts/async/index.md)
