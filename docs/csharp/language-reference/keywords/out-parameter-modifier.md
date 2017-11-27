---
title: "out – modifikátor parametrů (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- parameters [C#], out
- out parameters [C#]
ms.assetid: 3fce0dc5-03f4-4faa-bd61-36c41bc6baf1
caps.latest.revision: "9"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 68ef554f95fe71f925cfa22cc49758cec3da237e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="out-parameter-modifier-c-reference"></a>out – modifikátor parametrů (Referenční dokumentace jazyka C#)
`out` – Klíčové slovo způsobí, že argumenty předávané odkazem. Je třeba [ref](../../../csharp/language-reference/keywords/ref.md) – klíčové slovo, vyjma toho, že `ref` vyžaduje, aby před předáním iniciována proměnnou. Používat `out` nutné explicitně zadat parametr definici metody a volání metody `out` – klíčové slovo. Příklad:  
  
 [!code-csharp[cs-out-keyword](../../../../samples/snippets/csharp/language-reference/keywords/out/out-1.cs)]  

> [!NOTE] 
> `out` – Klíčové slovo lze také s parametr obecného typu k určení, že parametr typu je kovariant. Další informace o použití `out` – klíčové slovo v tomto kontextu, najdete v části [out (generický modifikátor)](../../../csharp/language-reference/keywords/out-generic-modifier.md).
  
 Proměnné předány jako `out` argumenty není nutné inicializovat před předáním ve volání metody. Je však potřeba přiřadit hodnotu, než vrátí metoda zavolat metodu.  
  
 I když `ref` a `out` klíčová slova způsobit různé chování, nejsou považovány za součást podpis metody v době kompilace. Proto metody nemohou být přetíženy, pokud je jediným rozdílem je, že jedna metoda má `ref` argument a dalších trvá `out` argument. Například následující kód, nebude kompilace:  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on ref and out".
    public void SampleMethod(out int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
Přetížení je právní, ale pokud jedna metoda má `ref` nebo `out` argument a dalších používá ani takto:  
  
 [!code-csharp[csrefKeywordsMethodParams#3](../../../../samples/snippets/csharp/language-reference/keywords/out/out-3.cs)]  
  
 Vlastnosti nejsou proměnné a proto ji nelze předat jako `out` parametry.  
  
 Informace o předávání polí najdete v tématu [předávání polí pomocí parametrů ref a out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).  
  
 Nelze použít `ref` a `out` klíčová slova pro následující typy metod:  
  
-   Asynchronní metody, které definují pomocí [asynchronní](../../../csharp/language-reference/keywords/async.md) modifikátor.  
  
-   Iterator metody, které zahrnují [yield vrátit](../../../csharp/language-reference/keywords/yield.md) nebo `yield break` příkaz.  

## <a name="declaring-out-arguments"></a>Deklarování `out` argumenty   

 Deklarování metodu s `out` argumenty je užitečné, když chcete metody, která vrátí více hodnot. Následující příklad používá `out` vrátit tří proměnných pomocí volání jedné metody. Všimněte si, že třetí argument je přiřazen na hodnotu null. To umožňuje metody volitelně návratové hodnoty.  
  
 [!code-csharp[csrefKeywordsMethodParams#4](../../../../samples/snippets/csharp/language-reference/keywords/out/out-4.cs)]  

 [Zkuste vzor](/visualstudio/code-quality/ca1021-avoid-out-parameters#try-pattern-methods.md) zahrnuje vrácení `bool` znamená, zda operace byla úspěšná a se nezdařilo a vrácení hodnoty vytvořeného operací v `out` argument. Počet analýza metody, jako [DateTime.TryParse](xref:System.DateTime.TryParse(System.String,System.DateTime@)) metoda, použijte tento vzor.
   
## <a name="calling-a-method-with-an-out-argument"></a>Volání metody s `out` argument

V jazyce C# 6 a starší, před předáváme jako třeba deklarovat proměnnou v samostatný příkaz `out` argument. Následující příklad deklaruje proměnné s názvem `number` předtím, než je předán [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) metoda, která se pokusí převést řetězec na číslo.

 [!code-csharp[csrefKeywordsMethodParams#5](../../../../samples/snippets/csharp/language-reference/keywords/out/out-5.cs)]  

Od verze jazyka C# 7, můžou deklarovat `out` proměnné v seznamu argumentů volání metody, a nikoli v samostatných deklarace proměnné. To vytváří kompaktnější a čitelné kódu a taky brání nechtěně přiřazení hodnoty proměnné před volání metody. Následující příklad je jako předchozí příklad, s tím rozdílem, že definuje `number` proměnné ve volání [Int32.TryParse](xref:System.Int32.TryParse(System.String,System.Int32@)) metoda.

 [!code-csharp[csrefKeywordsMethodParams#6](../../../../samples/snippets/csharp/language-reference/keywords/out/out-6.cs)]  
   
V předchozím příkladu `number` proměnné je silného typu jako `int`. Implicitně typované lokální proměnné a můžete také deklarovat, stejně jako v následujícím příkladu.

 [!code-csharp[csrefKeywordsMethodParams#7](../../../../samples/snippets/csharp/language-reference/keywords/out/out-7.cs)]  
   
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Parametry metody](../../../csharp/language-reference/keywords/method-parameters.md)
