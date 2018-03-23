---
title: v – modifikátor parametrů (referenční dokumentace jazyka C#)
ms.date: 03/06/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- parameters [C#], in
- in parameters [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9b8b21e2bdc95829c831ee71f24b47986321b7d0
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/23/2018
---
# <a name="in-parameter-modifier-c-reference"></a>v – modifikátor parametrů (referenční dokumentace jazyka C#)

`in` – Klíčové slovo způsobí, že argumenty předávané odkazem. Je třeba [ref](ref.md) nebo [out](out-parameter-modifier.md) klíčová slova, která kromě `in` argumenty nemůže být upraven zavolat metodu, zatímco `ref` argumenty může být změněna, `out` argumenty je třeba upravit volající, a tyto úpravy jsou lze zobrazit v volání kontextu.

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

Předchozí příklad ukazuje, který `in` modifikátor není nutný v lokalitě volání. Je potřeba jenom v deklaraci metoda.

> [!NOTE] 
> `in` – Klíčové slovo lze také s parametr obecného typu k určení, že parametr typu je kontravariant, jako součást `foreach` prohlášení, nebo jako součást `join` klauzuli v dotazu LINQ. Další informace o použití `in` – klíčové slovo v těchto kontextů, najdete v části [v](in.md) který obsahuje odkazy na všechny tyto používá.
  
 Proměnné předány jako `in` argumenty se musí inicializovat před předáním ve volání metody. Volané metody však nemusí přiřadit hodnotu nebo upravte argument.  
  
 I když `in`, `ref`, a `out` klíčová slova způsobit různé chování, nejsou považovány za součást podpis metody v době kompilace. Proto metody nemohou být přetíženy, pokud je jediným rozdílem je, že jedna metoda má `ref` nebo `in` argument a dalších trvá `out` argument. Například následující kód, nebude kompilace:  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on in, ref and out".
    public void SampleMethod(in int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
Přetížení podle přítomnosti `in` je povoleno, ale generuje upozornění kompilátoru:  
  
```csharp
class InOverloads
{
    // Discouraged. Calling SampleMethod(value) is ambiguous.
    public void SampleMethod(in int i) { }
    public void SampleMethod(int i) { }
}
```

Vlastnosti nebo konstanty může být předána jako `in` parametry, protože volající metody nesmí změnit jejich hodnot.
  
Nelze použít `in`, `ref`, a `out` klíčová slova pro následující typy metod:  
  
- Asynchronní metody, které definují pomocí [asynchronní](../../../csharp/language-reference/keywords/async.md) modifikátor.  
  
- Iterator metody, které zahrnují [yield vrátit](../../../csharp/language-reference/keywords/yield.md) nebo `yield break` příkaz.  

Obvykle deklarovat `in` argumenty, aby se zabránilo operace kopírování, která je nezbytná k předání argumentů hodnotou. To je velmi užitečné, když argumenty jsou typy hodnot, jako je například struktury, kde jsou dražší než předání odkazem operace kopírování.

> [!WARNING]
>  `in` Parametry může být i dražší, pokud došlo ke zneužití. Kompilátor nemusí vědět, pokud člen metody upravit stav struct. Vždy, když kompilátor nebude moct zajistit, že objekt se nemění, obranu vytvoří kopii a volá člen odkazů pomocí tuto kopii. Všechny možné změny se na tuto Obranným kopii. Dva způsoby, aby se zabránilo tyto kopie jsou předat `in` parametry jako `in` argumenty nebo k definování struktury jako `readonly struct`.

## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Parametry metody](../../../csharp/language-reference/keywords/method-parameters.md)  
 [Odkaz na sémantiku s typy hodnot](../../../csharp/reference-semantics-with-value-types.md)
