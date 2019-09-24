---
title: Vlastnosti
description: Přečtěte F# si o vlastnostech, které jsou členy, kteří představují hodnoty přidružené k objektu.
ms.date: 05/16/2016
ms.openlocfilehash: c71d61e033501c2d535b5582c82d36ed8cb2241b
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216428"
---
# <a name="properties"></a>Vlastnosti

*Vlastnosti* jsou členy, které představují hodnoty přidružené k objektu.

## <a name="syntax"></a>Syntaxe

```fsharp
// Property that has both get and set defined.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with [accessibility-modifier] get() =
    get-function-body
and [accessibility-modifier] set parameter =
    set-function-body

// Alternative syntax for a property that has get and set.
[ attributes-for-get ]
[ static ] member [accessibility-modifier-for-get] [self-identifier.]PropertyName =
    get-function-body
[ attributes-for-set ]
[ static ] member [accessibility-modifier-for-set] [self-identifier.]PropertyName
with set parameter =
    set-function-body

// Property that has get only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName =
    get-function-body

// Alternative syntax for property that has get only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with get() =
    get-function-body

// Property that has set only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with set parameter =
    set-function-body

// Automatically implemented properties.
[ attributes ]
[ static ] member val [accessibility-modifier] PropertyName = initialization-expression [ with get, set ]
```

## <a name="remarks"></a>Poznámky

Vlastnosti představují relaci "má" v objektově orientovaném programování reprezentující data, která jsou přidružena k instancím objektů nebo pro statické vlastnosti s typem.

Vlastnosti lze deklarovat dvěma způsoby v závislosti na tom, zda chcete explicitně zadat základní hodnotu (označovanou také jako záložní úložiště) pro vlastnost, nebo pokud chcete, aby kompilátor pro vás automaticky vygeneroval záložní úložiště. Obecně byste měli použít explicitní způsob, pokud má vlastnost netriviální implementaci a automatický způsob, pokud je vlastnost pouze jednoduchá obálka pro hodnotu nebo proměnnou. K deklaraci vlastnosti explicitně použijte `member` klíčové slovo. Tato deklarativní syntaxe následuje syntaxí, která určuje `get` metody a `set` , také pojmenované *přistupující objekty*. Různé formuláře explicitní syntaxe zobrazené v oddílu syntax jsou používány pro čtení a zápis, vlastnosti jen pro čtení a pouze pro zápis. Pro vlastnosti jen pro čtení definujete pouze `get` metodu, pro vlastnosti jen pro zápis definujte `set` pouze metodu. Všimněte si, že pokud má vlastnost `get` oba `set` i přistupující objekty, alternativní syntaxe vám umožní určit atributy a Modifikátory dostupnosti, které jsou pro každý přistupující objekt rozdílné, jak je uvedeno v následujícím kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3201.fs)]

Pro vlastnosti pro čtení a `get` zápis, které mají `set` `get` metodu a, pořadí a `set` lze obrátit. Alternativně můžete zadat syntaxi zobrazenou pouze pro `get` a syntaxi zobrazenou pouze pro `set` místo použití kombinované syntaxe. Díky tomu je snazší komentovat jednotlivec `get` nebo `set` metodu, pokud je to něco, co možná budete muset udělat. Tato alternativa k použití kombinované syntaxe je uvedena v následujícím kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3203.fs)]

Soukromé hodnoty, které uchovávají data pro vlastnosti, se nazývají *záložní úložiště*. Chcete-li, aby kompilátor vytvořil záložní úložiště automaticky, použijte klíčová slova `member val`, vynechejte identifikátor držitele a potom zadejte výraz pro inicializaci vlastnosti. Pokud má být vlastnost proměnlivá, zahrňte `with get, set`. Například následující typ třídy obsahuje dvě automaticky implementované vlastnosti. `Property1`je jen pro čtení a je inicializována na argument poskytnutý primárnímu konstruktoru a `Property2` je nastavitelnou vlastností inicializovaným na prázdný řetězec:

```fsharp
type MyClass(property1 : int) =
member val Property1 = property1
member val Property2 = "" with get, set
```

Automaticky implementované vlastnosti jsou součástí inicializace typu, takže musí být zahrnuty před ostatními definicemi členů, stejně jako `let` vazby a `do` vazby v definici typu. Všimněte si, že výraz, který inicializuje automaticky implementovanou vlastnost, je vyhodnocen pouze při inicializaci, a ne pokaždé, když je vlastnost k dispozici. Toto chování je v kontrastu s chováním explicitně implementované vlastnosti. To znamená, že kód k inicializaci těchto vlastností je přidán do konstruktoru třídy. Vezměte v úvahu následující kód, který ukazuje tento rozdíl:

