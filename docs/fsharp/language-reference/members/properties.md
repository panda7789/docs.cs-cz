---
title: Vlastnosti (F#)
description: 'Další informace o F # vlastnosti, které jsou členy, které reprezentují hodnoty přidružené k objektu.'
ms.date: 05/16/2016
ms.openlocfilehash: 7aa71b1801b44fedcb420b824078004c6c240dc2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="properties"></a>Vlastnosti

*Vlastnosti* jsou členy, které reprezentují hodnoty přidružené k objektu.


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
Vlastnosti představují "má" vztahu v rámci objektově orientované programování reprezentující data, která souvisí s instancí objektů nebo statických vlastností s typem.

Vlastnosti dvěma způsoby v závislosti na tom, jestli chcete explicitně zadat základní hodnotu (označovanou taky jako úložiště zálohování) pro vlastnost, nebo pokud chcete povolit kompilátor automaticky generuje úložiště zálohování pro vás můžou deklarovat. Obecně byste měli použít podrobnější způsob, pokud má vlastnost netriviální implementace a automatické způsob při vlastnost je stejně jednoduché obálku pro hodnota nebo proměnná. Chcete-li explicitně deklarace vlastnosti, použijte `member` – klíčové slovo. Tato deklarativní syntaxe následuje syntaxi, která určuje, `get` a `set` metody, také s názvem *přístupové objekty*. Vlastnosti jen pro čtení a zápisu jen pro čtení a zápis, se používají různé formy explicitní syntaxi uvedenou v části syntaxe. Vlastnosti jen pro čtení, můžete definovat jenom `get` metoda; pouze pro vlastnosti jen pro zápis, definovat `set` metoda. Všimněte si, že pokud má vlastnost obě `get` a `set` přístupových objektů, alternativní syntaxe umožňuje určit atributy a modifikátory usnadnění, které se liší pro každý přistupující objekt, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3201.fs)]

Pro vlastnosti čtení/zápisu, které oba `get` a `set` metoda, pořadí `get` a `set` lze vrátit zpět. Alternativně můžete zadat syntaxi uvedenou pro `get` pouze a syntaxe pro `set` pouze místo použití kombinované syntaxe. To usnadňuje komentář jednotlivých `get` nebo `set` metodu, pokud je něco možná budete muset provést. Následující kód ukazuje tento alternativu k použití kombinované syntaxe.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3203.fs)]

Soukromé hodnoty tohoto uchování data pro vlastnosti se nazývají *záložnímu úložišti*. Pokud chcete, aby kompilátoru záložní úložiště vytvářet automaticky, použijte klíčová slova `member val`, vynechejte vlastní identifikátor, a zadejte výraz k inicializaci vlastnosti. Pokud má-li být měnitelný vlastnost, zahrnout `with get, set`. Například následující typ třídy obsahuje dvě automaticky implementované vlastnosti. `Property1` je jen pro čtení a je inicializováno argument poskytnutý primární konstruktoru, a `Property2` se nastavit vlastnost inicializovat na prázdný řetězec:

```fsharp
type MyClass(property1 : int) =
member val Property1 = property1
member val Property2 = "" with get, set
```

Automaticky implementované vlastnosti jsou součástí inicializace typu, proto musí být obsažena před jiné definice člen podobně jako `let` vazby a `do` vazby v definici typu. Všimněte si, že výraz, který inicializuje automaticky implementované vlastnosti je Vyhodnocená jenom po inicializaci a není pokaždé, když vlastnost přistupuje. Toto chování se liší od chování – explicitně implementovaná vlastnost. Co to znamená, je, že kód pro inicializaci tyto vlastnosti se přidá do konstruktoru třídy. Vezměte v úvahu následující kód, který ukazuje tento rozdíl:

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

```
class1.AutoProperty = 1853799794
class1.AutoProperty = 1853799794
class1.ExplicitProperty = 978922705
class1.ExplicitProperty = 1131210765
```

