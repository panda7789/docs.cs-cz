---
title: Vlastnosti (F#)
description: 'Další informace o F # vlastnosti, které jsou členy, které představují hodnoty přidružené k objektu.'
ms.date: 05/16/2016
ms.openlocfilehash: 75d21415b44ccc1c26ef5f478d5f5de20c3412e8
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2018
ms.locfileid: "46481777"
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

Vlastnosti představují "má" relace v objektově orientované programování, představující data, která souvisí s instancí objektů nebo statických vlastností s typem.

Můžete deklarovat vlastnosti dvěma způsoby v závislosti na tom, jestli chcete explicitně zadat zdrojovou hodnotu (také nazývané záložní úložiště) pro vlastnost, nebo pokud budete chtít povolit kompilátor automaticky generovat záložní úložiště pro vás. Obecně platí měli byste použít více explicitní způsob, pokud má vlastnost nejsou v netriviálních implementace a automatický způsob při vlastnost je stejně jednoduchá obálka pro hodnotu nebo proměnnou. Chcete-li explicitně deklarovat vlastnost, použijte `member` – klíčové slovo. Tato deklarativní syntaxe je následována syntaxi, která určuje, `get` a `set` metody, také s názvem *přistupující objekty*. Různé formy explicitní syntaxe uvedené v části Syntaxe se používají pro vlastnosti jen pro čtení a zápisu jen pro čtení a zápis. Pro vlastnosti jen pro čtení, můžete definovat pouze `get` metoda; pouze pro vlastnosti jen pro zápis, definovat `set` metoda. Všimněte si, že pokud má vlastnost obě `get` a `set` přístupové objekty, alternativní syntaxi vám umožní určit atributy a modifikátory dostupnosti, které se liší pro každý přistupující objekt, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3201.fs)]

Pro vlastnosti čtení/zápis, které mají obojí `get` a `set` metody, pořadí `get` a `set` je možné vrátit zpět. Alternativně můžete poskytnout tomu syntaxe uvedená pro `get` pouze a syntaxe pro `set` pouze místo kombinované syntaxe. To usnadňuje Odkomentujte jednotlivých `get` nebo `set` metodu, pokud je to něco možná bude potřeba provést. Tuto alternativu k použití kombinované syntaxe se zobrazí v následujícím kódu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3203.fs)]

Soukromé hodnoty tohoto uchování dat pro vlastnosti se nazývají *zálohování úložišť*. Pokud chcete, aby kompilátor automaticky vytvořit záložní úložiště, pomocí klíčových slov `member val`, vynechejte vlastní identifikátor a pak zadejte výraz k inicializaci vlastnosti. Pokud je vlastnost má být proměnlivá, obsahovat `with get, set`. Například následující typ třída obsahuje dva automaticky implementované vlastnosti. `Property1` je jen pro čtení a je inicializován na argumentu poskytnutému metodě primárnímu konstruktoru a `Property2` je nastavitelnou vlastnost inicializovat na prázdný řetězec:

```fsharp
type MyClass(property1 : int) =
member val Property1 = property1
member val Property2 = "" with get, set
```

Automaticky implementované vlastnosti jsou součástí inicializace typu, takže musí být obsažena před další definice členů stejně jako `let` vazby a `do` vazby v definici typu. Všimněte si, že výraz, který inicializuje automaticky implementovanou vlastnost je vyhodnocen pouze při inicializaci, a ne vždy, když přistupuje k vlastnosti. Toto chování se liší od chování explicitně implementovaná vlastnost. Co to efektivně znamená, že kód pro inicializaci tyto vlastnosti se přidá do konstruktoru třídy. Vezměte v úvahu následující kód, který ukazuje rozdíl:

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

Výstup předcházejícího kódu ukazuje, že hodnota AutoProperty beze změny při volání opakovaně, že ExplicitProperty změní pokaždé, když je volána. Tento příklad ukazuje, že výraz pro automaticky implementovanou vlastnost není vyhodnocen pokaždé, když, jako je metoda getter pro explicitní vlastnost.

>[!WARNING]
Existují některé knihovny, jako je například rozhraní Entity Framework (`System.Data.Entity`), které provádí vlastní operace v konstruktory základní třídy, které nefungují dobře v inicializaci automaticky implementované vlastnosti. V těchto případech použijte explicitní vlastnosti.

Vlastnosti můžou být členy třídy, struktury, rozlišovaná sjednocení, záznamy, rozhraní a rozšíření typu a lze také definovat v objektových výrazech.

Atributy lze použít k vlastnosti. Použijte atribut na vlastnost, zapisovat atribut na samostatný řádek před vlastnost. Další informace najdete v tématu [atributy](../attributes.md).

Ve výchozím nastavení jsou veřejné vlastnosti. Modifikátory dostupnosti lze použít také k vlastnostem. Použít modifikátor přístupnosti, vraťte ho bezprostředně před název vlastnosti, pokud je určená k použití pro obě `get` a `set` metody; přidat před `get` a `set` klíčová slova, pokud je různou přístupností. vyžaduje se pro každý přistupující objekt. *Modifikátor dostupnosti* může být jedna z následujících akcí: `public`, `private`, `internal`. Další informace najdete v tématu [řízení přístupu](../access-control.md).

Implementace vlastnosti provádějí pokaždé, když přistupuje k vlastnosti.

## <a name="static-and-instance-properties"></a>Statické a vlastnosti Instance

Vlastnosti mohou být statické nebo vlastnosti instance. Statické vlastnosti může být vyvolána bez instance a používají se pro hodnoty přidružené k typu, nikoli se jednotlivé objekty. Statické vlastnosti vynechejte vlastní identifikátor. Je vyžadován pro vlastnosti instance vlastní identifikátor.

Následující definice statickou vlastnost je založena na situaci, ve kterém máte statické pole `myStaticValue` , který je záložní úložiště pro vlastnost.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3204.fs)]

Vlastnosti může být také jako pole, v takovém případě se nazývají *indexovaných vlastností*. Další informace najdete v tématu [indexované vlastnosti](indexed-properties.md).

## <a name="type-annotation-for-properties"></a>Anotace typu vlastnosti

V mnoha případech kompilátor má dostatek informací k odvození typu vlastnosti z typu záložního úložiště, ale typ můžete explicitně nastavit tak, že přidáte anotaci typu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3205.fs)]

## <a name="using-property-set-accessors"></a>Pomocí vlastnosti přístupové objekty set

Můžete nastavit vlastnosti, které poskytují `set` přístupové objekty pomocí `<-` operátor.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3206.fs)]

Výstup je **20**.

## <a name="abstract-properties"></a>Abstraktní vlastnosti

Vlastnosti mohou být abstraktní. Stejně jako u metod, `abstract` právě znamená, že je virtuální odeslání přidružený k vlastnosti. Může být abstraktních a vlastností skutečně abstract, to znamená bez definice ve stejné třídě. Třída, která obsahuje tato vlastnost je proto abstraktní třídu. Abstraktní Alternativně právě může znamenat, že vlastnost je virtuální a v takovém případě definice musí existovat ve stejné třídě. Všimněte si, že abstraktních a vlastností nesmí být privátní, a pokud jeden přistupující objekt je abstraktní, ostatní musí také být abstraktní. Další informace o abstraktních tříd naleznete v tématu [abstraktní třídy](../abstract-classes.md).

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3207.fs)]

## <a name="see-also"></a>Viz také:

- [Členové](index.md)
- [Metody](methods.md)
