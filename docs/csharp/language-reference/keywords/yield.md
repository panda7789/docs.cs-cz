---
title: "yield (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- yield
- yield_CSharpKeyword
helpviewer_keywords: yield keyword [C#]
ms.assetid: 1089194f-9e53-46a2-8642-53ccbe9d414d
caps.latest.revision: "46"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4735ab33faea71b792cbc6b567884b64bd6ca029
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="yield-c-reference"></a>yield (Referenční dokumentace jazyka C#)
Při použití `yield` – klíčové slovo v příkazu, které označuje, že metoda, operátor, nebo `get` přistupujícího objektu, ve kterých se vyskytuje je iterátor. Pomocí `yield` k definování iterovat odebírá potřebu, explicitní navíc – třída (třída, která obsahuje stav pro výčet, najdete v části <xref:System.Collections.Generic.IEnumerator%601> příklad) při implementaci <xref:System.Collections.IEnumerable> a <xref:System.Collections.IEnumerator> vzor pro vlastní shromažďování typ.  
  
 Následující příklad ukazuje dva způsoby `yield` příkaz.  
  
```csharp  
yield return <expression>;  
yield break;  
```  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít `yield return` příkaz vrátit každý element, jeden v čase.  
  
 Používat metodu iterator přes [foreach](../../../csharp/language-reference/keywords/foreach-in.md) příkaz nebo dotaz LINQ. Každé iteraci `foreach` smyčky volá metodu iterator. Když `yield return` příkaz je dosaženo v metodě iterator `expression` se vrátí, a se uchovávají aktuální umístění v kódu. Provádění je restartováno ze zmíněného umístění pokaždé, když je zavolána funkce iterátoru.  
  
 Můžete použít `yield break` příkaz k ukončení iterace.  
  
 Další informace o iterátory najdete v tématu [iterátory](../../iterators.md).  
  
## <a name="iterator-methods-and-get-accessors"></a>Iterátory a přístupové objekty get  
 Deklarace iterátoru musí splňovat následující požadavky:  
  
-   Návratový typ musí být <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, nebo <xref:System.Collections.Generic.IEnumerator%601>.  
  
-   Deklaraci nemůže mít žádné [ref](../../../csharp/language-reference/keywords/ref.md) nebo [out](../../../csharp/language-reference/keywords/out.md) parametry.  
  
 `yield` Typ iterátor, který vrátí <xref:System.Collections.IEnumerable> nebo <xref:System.Collections.IEnumerator> je `object`.  Pokud vrátí iteraci <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Collections.Generic.IEnumerator%601>, musí být implicitní převod z typu výraz v `yield return` příkaz, který má parametr obecného typu.  
  
 Nelze zahrnout `yield return` nebo `yield break` příkaz v metody, které mají následující vlastnosti:  
  
-   Anonymní metody. Další informace najdete v tématu [anonymní metody](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).  
  
-   Metody, které obsahují nebezpečné bloky. Další informace najdete v tématu [unsafe](../../../csharp/language-reference/keywords/unsafe.md).  
  
## <a name="exception-handling"></a>Zpracování výjimek  
 A `yield return` příkaz nebyl nalezen v bloku try-catch. A `yield return` příkaz se může nacházet v zkuste bloku příkazu try-finally –.  
  
 A `yield break` příkaz může být umístěno v bloku try nebo catch bloku, ale není a nakonec blokovat.  
  
 Pokud `foreach` textu (mimo metodu iterator) vyvolá výjimku, `finally` bloku v metodě iterator se spustí.  
  
## <a name="technical-implementation"></a>Technická implementace  
 Následující kód vrátí `IEnumerable<string>` z metody iterator a pak iteruje jejích elementů.  
  
```csharp  
IEnumerable<string> elements = MyIteratorMethod();  
foreach (string element in elements)  
{  
   ...  
}  
```  
  
 Volání `MyIteratorMethod` neprovede těla metody. Místo toho se volání vrátí `IEnumerable<string>` do `elements` proměnné.  
  
 Na iterace `foreach` smyčky, <xref:System.Collections.IEnumerator.MoveNext%2A> metoda je volána pro `elements`. Toto volání provede text `MyIteratorMethod` až do dalšího `yield return` je dosaženo příkaz. Výraz vrácený `yield return` příkaz určuje nejen hodnotu `element` proměnná pro spotřeba těla smyčky, ale také <xref:System.Collections.Generic.IEnumerator%601.Current%2A> vlastnost `elements`, který je `IEnumerable<string>`.  
  
 Při každém opakování následné `foreach` cykly, odkud pokračuje v provádění těla iterator bylo přerušeno, znovu zastavit při dosažení `yield return` příkaz. `foreach` Dokončení smyčky, kdy konec metodu iterator nebo `yield break` je dosaženo příkaz.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu má `yield return` příkaz, který je uvnitř `for` smyčky. Každé iteraci `foreach` těla příkazu v `Process` vytvoří volání `Power` iterator funkce. Každé volání funkce iterator pokračuje dalším spuštění `yield return` příkaz, který spadá další iterace `for` smyčky.  
  
 Návratový typ metody iterator <xref:System.Collections.IEnumerable>, který je typu iterator rozhraní. Při volání metody iterátoru je vrácen vyčíslitelný objekt, který obsahuje mocniny čísla.  
  
 [!code-csharp[csrefKeywordsContextual#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/yield_1.cs)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje `get` přistupujícího objektu, který je iterátor. V příkladu každý `yield return` příkaz vrací instanci třídy definovaný uživatelem.  
  
 [!code-csharp[csrefKeywordsContextual#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/yield_2.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [foreach v](../../../csharp/language-reference/keywords/foreach-in.md)  
 [Iterátory](../../iterators.md)