Výstup předchozí kód ukazuje, že hodnota AutoProperty je beze změny při volání opakovaně, zatímco ExplicitProperty změní pokaždé, když je volána. To znamená, že výraz automaticky implementované vlastnosti není vyhodnocen pokaždé, když, jako je metoda getter pro explicitní vlastnost.


>[!WARNING]
Existují některé knihovny, například rozhraní Entity Framework (`System.Data.Entity`), provádění vlastních operací v konstruktorech základní třídu, která nejsou dobře fungují s inicializace automaticky implementované vlastnosti. V takových případech použijte explicitní vlastnosti.

Vlastnosti mohou být členy třídy, struktury, rozlišovaná sjednocení, záznamy, rozhraní a typ rozšíření a může být také definováno v objektové výrazy.

Atributy lze použít jako vlastnosti. Použít atribut na vlastnost, zapište na samostatném řádku před vlastnost atribut. Další informace najdete v tématu [atributy](../attributes.md).

Ve výchozím nastavení jsou veřejné vlastnosti. Modifikátory usnadnění přístupu lze použít také k vlastnostem. Použít usnadnění modifikátor, přidejte ho bezprostředně před název vlastnosti, pokud smyslem je chcete použít pro obě `get` a `set` metody; přidejte ho před `get` a `set` klíčová slova, pokud je jiný pro usnadnění přístupu vyžaduje se pro každý přistupující objekt. *Modifikátor dostupnosti* může být jedna z následujících: `public`, `private`, `internal`. Další informace najdete v tématu [řízení přístupu](../access-control.md).

Vlastnost implementace jsou spouštěny pokaždé, když vlastnost přistupuje.


## <a name="static-and-instance-properties"></a>Statické a instanci vlastnosti
Vlastnosti můžou být statické nebo vlastnosti instance. Statické vlastnosti může být volána bez instance a jsou používány pro hodnoty související s typem, ne při jednotlivých objektů. Statické vlastnosti vynechejte vlastní identifikátor. Je vyžadován pro vlastnosti instance vlastní identifikátor.

Následující definice statické vlastnosti je založena na situaci, ve kterém máte statické pole `myStaticValue` tedy úložiště zálohování pro vlastnost.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3204.fs)]

Vlastnosti může být také jako pole, v takovém případě se nazývají *indexovaných vlastností*. Další informace najdete v tématu [indexované vlastnosti](indexed-properties.md).


## <a name="type-annotation-for-properties"></a>Anotaci typu vlastností
V mnoha případech kompilátor má dostatek informací k odvození typu vlastnosti z typu záložnímu úložišti, ale můžete nastavit typ explicitně přidáním anotaci typu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3205.fs)]

## <a name="using-property-set-accessors"></a>Pomocí vlastnosti nastavení přístupových objektů
Můžete nastavit vlastnosti, které poskytují `set` přístupových objektů pomocí `<-` operátor.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3206.fs)]

Výstupem je **20**.


## <a name="abstract-properties"></a>Abstraktní vlastnosti
Vlastnosti mohou být abstraktní. Stejně jako u metod `abstract` právě znamená, že je virtuální odesílání přidružená vlastnost. Abstraktní vlastnosti mohou být skutečně abstraktní, to znamená, bez definice ve stejné třídě. Třída, která obsahuje tato vlastnost je proto abstraktní třídu. Abstraktní Alternativně můžete znamenají právě, že je vlastnost virtuální a definice v takovém případě musí být součástí stejné třídy. Všimněte si, že abstraktních a vlastností nesmí být privátní, a pokud jednoho přístupového objektu je abstraktní, dalších také musí být abstraktní. Další informace o abstraktní třídy najdete v tématu [abstraktní třídy](../abstract-classes.md).

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3207.fs)]

## <a name="see-also"></a>Viz také
[Členové](index.md)

[Metody](methods.md)
