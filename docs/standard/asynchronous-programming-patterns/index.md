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
ms.openlocfilehash: e399a512d2bee636aec35e008c0632ce9c5fa781
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44068401"
---
# <a name="asynchronous-programming-patterns"></a>Vzory asynchronního programování

Rozhraní .NET Framework poskytuje tři vzory pro provádění asynchronních operací:  
  
- **Asynchronní Programovací Model (APM)** vzor (také nazývané <xref:System.IAsyncResult> vzor), kde asynchronní operace vyžadují `Begin` a `End` metody (například `BeginWrite` a `EndWrite` pro asynchronní operace zápisu). Tento model už se nedoporučuje pro vývoj nových projektů. Další informace najdete v tématu [asynchronního programovacího modelu (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md).  
  
- **Událost asynchronní vzor založený (EAP)**, což vyžaduje metodu, která má `Async` příponu a také vyžaduje jeden nebo více událostí, typy delegátu obslužné rutiny událostí, a `EventArg`-odvozené typy. EAP byla zavedena v rozhraní .NET Framework 2.0. Doporučuje se už pro vývoj nových projektů. Další informace najdete v tématu [události asynchronní vzor založený (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).  
  
- **Založený na úlohách asynchronního vzoru (TAP)**, který používá jedinou metodu k reprezentaci zahájení a dokončení asynchronní operace. Klepněte na byla zavedena v rozhraní .NET Framework 4 a je doporučený postup pro asynchronní programování v rozhraní .NET Framework. [Asynchronní](~/docs/csharp/language-reference/keywords/async.md) a [await](~/docs/csharp/language-reference/keywords/await.md) klíčová slova v jazyce C# a [asynchronní](~/docs/visual-basic/language-reference/modifiers/async.md) a [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) operátory v jazyce Visual Basic přidejte jazyková podpora v nástroji TAP. Další informace najdete v tématu [úkolově orientovanou asynchronní vzor (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).  
  
## <a name="comparing-patterns"></a>Porovnávání vzorů  

Rychlé porovnání jak tři vzory modelu asynchronních operací, vezměte v úvahu `Read` metodu, která načte zadaného množství dat do zadané vyrovnávací paměti, počínaje od určeného posunutí:  
  
```csharp  
public class MyClass  
{  
    public int Read(byte [] buffer, int offset, int count);  
}  
```  
  
APM protějšek této metody by vystavit `BeginRead` a `EndRead` metody:  
  
```csharp  
public class MyClass  
{  
    public IAsyncResult BeginRead(  
        byte [] buffer, int offset, int count,   
        AsyncCallback callback, object state);  
    public int EndRead(IAsyncResult asyncResult);  
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
  
Protějšek TAP by vystavovat následující jedním `ReadAsync` metody:  
  
```csharp  
public class MyClass  
{  
    public Task<int> ReadAsync(byte [] buffer, int offset, int count);  
}  
```  
  
Komplexní informace o protokolu EAP, klepněte na a APM najdete v článku odkazů uvedených v následující části.  
  
## <a name="related-topics"></a>Související témata

| Název | Popis |
| ----- | ----------- |
| [Model asynchronního programování (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) | Popisuje starší verzi modelu, který používá <xref:System.IAsyncResult> rozhraní k poskytování asynchronní chování. Tento model už se nedoporučuje pro vývoj nových projektů. |
| [Asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) | Popisuje starší model pro poskytování asynchronní chování založený na událostech. Tento model už se nedoporučuje pro vývoj nových projektů. |
| [Asynchronní vzor založený na úlohách (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) | Popisuje nový asynchronní vzor založený na <xref:System.Threading.Tasks> oboru názvů. Tento model je doporučený postup pro asynchronní programování v rozhraní .NET Framework 4 a novější verze. |

## <a name="see-also"></a>Viz také:

- [Asynchronní programování v jazyce C#](~/docs/csharp/async.md)   
- [Asynchronní programování v jazyce F #](~/docs/fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)   
- [Asynchronní programování pomocí modifikátoru Async a operátoru Await (Visual Basic)](~/docs/visual-basic/programming-guide/concepts/async/index.md)
