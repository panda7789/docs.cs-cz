---
title: "where (omezení obecného typu) (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.assetid: d7aa871b-0714-416a-bab2-96f87ada4310
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f2b7b159689aa771d3f9d59e3b1dd340c85b1d79
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="where-generic-type-constraint-c-reference"></a>where (omezení obecného typu) (Referenční dokumentace jazyka C#)
V definici obecného typu `where` klauzule slouží k určení omezení typy, které lze použít jako argumenty pro definované v deklaraci obecný parametr typu. Můžou například deklarovat obecná třída `MyGenericClass`, tak, že parametr typu `T` implementuje <xref:System.IComparable%601> rozhraní:  
  
```csharp  
public class MyGenericClass<T> where T:IComparable { }  
```  
  
> [!NOTE]
>  Další informace o where klauzule ve výrazu dotazu, najdete v části [kde klauzule](../../../csharp/language-reference/keywords/where-clause.md).  
  
 Kromě omezení rozhraní `where` klauzule může obsahovat omezení základní třídu, která uvádí, že typ musí mít zadaný třídy jako základní třída (nebo být třídy sám sebe) aby bylo možné použít jako argument typu pro obecného typu. Pokud se používá takové omezení, musí být před jiná omezení u tohoto typu parametru.  
  
 [!code-csharp[csrefKeywordsContextual#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_1.cs)]  
  
 `where` Klauzule může také zahrnovat omezení konstruktor. Je možné vytvořit instanci typu parametr pomocí operátor new; ale, aby bylo možné učinit parametr typu musí být omezen omezením konstruktor `new()`. [New() omezení](../../../csharp/language-reference/keywords/new-constraint.md) umožňuje kompilátoru vědět, že musí mít přístupné některý typ argument zadaný bez parametrů--nebo--výchozí konstruktor. Příklad:  
  
 [!code-csharp[csrefKeywordsContextual#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_2.cs)]  
  
 `new()` Omezení, zobrazí se v poslední `where` klauzule.  
  
 S více typů parametrů, použijte jednu `where` klauzuli pro každý parametr typu, například:  
  
 [!code-csharp[csrefKeywordsContextual#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_3.cs)]  
  
 Můžete také připojit omezení zadání parametrů Obecné metody takto:  
  
```csharp  
public bool MyMethod<T>(T t) where T : IMyInterface { }  
```  
  
 Všimněte si, že syntaxe pro popis typu parametru omezení delegáti je stejná jako u metody:  
  
```csharp  
delegate T MyDelegate<T>() where T : new()  
```  
  
 Informace pro obecné delegáty najdete v tématu [obecní delegáti](../../../csharp/programming-guide/generics/generic-delegates.md).  
  
 Podrobnosti o syntaxi a použití omezení najdete v tématu [omezení parametrů typů](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Úvod do obecných typů](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [New – omezení](../../../csharp/language-reference/keywords/new-constraint.md)  
 [Omezení parametrů typů](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)
