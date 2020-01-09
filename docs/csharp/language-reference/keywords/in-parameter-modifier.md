---
title: v modifikátoru parametru C# – referenční informace
ms.date: 03/26/2019
helpviewer_keywords:
- parameters [C#], in
- in parameters [C#]
ms.openlocfilehash: 10e7b91f9a6bf280c5f0654b243492bac8cde1e0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715255"
---
# <a name="in-parameter-modifier-c-reference"></a>in – modifikátor parametruC# (odkaz)

Klíčové slovo `in` způsobí, že argumenty budou předány odkazem. Nastaví formální parametr jako alias pro argument, který musí být proměnná. Jinými slovy, každá operace s parametrem je provedena na argumentu. Je podobný klíčovým slovem [ref](ref.md) nebo [out](out-parameter-modifier.md) s tím rozdílem, že `in` argumenty nelze upravovat pomocí volané metody. Vzhledem k tomu, že lze upravit argumenty `ref`, `out` argumenty musí být upraveny volanou metodou a tyto úpravy jsou pozorovatelně v volajícím kontextu.

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

Předchozí příklad ukazuje, že modifikátor `in` je obvykle zbytečný na webu volání. Vyžaduje se pouze v deklaraci metody.

> [!NOTE] 
> Klíčové slovo `in` lze také použít s parametrem obecného typu k určení toho, že parametr typu je kontravariantní, jako součást příkazu `foreach` nebo jako součást klauzule `join` v dotazu LINQ. Další informace o použití klíčového slova `in` v těchto kontextech naleznete [v části v](in.md)tématu, která poskytuje odkazy na všechna tato použití.
  
Proměnné předané jako argumenty `in` musí být před předáním do volání metody inicializovány. Volaná metoda ale nemůže přiřadit hodnotu ani upravovat argument.  

Modifikátor parametru `in` je k dispozici C# v 7,2 a novějších. Předchozí verze generují chybu kompilátoru `CS8107` ("funkce" odkazy jen pro čtení "není v C# 7,0 k dispozici. Použijte prosím jazyk verze 7,2 nebo vyšší. ") Chcete-li nakonfigurovat verzi jazyka kompilátoru, přečtěte si téma [ C# výběr jazykové verze](../configure-language-version.md).

Klíčová slova `in`, `ref`a `out` nejsou považována za součást signatury metody pro účely překladu přetížení. Proto metody nemohou být přetíženy, pokud jediným rozdílem je, že jedna metoda přebírá `ref` nebo `in` argument a druhý přebírá `out` argument. Následující kód například nebude zkompilován:  
  
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

Pravidla řešení přetížení můžete pochopit pro metody s hodnotou a `in` argumenty vysvětlením motivace pro `in` argumenty. Definování metod pomocí `in`ch parametrů je potenciální optimalizace výkonu. Některé argumenty typu `struct` mohou být velké a když jsou metody volány v těsných smyčkách nebo kritických cestách kódu, náklady na kopírování těchto struktur jsou kritické. Metody deklarují `in` parametrů pro určení, že argumenty mohou být předány odkazem bezpečně, protože volaná metoda neupravuje stav tohoto argumentu. Předání těchto argumentů odkazem se vyhne (potenciálně) nákladné kopii. 

Určení `in` argumentů na webu volání je obvykle volitelné. Neexistuje žádný sémantický rozdíl mezi předáním argumentů podle hodnoty a jejich předáním odkazem pomocí modifikátoru `in`. Modifikátor `in` na webu volání je nepovinný, protože nemusíte označovat, že hodnota argumentu může být změněna. Explicitně přidáte modifikátor `in` na webu volání, aby se zajistilo, že argument je předán odkazem, nikoli hodnotou. Explicitní použití `in` má následující dva účinky:

Nejprve zadáním `in` na webu volání vynutí kompilátor vybrat metodu definovanou s parametrem odpovídajícího `in`. V opačném případě, pokud se dvě metody liší pouze v přítomnosti `in`, je přetížení hodnotou pomocí lepší shody.

Dále zadáním `in` deklarujete záměr k předání argumentu odkazem. Argument použitý v `in` musí představovat umístění, na které lze přímo odkazovat. Platí stejná obecná pravidla pro argumenty `out` a `ref`: nemůžete použít konstanty, běžné vlastnosti nebo jiné výrazy, které vytváří hodnoty. V opačném případě vynechání `in` na webu volání informuje kompilátor, že umožňuje vytvořit dočasnou proměnnou, která bude předána odkazem jen pro čtení k metodě. Kompilátor vytvoří dočasnou proměnnou k překonání několika omezení s `in` argumenty:

- Dočasná proměnná umožňuje konstanty v čase kompilace jako parametry `in`.
- Dočasná proměnná povoluje vlastnosti nebo jiné výrazy pro parametry `in`.
- Dočasná proměnná umožňuje argumenty, kde existuje implicitní převod typu argumentu na typ parametru.

Ve všech předchozích instancích vytvoří kompilátor dočasnou proměnnou, která ukládá hodnotu konstanty, vlastnosti nebo jiného výrazu.

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

Nyní předpokládejme, že je k dispozici jiná metoda používající argumenty hodnoty. Změny výsledků, jak je znázorněno v následujícím kódu:

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

Jediným voláním metody, kde je argument předána odkazem, je ten poslední.

> [!NOTE]
> Předchozí kód používá `int` jako typ argumentu pro zjednodušení. Vzhledem k tomu, že `int` není větší než odkaz ve většině moderních počítačů, neexistuje žádná výhoda k předání jednoho `int` jako odkazu jen pro čtení. 

## <a name="limitations-on-in-parameters"></a>Omezení parametrů `in`

Klíčová slova `in`, `ref`a `out` nelze použít pro následující typy metod:  
  
- Asynchronní metody, které definujete pomocí modifikátoru [Async](async.md) .  
- Metody iterátoru, které zahrnují příkaz [yield return](yield.md) nebo `yield break`.  

## <a name="c-language-specification"></a>C# – jazyková specifikace  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Parametry metody](method-parameters.md)
- [Zapisovat bezpečný efektivní kód](../../write-safe-efficient-code.md)
