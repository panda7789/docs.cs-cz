---
title: v – modifikátor parametrů (referenční dokumentace jazyka C#)
ms.date: 03/06/2018
helpviewer_keywords:
- parameters [C#], in
- in parameters [C#]
ms.openlocfilehash: aa6720430a1d93d7eacb098962c09efad09a179f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="in-parameter-modifier-c-reference"></a>v – modifikátor parametrů (referenční dokumentace jazyka C#)

`in` – Klíčové slovo způsobí, že argumenty předávané odkazem. Je třeba [ref](ref.md) nebo [out](out-parameter-modifier.md) klíčová slova, která kromě `in` argumenty nemůže být upraven zavolat metodu, zatímco `ref` argumenty může být změněna, `out` argumenty je třeba upravit volající, a tyto úpravy jsou lze zobrazit v volání kontextu.

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

Předchozí příklad ukazuje `in` modifikátor není nutný, obvykle v lokalitě volání. Je potřeba jenom v deklaraci metoda.

> [!NOTE] 
> `in` – Klíčové slovo lze také s parametr obecného typu k určení, že parametr typu je kontravariant, jako součást `foreach` prohlášení, nebo jako součást `join` klauzuli v dotazu LINQ. Další informace o použití `in` – klíčové slovo v těchto kontextů, najdete v části [v](in.md), který obsahuje odkazy na všechny tyto používá.
  
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
  
Přetížení podle přítomnosti `in` je povoleno:  
  
```csharp
class InOverloads
{
    public void SampleMethod(in int i) { }
    public void SampleMethod(int i) { }
}
```

## <a name="overload-resolution-rules"></a>Pravidel řešení přetížení

Rozumíte pravidla rozlišení přetížení pro metody s hodnotou oproti `in` argumenty prostřednictvím pochopení motivace pro `in` argumenty. Definování metod pomocí `in` parametrů je potenciální optimalizace výkonu. Některé `struct` argumenty typu mohou být velká velikost, a pokud jsou volány metody v úzkou smyčky nebo kód kritický pro cesty, náklady na kopírování tyto struktury je důležité. Metody deklarovat `in` parametry k určení, že argumenty může být předána odkazem bezpečně protože zavolat metodu nedojde ke změně stavu tohoto argumentu. Předání těchto argumentů odkazem zabraňuje (potenciálně) nákladné kopírování. 

Určení `in` argumenty při volání lokalita je obvykle volitelné. Není žádný sémantického rozdíl mezi předání argumentů hodnotou a jejich předávání pomocí odkazu `in` modifikátor. `in` Modifikátor v lokalitě volání je volitelný, protože nemusíte znamenat, že hodnota argumentu může být změněn. Explicitně přidat `in` modifikátor v lokalitě volání zajistit argument odkaz, je předaná není hodnotou. Explicitně pomocí `in` má dva důsledky:

Nejprve zadání `in` na volání lokality vynutí kompilátoru vybrat metodu definovaný s odpovídající `in` parametr. Jinak, když dvě metody se liší pouze v přítomnosti z `in`, podle hodnoty přetížení je lepší shodu.

Druhý, zadání `in` deklaruje vašich představ předat argument odkazem. Argument použít s `in` musí představovat umístění, které lze přímo odkazovat. Stejné obecná pravidla pro `out` a `ref` platí argumenty: konstanty, běžné vlastnosti nebo jiné výrazy, které produkují hodnoty nelze použít. Jinak hodnota vynechání `in` na volání lokality informuje kompilátor, že vám umožní vytvořit dočasnou proměnnou k předání odkazem jen pro čtení do metody. Kompilátor vytvoří dočasný proměnnou překonat několik omezení s `in` argumenty:

- Dočasné proměnné umožňuje kompilaci konstanty jako `in` parametry.
- Dočasné proměnné umožňuje vlastnosti nebo jiné výrazy pro `in` parametry.
- Dočasné proměnné umožňuje argumenty níž se nachází implicitní převod z typu argument na typ parametru.

Ve všech předchozích instancích kompilátor vytvoří dočasné proměnné, která ukládá hodnotu identifikátoru konstanta, vlastnost nebo jiných výraz.

Následující kód ukazuje tato pravidla:

```csharp
static void Method(in int argument)
{
    // implementation removed
}

Method(5); // OK, temporary variable created.
Method(5L); // CS1503: no implicit conversion from long to int
short s = 0;
Method(s); // OK, temporary int created with the value 0
Method(in s); // CS1503: cannot convert from in short to in int
int i = 42;
Method(i); // passed by readonly reference
Method(in i); // passed by readonly reference, explicitly using `in`
```

Nyní předpokládejme, že jinou metodu, pomocí hodnot argumentů byl k dispozici. Výsledky změnit, jak je znázorněno v následujícím kódu:

```csharp
static void Method(int argument)
{
    // implementation removed
}

static void Method(in int argument)
{
    // implementation removed
}

Method(5); // Calls overload passed by value
Method(5L); // CS1503: no implicit conversion from long to int
short s = 0;
Method(s); // Calls overload passed by value.
Method(in s); // CS1503: cannot convert from in short to in int
int i = 42;
Method(i); // Calls overload passed by value
Method(in i); // passed by readonly reference, explicitly using `in`
```

Jenom volání metody, kde je argument předaná odkaz je tu poslední.

> [!NOTE]
> Předchozí kód používá `int` jako typ argumentu pro jednoduchost. Protože `int` není větší než odkaz v většina moderních počítače, není k předání jedné `int` jako odkaz jen pro čtení. 

## <a name="limitations-on-in-parameters"></a>Omezení `in` parametry

Nelze použít `in`, `ref`, a `out` klíčová slova pro následující typy metod:  
  
- Asynchronní metody, které definují pomocí [asynchronní](async.md) modifikátor.  
- Iterator metody, které zahrnují [yield vrátit](yield.md) nebo `yield break` příkaz.  

## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../index.md)  
 [Průvodce programováním v jazyce C#](../../programming-guide/index.md)  
 [Klíčová slova jazyka C#](index.md)  
 [Parametry metody](method-parameters.md) [odkazovat sémantiku s typy hodnot](../../reference-semantics-with-value-types.md)
