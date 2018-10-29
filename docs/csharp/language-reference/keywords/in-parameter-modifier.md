---
title: v parametru modifikátor (referenční dokumentace jazyka C#)
ms.date: 03/06/2018
helpviewer_keywords:
- parameters [C#], in
- in parameters [C#]
ms.openlocfilehash: 199d2d54a1937b9982131b8cc7f1c777f656d7a9
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2018
ms.locfileid: "50199406"
---
# <a name="in-parameter-modifier-c-reference"></a>v parametru modifikátor (referenční dokumentace jazyka C#)

`in` – Klíčové slovo způsobí, že argumenty, které mají být předány podle odkazu. Je třeba [ref](ref.md) nebo [si](out-parameter-modifier.md) klíčová slova, kromě toho, že `in` nemůže upravit argumentů volané metody. Vzhledem k tomu `ref` argumenty se dají měnit, `out` argumenty musí být upravena klíčovým volané metody a jsou tyto změny pozorovat ve volání kontextu.

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

Předchozí příklad ukazuje, že `in` Modifikátor je obvykle zbytečné na lokalitu volání. Je potřeba jenom v deklaraci metody.

> [!NOTE] 
> `in` – Klíčové slovo je také možné pomocí parametru obecného typu k určení, že parametr typu je kontravariant, jako součást `foreach` příkazu, nebo jako součást `join` klauzule v dotazu LINQ. Další informace týkající se použití `in` – klíčové slovo v těchto kontextech najdete v článku [v](in.md), který obsahuje odkazy na tato použití.
  
 Proměnné se předaly jako `in` argumenty musí být inicializován před předáním ve volání metody. Volané metody však nelze přiřadit hodnotu nebo upravujete argument.  
  
 I když `in`, `ref`, a `out` klíčová slova způsobit různé chování za běhu, nejsou považovány za součást podpisu metody v době kompilace. Proto metody nemohou být přetíženy, pokud je jediným rozdílem je, že jedna metoda má `ref` nebo `in` argument a druhý bere `out` argument. Například následující kód, nebude kompilovat:  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded 
    // methods that differ only on in, ref and out".
    public void SampleMethod(in int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
Přetížení založené na přítomnost `in` může:  
  
```csharp
class InOverloads
{
    public void SampleMethod(in int i) { }
    public void SampleMethod(int i) { }
}
```

## <a name="overload-resolution-rules"></a>Pravidla pro řešení přetížení

Rozumíte pravidla rozlišení přetížení pro metody s hodnotou versus `in` argumenty Pochopením motivace pro `in` argumenty. Definování metody pomocí `in` parametrů je potenciální optimalizaci výkonu. Některé `struct` argumenty typu mohou být velké a při volání metody v těsné smyčky nebo cesty kritického kódu, náklady na kopírování těchto struktur je velmi důležité. Metody deklarovat `in` parametry k určení, že argumenty mohou být předány podle odkazu bezpečně protože volané metody neprovede žádné změny stavu tento argument. Předání těchto argumentů odkazem se vyhnete (potenciálně) nákladné kopírování. 

Určení `in` pro argumenty při volání lokalita je obvykle volitelné. Neexistuje žádné sémantické rozdíly mezi předávání argumentů podle hodnoty a jejich předání pomocí odkazu `in` modifikátor. `in` Modifikátor na lokalitu volání je volitelný, protože není nutné k označení, že hodnota argumentu může být změněn. Explicitně přidat `in` modifikátor lokality volání k zajištění argument se předá odkazem, ne podle hodnoty. Explicitně pomocí `in` má následující dva důsledky:

Nejprve zadání `in` při volání webu vynutí, aby kompilátor výběr metody definované k odpovídajícímu `in` parametru. Jinak, pokud dvě metody se liší pouze v nichž se nachází z `in`, podle hodnoty přetížení představuje lepší shodu.

Za druhé, určení `in` deklaruje vaším záměrem pro předání argumentu podle odkazu. Argument použitý s `in` musí představovat umístění, které lze přímo odkazovat. Stejné obecná pravidla pro `out` a `ref` použít argumenty: nelze použít konstanty, běžné vlastnosti nebo dalších výrazů, které vracet hodnoty. V opačném případě vynechání `in` při volání webu informuje kompilátor, že vám umožní vytvořit dočasnou proměnnou předávání pomocí odkazu pouze pro čtení k metodě. Kompilátor vytvoří dočasnou proměnnou několik omezení s `in` argumenty:

- Dočasná proměnná umožňuje konstanty z doby kompilace jako `in` parametry.
- Dočasná proměnná umožňuje vlastnosti nebo dalších výrazů pro `in` parametry.
- Dočasná proměnná umožňuje argumenty tam, kde je implicitní převod z typu argumentu na typ parametru.

Ve všech předchozích instancích kompilátor vytvoří dočasnou proměnnou, která ukládá hodnotu konstanty, vlastnosti nebo jiný výraz.

Následující kód znázorňuje tato pravidla:

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

Předpokládejme, že byla k dispozici jinou metodu pomocí hodnot argumentů. Výsledky změnit, jak je znázorněno v následujícím kódu:

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

Pouze volání metody, kde se argument předaný odkazem je finální.

> [!NOTE]
> Předchozí kód používá `int` jako typ argumentu pro zjednodušení. Protože `int` není větší než odkaz na většině moderních počítačů není žádná výhoda pro předání jednoho `int` jako jen pro čtení. 

## <a name="limitations-on-in-parameters"></a>Omezení `in` parametry

Nelze použít `in`, `ref`, a `out` klíčová slova pro následující druhy metod:  
  
- Asynchronní metody, které definujete pomocí [asynchronní](async.md) modifikátor.  
- Metody iterátorů, mezi které patří [yield return](yield.md) nebo `yield break` příkazu.  

## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../index.md)  
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)  
- [Klíčová slova jazyka C#](index.md)  
- [Parametry metody](method-parameters.md)  
- [Psát bezpečný kód efektivní](../../write-safe-efficient-code.md)  
