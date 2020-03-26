---
title: v modifikátoru parametrů - C# Reference
ms.date: 03/19/2020
helpviewer_keywords:
- parameters [C#], in
- in parameters [C#]
ms.openlocfilehash: 20956f9e25b6830a8876824a4c9dad1dbc4c4f3e
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249367"
---
# <a name="in-parameter-modifier-c-reference"></a>v modifikátoru parametrů (C# Reference)

Klíčové `in` slovo způsobí, že argumenty, které mají být předány odkazem. Vytvoří formální parametr alias pro argument, který musí být proměnná. Jinými slovy, každá operace na parametr je provedena na argument. Je to jako [ref](ref.md) nebo [out](out-parameter-modifier.md) `in` klíčová slova, s tím rozdílem, že argumenty nelze změnit volanou metodou. Vzhledem `ref` k tomu, `out` argumenty mohou být změněny, argumenty musí být změněny volanou metodou a tyto změny jsou pozorovatelné v kontextu volání.

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

Předchozí příklad ukazuje, že `in` modifikátor je obvykle zbytečné na webu volání. Je vyžadována pouze v deklaraci metody.

> [!NOTE]
> Klíčové `in` slovo lze také použít s parametrem obecného typu k určení, že `foreach` parametr typu je `join` kontravariantní, jako součást příkazu nebo jako součást klauzule v dotazu LINQ. Další informace o použití `in` klíčového slova v těchto souvislostech naleznete v [části](in.md), která obsahuje odkazy na všechna tato použití.
  
Proměnné předané `in` jako argumenty musí být inicializovány před předáním ve volání metody. Volaná metoda však nesmí přiřadit hodnotu nebo upravit argument.  

Modifikátor `in` parametrů je k dispozici v c# 7.2 a novější. Předchozí verze generovat chybu `CS8107` kompilátoru ("Funkce odkazy jen pro čtení' není k dispozici v C# 7.0. Použijte prosím jazyk verze 7.2 nebo vyšší.") Informace o konfiguraci jazykové verze kompilátoru naleznete [v tématu Výběr jazykové verze jazyka C#](../configure-language-version.md).

`in`, `ref`a `out` klíčová slova nejsou považovány za součást podpisu metody pro účely řešení přetížení. Proto metody nelze přetížit, pokud jediný rozdíl `ref` je, že jedna metoda trvá nebo `in` argument a druhý trvá `out` argument. Následující kód, například, nebude kompilovat:  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on in, ref and out".
    public void SampleMethod(in int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
Přetížení na základě přítomnosti `in` je povoleno:  
  
```csharp
class InOverloads
{
    public void SampleMethod(in int i) { }
    public void SampleMethod(int i) { }
}
```

## <a name="overload-resolution-rules"></a>Pravidla řešení přetížení

Můžete pochopit pravidla řešení přetížení pro metody s `in` hodnotou vs `in` argumenty pochopením motivace pro argumenty. Definování metod `in` pomocí parametrů je potenciální optimalizace výkonu. Některé `struct` argumenty typu mohou mít velké velikosti a při volání metod v těsných cyklických cynicích nebo kritických cestách kódu jsou náklady na kopírování těchto struktur kritické. Metody `in` deklarují parametry, které určují, že argumenty mohou být bezpečně předány odkazem, protože volaná metoda nemění stav tohoto argumentu. Předáním těchto argumentů odkazem se vyhnete (potenciálně) nákladné kopii.

Zadání `in` argumentů na webu volání je obvykle volitelné. Neexistuje žádný sémantický rozdíl mezi předávání argumentů hodnotou `in` a jejich předávání odkazem pomocí modifikátoru. Modifikátor `in` na webu volání je volitelný, protože není nutné označit, že hodnota argumentu může být změněna. Explicitně přidáte `in` modifikátor na webu volání, abyste zajistili, že argument je předán odkazem, nikoli hodnotou. Explicitně `in` using má následující dva efekty:

Nejprve zadání `in` na pracovišti volání vynutí kompilátoru `in` vybrat metodu definovanou s odpovídající parametr. V opačném případě, pokud dvě `in`metody se liší pouze v přítomnosti , přetížení podle hodnoty je lepší shoda.

Za druhé, `in` zadání deklaruje váš záměr předat argument odkazem. Argument použitý `in` s musí představovat umístění, které lze přímo odkazovat. Stejná obecná `out` pravidla `ref` pro a argumenty platí: Nelze použít konstanty, běžné vlastnosti nebo jiné výrazy, které vytvářejí hodnoty. V opačném případě `in` vynechání na webu volání informuje kompilátor, který mu umožní vytvořit dočasnou proměnnou předat jen pro čtení odkaz na metodu. Kompilátor vytvoří dočasnou proměnnou `in` k překonání několika omezení s argumenty:

- Dočasná proměnná umožňuje konstanty `in` v době kompilace jako parametry.
- Dočasná proměnná umožňuje vlastnosti `in` nebo jiné výrazy pro parametry.
- Dočasná proměnná umožňuje argumenty, kde je implicitní převod z typu argumentu na typ parametru.

Ve všech předchozích instancích kompilátor vytvoří dočasnou proměnnou, která ukládá hodnotu konstanty, vlastnosti nebo jiného výrazu.

Následující kód ilustruje tato pravidla:

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

Nyní předpokládejme, že byla k dispozici jiná metoda používající argumenty hodnoty. Výsledky se mění tak, jak je znázorněno v následujícím kódu:

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

Jediná metoda volání, kde je argument předán odkazem je poslední.

> [!NOTE]
> Předchozí kód používá `int` jako typ argumentu pro jednoduchost. Protože `int` není větší než odkaz ve většině moderních počítačů, není `int` žádný přínos pro předání jeden jako odkaz jen pro čtení.

## <a name="limitations-on-in-parameters"></a>Omezení `in` parametrů

Klíčová `out` slova a `in`klíčová `ref`slova nelze použít pro následující typy metod:  
  
- Asynchronní metody, které definujete pomocí [asynchronního](async.md) modifikátoru.  
- Iterátor metody, které zahrnují výnos `yield break` výnos [return](yield.md) nebo příkaz.
- První argument metody rozšíření nemůže `in` mít modifikátor, pokud tento argument není struktura.
- První argument metody rozšíření, kde tento argument je obecný typ (i když je tento typ omezen na strukturu.)

## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [C# Klíčová slova](index.md)
- [Parametry metody](method-parameters.md)
- [Zapisujte bezpečný efektivní kód](../../write-safe-efficient-code.md)
