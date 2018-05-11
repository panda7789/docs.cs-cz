---
title: Vlastnosti
description: Další informace o C# vlastnosti, které obsahují funkce pro ověření, počítaný hodnoty, opožděné vyhodnocení, a vlastnost změnit oznámení.
ms.date: 04/25/2018
ms.openlocfilehash: d4fa7b6117bec63c41318dd4bcc3850ce55a5907
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2018
---
# <a name="properties"></a>Vlastnosti

Vlastnosti jsou prvotřídní občanů v jazyce C#. Jazyk definuje syntaxi, která umožňuje vývojářům psát kód, který přesně vyjadřoval jejich záměr návrhu.

Vlastnosti chovat jako pole, když k nim.
Na rozdíl od pole, ale vlastnosti jsou u přistupující objekty, které definují příkazy spustit, když je vlastnost získat přístup nebo přiřazená implementován.

## <a name="property-syntax"></a>Syntaxe vlastností

Syntaxe vlastností v představuje přirozené rozšíření na pole. Pole definuje umístění úložiště:

[!code-csharp[Person class with public fields](../../samples/snippets/csharp/properties/Person.cs#1)]

Obsahuje deklarace pro definici vlastnosti `get` a `set` přistupujícího objektu, který načítá a přiřadí hodnota této vlastnosti:

[!code-csharp[Person class with public properties](../../samples/snippets/csharp/properties/Person.cs#2)]

Syntaxe uvedené výše je *automaticky vlastnost* syntaxe. Kompilátor generuje umístění úložiště pro pole, který zálohuje vlastnost. Kompilátor také implementuje text `get` a `set` přistupující objekty.

V některých případech je nutné inicializovat vlastnost na jinou hodnotu než výchozí u tohoto typu.  C# umožňuje který nastavením hodnoty po pravé složené závorce pro vlastnost. Dáte možná přednost počáteční hodnota `FirstName` vlastnost, která má být prázdný řetězec místo `null`. Zadáte, jak je uvedeno níže:

[!code-csharp[Person class with properties and initializer](../../samples/snippets/csharp/properties/Person.cs#3)]

Konkrétní inicializace je nejvhodnější pro vlastnosti jen pro čtení, jak uvidíte později v tomto článku.

Můžete také definovat úložiště sami, jak je uvedeno níže:

[!code-csharp[Person class with properties and backing field](../../samples/snippets/csharp/properties/Person.cs#4)]

Pokud implementace vlastností jeden výraz, můžete použít *výraz vozidlo členy* pro mechanismu získání nebo nastavení:

[!code-csharp[Person class with properties and expression bodied getters and setters](../../samples/snippets/csharp/properties/Person.cs#5)]

Tato zjednodušenou syntaxi se použije v případě potřeby v tomto článku.

Definici vlastnosti uvedené výše je vlastnost pro čtení a zápis. Všimněte si klíčové slovo `value` v přistupující objekt set. `set` Přistupujícího objektu má vždy jeden parametr s názvem `value`. `get` Přistupujícího objektu musí vracet hodnotu, která je převést na typ vlastnosti (`string` v tomto příkladu).

To je základní informace o syntaxi. Existuje mnoho různých variant, které podporují celou řadu různých idioms. Umožňuje prozkoumat a další možnosti syntaxe pro každou.

## <a name="scenarios"></a>Scénáře

Výše uvedených příkladech vám ukázal, jedním z nejjednodušších definice vlastnost: vlastnost pro čtení a zápis bez ověřování. Zápis kódu chcete `get` a `set` přístupové objekty, můžete vytvořit mnoho různých scénářů.

### <a name="validation"></a>Ověřování

Můžete napsat kód ve `set` přistupujícího objektu hodnoty reprezentována vlastnost musí být vždy platné. Předpokládejme například, pro jedno pravidlo `Person` třída je, že název nemůže být prázdný nebo mezer. By zápisu, následujícím způsobem:

[!code-csharp[Validating property setters](../../samples/snippets/csharp/properties/Person.cs#6)]

V předchozím příkladu můžete zjednodušit pomocí`throw` výrazu v rámci ověření Metoda setter vlastnosti:

[!code-csharp[Validating property setters](../../samples/snippets/csharp/properties/Person.cs#7)]

V předchozím příkladu vynucuje pravidlo, že křestní jméno nesmí být prázdný nebo mezer. Pokud vývojář zapíše

```csharp
hero.FirstName = "";
```

Vyvolá tuto přiřazení `ArgumentException`. Protože vlastnosti musí mít typ vrácené hodnoty void, sestavu chyb v přistupující objekt set podle došlo k výjimce.

Tato stejná syntaxe k ničemu potřeba ve vašem scénáři můžete rozšířit. Můžete zkontrolovat vztahy mezi různé vlastnosti nebo vyhodnotit proti případné externí podmínky. Všechny platné příkazy jazyka C# jsou platné v přistupujícího objektu vlastnosti.

### <a name="read-only"></a>jen pro čtení

V tomto okamžiku jsou všechny definice vlastností, které jste viděli vlastností čtení/zápisu s veřejné přistupující objekty. Toto není platné pouze pro usnadnění přístupu pro vlastnosti.
Můžete vytvořit vlastnosti jen pro čtení, nebo poskytnout jiné usnadnění přístupu k sadě a získat přístupové objekty. Předpokládat, že vaše `Person` třída měli jenom povolit změna hodnoty `FirstName` vlastnost z jiné metody v dané třídě. Může poskytnout přistupující objekt set `private` usnadnění místo `public`:

[!code-csharp[Using a private setter for a publicly readonly property](../../samples/snippets/csharp/properties/Person.cs#8)]

Nyní `FirstName` vlastnost je přístupná z žádný kód, ale lze přiřadit pouze z jiných kódu v `Person` třídy.

Můžete přidat všechny – modifikátor přístupu omezující buď sadu nebo získat přístupové objekty. Žádné – modifikátor přístupu u jednotlivých přistupujícího objektu musí být omezenější než – modifikátor přístupu na definici vlastnosti. Výše je právní protože `FirstName` vlastnost je `public`, ale je přistupující objekt set `private`. Nelze deklarovat `private` vlastnost s `public` přistupujícího objektu. Vlastnost deklarace lze také deklarovat `protected`, `internal`, `protected internal`, nebo i `private`.

Taky je platné umístit na víc omezující modifikátor `get` přistupujícího objektu. Například můžete mít `public` vlastnost, ale omezit `get` přistupujícího objektu `private`. Tento scénář se zřídka provádí v praxi.

Úpravy vlastností můžete taky omezit tak, aby lze nastavit pouze v konstruktoru nebo inicializátoru vlastnost. Můžete upravit `Person` třídy tak následujícím způsobem:

[!code-csharp[A readonly auto implemented property](../../samples/snippets/csharp/properties/Person.cs#9)]

Tato funkce se nejčastěji používá pro inicializaci kolekce, které jsou zveřejněné jako jen pro čtení vlastnosti:

```csharp
public class Measurements
{
    public ICollection<DataPoint> points { get; } = new List<DataPoint>();
}
```

### <a name="computed-properties"></a>Počítané vlastnosti

Vlastnost není nutné jednoduše vrátí hodnotu pole členů. Můžete vytvořit vlastnosti, které vracejí vypočtená hodnota. Umožňuje rozšířit `Person` objekt, který chcete vrátit úplný název, počítaný zřetězením názvy první a poslední:

[!code-csharp[A computed property](../../samples/snippets/csharp/properties/Person.cs#10)]

V příkladu výše používá [řetězec interpolace](../csharp/language-reference/tokens/interpolated.md) funkce vytvořit formátovaný řetězec pro úplný název.

Můžete použít také *výraz vozidlo člen*, který poskytuje více stručného způsob, jak vytvořit použití počítaných `FullName` vlastnost:

[!code-csharp[A computed property using an expression bodied member](../../samples/snippets/csharp/properties/Person.cs#11)]

*Výraz vozidlo členy* použít *výrazu lambda* syntaxe definovat metody, které obsahují jeden výraz. Tento výraz zde, vrátí úplný název pro objekt osoby.

### <a name="cached-evaluated-properties"></a>V mezipaměti vyhodnotí vlastnosti

Můžete kombinovat koncept vypočítané vlastnosti s úložištěm a vytvořit *mezipaměti vyhodnotí vlastnost*.  Například můžete aktualizovat `FullName` vlastnost tak, aby formátování řetězce pouze došlo při prvním byl přístup:

[!code-csharp[Caching the value of a computed property](../../samples/snippets/csharp/properties/Person.cs#12)]

Výše uvedený kód obsahuje chybu, když. Pokud kód aktualizace hodnotu buď `FirstName` nebo `LastName` vlastnost, dříve vyhodnotí `fullName` pole je neplatné. Můžete změnit `set` přístupových objektů `FirstName` a `LastName` vlastnost tak, aby `fullName` pole se vypočítává znovu:

[!code-csharp[Invalidating the cache correctly](../../samples/snippets/csharp/properties/Person.cs#13)]

Vyhodnotí této poslední verzi `FullName` vlastnost pouze v případě potřeby.
Pokud je platný dříve počítané verze, se používá. Další změnou stavu by způsobila neplatnost dříve počítané verze, bude přepočítána. Vývojáři, které používají tuto třídu není potřeba znát podrobnosti implementace. Žádná z těchto interní změny mají vliv na použití objektu osoby. To je klíče důvod pomocí vlastnosti vystavit data členům v objektu.

### <a name="attaching-attributes-to-auto-implemented-properties"></a>Atributy se připojuje k automaticky implementované vlastnosti

Počínaje 7.3 C#, atributy pole lze připojit k poli kompilátoru generované zálohování v automaticky implementované vlastnosti. Představte si třeba revize k `Person` třída, která přidává jedinečné číslo `Id` vlastnost.
Psaní`Id` vlastnost pomocí ve automaticky implementované vlastnosti, ale váš návrh nevyvolá pro uchování `Id` vlastnost. <xref:System.NonSerializedAttribute> Lze připojit pouze na pole není vlastnosti. Můžete připojit <xref:System.NonSerializedAttribute> základní pole pro `Id` vlastnost pomocí `field:` specifikátor pro atribut, jak je znázorněno v následujícím příkladu:

[!code-csharp[Attaching attributes to a backing field](../../samples/snippets/csharp/properties/Person.cs#14)]

Tento postup funguje pro všechny atributy, které můžete připojit k poli zálohování na automaticky implementované vlastnosti.

### <a name="implementing-inotifypropertychanged"></a>Implementace rozhraní INotifyPropertyChanged.

Poslední scénář, kde je potřeba psát kód v přistupujícího objektu vlastnosti je podpora <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní sloužící k upozornění klientů vazby dat, která byla hodnota změněna. Při změně hodnoty vlastnosti, vyvolá objekt <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged?displayProperty=nameWithType> události označit změny. Datové vazby knihovny, pak aktualizovat zobrazení prvky založené na tuto změnu. Následující kód ukazuje, jak můžete implementovat `INotifyPropertyChanged` pro `FirstName` vlastnost této třídy osoby.

[!code-csharp[invalidating the cache correctly](../../samples/snippets/csharp/properties/Person.cs#15)]

`?.` Operátor je volána *null podmíněný operátor*. Před vyhodnocením pravé straně operátoru zkontroluje pro odkaz s hodnotou null. Konečným výsledkem je, že pokud neexistují žádné odběratele, kteří mají `PropertyChanged` událostí, neprovede se kód pro vyvolání události. By throw `NullReferenceException` bez zkontrolujte v takovém případě. Další informace najdete na webu [`events`](delegates-events.md). Tento příklad také používá nové `nameof` operátor převést z názvu symbolu vlastnost textové reprezentace.
Pomocí `nameof` můžete snížit počet chyb, které jste zadali název vlastnosti.

Znovu implementace <xref:System.ComponentModel.INotifyPropertyChanged> je příklad případu, kde můžete napsat kód ve vaší přístupových objektů pro podporu scénářů, budete potřebovat.

## <a name="summing-up"></a>Shrnutí

Vlastnosti jsou formuláře inteligentních polí ve třídě nebo objekt. Z mimo objekt, zobrazí se jako pole v objektu. Však vlastnosti se dají implementovat pomocí úplné palety funkcí jazyka C#.
Můžete zadat ověřování, jiný usnadnění, opožděné vyhodnocení nebo všechny požadavky potřebné pro vaše scénáře.
