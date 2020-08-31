---
description: v modifikátoru parametru – reference jazyka C#
title: v modifikátoru parametru – reference jazyka C#
ms.date: 03/19/2020
helpviewer_keywords:
- parameters [C#], in
- in parameters [C#]
ms.openlocfilehash: 613be9248e6ce9b974bcab1b59abd30469e9e180
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89118401"
---
# <a name="in-parameter-modifier-c-reference"></a>in – modifikátor parametru (Referenční dokumentace jazyka C#)

`in`Klíčové slovo způsobuje argumenty předávané odkazem. Nastaví formální parametr jako alias pro argument, který musí být proměnná. Jinými slovy, každá operace s parametrem je provedena na argumentu. Je podobný klíčovým slovem [ref](ref.md) nebo [out](out-parameter-modifier.md) s tím rozdílem, že `in` argumenty nemohou být upraveny metodou volané. Vzhledem k tomu, že je `ref` možné upravit argumenty, `out` musí být argumenty upraveny metodou volané a tyto úpravy lze v kontextu volání pozorovatelit.

[!code-csharp-interactive[cs-in-keyword](../../../../samples/snippets/csharp/language-reference/keywords/in-ref-out-modifier/InParameterModifier.cs#1)]  

Předchozí příklad ukazuje, že `in` Modifikátor je obvykle zbytečný na webu volání. Vyžaduje se pouze v deklaraci metody.

> [!NOTE]
> `in`Klíčové slovo lze také použít s parametrem obecného typu k určení toho, že parametr typu je kontravariantní, jako součást `foreach` příkazu nebo jako součást `join` klauzule v dotazu LINQ. Další informace o použití `in` klíčového slova v těchto kontextech naleznete [v části v](in.md)tématu, který poskytuje odkazy na všechna tato použití.
  
Proměnné předané jako `in` argumenty musí být před předáním do volání metody inicializovány. Volaná metoda ale nemůže přiřadit hodnotu ani upravovat argument.  

`in`Modifikátor parametru je k dispozici v C# 7,2 a novějším. Předchozí verze generují chybu kompilátoru `CS8107` ("funkce" odkazy jen pro čtení "není v jazyce C# 7,0 k dispozici. Použijte prosím jazyk verze 7,2 nebo vyšší. ") Chcete-li nakonfigurovat verzi jazyka kompilátoru, přečtěte si téma [Výběr verze jazyka C#](../configure-language-version.md).

`in` `ref` `out` Klíčová slova, a nejsou považována za součást signatury metody pro účely řešení přetížení. Proto metody nemohou být přetíženy, pokud jediným rozdílem je, že jedna metoda přebírá `ref` `in` argument or a druhý přebírá `out` argument. Následující kód například nebude zkompilován:  
  
```csharp
class CS0663_Example
{
    // Compiler error CS0663: "Cannot define overloaded
    // methods that differ only on in, ref and out".
    public void SampleMethod(in int i) { }
    public void SampleMethod(ref int i) { }
}
```
  
Přetížení na základě přítomnosti `in` je povolené:  
  
```csharp
class InOverloads
{
    public void SampleMethod(in int i) { }
    public void SampleMethod(int i) { }
}
```

## <a name="overload-resolution-rules"></a>Pravidla řešení přetížení

Můžete pochopit pravidla rozlišení přetížení pro metody s hodnotou a `in` argumenty pomocí pochopení motivace pro `in` argumenty. Definování metod pomocí `in` parametrů je potenciální optimalizace výkonu. Některé `struct` argumenty typu můžou být velké a při volání metod v těsných smyčkách nebo kritických cestách kódu jsou náklady na kopírování těchto struktur kritické. Metody deklaruje `in` parametry pro určení, že argumenty mohou být předány odkazem bezpečně, protože volaná metoda neupravuje stav tohoto argumentu. Předání těchto argumentů odkazem se vyhne (potenciálně) nákladné kopii.

Zadání `in` argumentů na webu volání je obvykle volitelné. Neexistuje žádný sémantický rozdíl mezi předáním argumentů podle hodnoty a jejich předáním odkazem pomocí `in` modifikátoru. `in`Modifikátor na webu volání je nepovinný, protože nemusíte označovat, že hodnota argumentu může být změněna. Explicitně přidáte `in` Modifikátor na webu volání, aby se zajistilo, že argument je předán odkazem, nikoli hodnotou. Explicitní použití `in` má následující dva účinky:

Nejprve zadáním `in` na webu volání vynutí kompilátor vybrat metodu definovanou s parametrem, který je s ním shodný `in` . V opačném případě, pokud se dvě metody liší pouze v přítomnosti `in` , je přetížení podle hodnot lepší shodu.

Za druhé, zadáním `in` deklarujete záměr k předání argumentu odkazem. Argument použitý spolu `in` musí představovat umístění, na které lze přímo odkazovat. Platí stejná obecná pravidla pro `out` `ref` argumenty a. nemůžete použít konstanty, běžné vlastnosti nebo jiné výrazy, které vytváří hodnoty. V opačném případě vynechání `in` na webu volání informuje kompilátor, že umožňuje vytvořit dočasnou proměnnou, která bude předána odkazem jen pro čtení k metodě. Kompilátor vytvoří dočasnou proměnnou k překonání několika omezení s `in` argumenty:

- Dočasná proměnná umožňuje jako parametry konstanty v čase kompilace `in` .
- Dočasná proměnná povoluje vlastnosti nebo jiné výrazy pro `in` parametry.
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
> Předchozí kód používá `int` jako typ argumentu pro zjednodušení. Vzhledem k tomu `int` , že se ve většině moderních počítačů nejedná o větší než odkaz, není výhoda pro předání jediného `int` odkazu jen pro čtení.

## <a name="limitations-on-in-parameters"></a>Omezení `in` parametrů

`in` `ref` Klíčová slova, a nelze použít `out` pro následující typy metod:  
  
- Asynchronní metody, které definujete pomocí modifikátoru [Async](async.md) .  
- Metody iterátoru, které zahrnují [návratový návrat](yield.md) nebo `yield break` příkaz yield.
- První argument metody rozšíření nemůže mít `in` modifikátor, pokud tento argument není struktura.
- První argument metody rozšíření, kde je tento argument obecný typ (i když je tento typ omezen na strukturu)

## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Parametry metody](method-parameters.md)
- [Zapisovat bezpečný efektivní kód](../../write-safe-efficient-code.md)