```fsharp
type MyClass() =
    let random  = new System.Random()
    member val AutoProperty = random.Next() with get, set
    member this.ExplicitProperty = random.Next()

let class1 = new MyClass()

printfn "class1.AutoProperty = %d" class1.AutoProperty
printfn "class1.AutoProperty = %d" class1.AutoProperty
printfn "class1.ExplicitProperty = %d" class1.ExplicitProperty
printfn "class1.ExplicitProperty = %d" class1.ExplicitProperty
```

**Output**

```console
class1.AutoProperty = 1853799794
class1.AutoProperty = 1853799794
class1.ExplicitProperty = 978922705
class1.ExplicitProperty = 1131210765
```

Výstup předcházejícího kódu ukazuje, že hodnota autoproperty není při opakovaném volání změněna, zatímco ExplicitProperty se mění pokaždé, když je volána. To ukazuje, že výraz pro automaticky implementovanou vlastnost není vyhodnocen pokaždé, jak je metoda getter pro vlastnost Explicit.

>[!WARNING]
>Existují některé knihovny, například Entity Framework (`System.Data.Entity`), které provádějí vlastní operace v konstruktorech základní třídy, které nefungují dobře s inicializací automaticky implementovaných vlastností. V těchto případech se pokuste použít explicitní vlastnosti.

Vlastnosti mohou být členy tříd, struktur, rozlišených sjednocení, záznamů, rozhraní a přípon typů a lze také definovat ve výrazech objektů.

Atributy lze použít pro vlastnosti. Chcete-li použít atribut na vlastnost, napište atribut na samostatném řádku před vlastností. Další informace najdete v tématu [atributy](../attributes.md).

Ve výchozím nastavení jsou vlastnosti veřejné. Modifikátory dostupnosti lze použít také pro vlastnosti. Chcete-li použít modifikátor přístupnosti, přidejte jej těsně před název vlastnosti, pokud má `get` být použita pro metody a `set` `get` ; přidejte před klíčovým slovem a `set` , pokud je různá přístupnost vyžaduje se pro každý přistupující objekt. *Modifikátor přístupnosti* může být jedna z následujících: `public`, `private`, `internal`. Další informace najdete v tématu [Access Control](../access-control.md).

Implementace vlastností jsou spouštěny pokaždé, když je k vlastnosti přistupovaná.

## <a name="static-and-instance-properties"></a>Statické a vlastnosti instance

Vlastnosti mohou být statické nebo vlastnosti instance. Statické vlastnosti lze vyvolat bez instance a jsou použity pro hodnoty přidružené k typu, nikoli s jednotlivými objekty. V případě statických vlastností vynechejte identifikátor držitele. Pro vlastnosti instance je vyžadován samočinný identifikátor.

Následující definice statických vlastností je založena na scénáři, ve kterém máte statické pole `myStaticValue` , které je záložním úložištěm pro danou vlastnost.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3204.fs)]

Vlastnosti mohou být také typu pole. v takovém případě se nazývají *indexované vlastnosti*. Další informace najdete v tématu [indexované vlastnosti](indexed-properties.md).

## <a name="type-annotation-for-properties"></a>Anotace typu pro vlastnosti

V mnoha případech má kompilátor dostatek informací pro odvození typu vlastnosti z typu záložního úložiště, ale můžete nastavit typ explicitně přidáním anotace typu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3205.fs)]

## <a name="using-property-set-accessors"></a>Použití přístupových objektů sady vlastností

Můžete nastavit vlastnosti, které poskytují `set` přístupové objekty `<-` pomocí operátoru.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3206.fs)]

Výstup je **20**.

## <a name="abstract-properties"></a>Abstraktní vlastnosti

Vlastnosti mohou být abstraktní. Stejně jako u metod `abstract` stačí pouze, když je k této vlastnosti přidruženo virtuální odeslání. Abstraktní vlastnosti mohou být skutečně abstraktní, to znamená bez definice ve stejné třídě. Třída, která obsahuje taková vlastnost, je tedy abstraktní třída. Alternativně může abstraktní pouze znamenat, že vlastnost je virtuální a v takovém případě musí být definice přítomna ve stejné třídě. Všimněte si, že abstraktní vlastnosti nesmí být privátní a pokud je jeden přistupující objekt abstraktní, druhý musí být také abstraktní. Další informace o abstraktních třídách naleznete v tématu [abstraktní třídy](../abstract-classes.md).

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3207.fs)]

## <a name="see-also"></a>Viz také:

- [Členové](index.md)
- [Metody](methods.md)
