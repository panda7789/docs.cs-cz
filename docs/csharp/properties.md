---
title: Vlastnosti
description: Další informace o C# vlastnosti, jako je například funkce pro ověření, vypočítané hodnoty, opožděné vyhodnocení, a vlastnost změnit oznámení.
ms.date: 04/25/2018
ms.openlocfilehash: e8b6955da1f36673962339785b0bfb012343acf8
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65878280"
---
# <a name="properties"></a>Vlastnosti

Vlastnosti jsou první třídy občanům v C#. Jazyk definuje syntaxe, která vývojářům umožňuje psát kód, který se přesně vyjadřoval jejich návrhu záměr.

Vlastnosti se chovat jako pole, když k nim přistupovat.
Na rozdíl od pole, ale vlastnosti jsou implementovány s přístupové objekty, které definují příkazy, které jsou spouštěny, když je vlastnost přistupovat ani přiřazené.

## <a name="property-syntax"></a>Syntaxe vlastnosti

Syntaxe vlastností je přirozeným pole. Pole určuje umístění úložiště:

[!code-csharp[Person class with public fields](../../samples/snippets/csharp/properties/Person.cs#1)]

Definice vlastnosti obsahuje deklarace `get` a `set` přístupový objekt, který načte a přiřadí hodnotu této vlastnosti:

[!code-csharp[Person class with public properties](../../samples/snippets/csharp/properties/Person.cs#2)]

Syntaxe uvedené výše je *auto vlastnost* syntaxe. Kompilátor generuje umístění úložiště pro pole, který zálohuje vlastnost. Kompilátor také implementuje text `get` a `set` přistupující objekty.

V některých případech je nutné inicializovat vlastnost, která má jinou hodnotu než výchozí nastavení pro jeho typu.  C#který umožňuje tak, že nastavíte hodnotu po pravé složené závorce pro vlastnost. Možná dáte přednost počáteční hodnotu `FirstName` vlastnost jako prázdný řetězec spíše než `null`. By určíte, jak je znázorněno níže:

[!code-csharp[Person class with properties and initializer](../../samples/snippets/csharp/properties/Person.cs#3)]

Konkrétní inicializační je zvláště užitečná pro vlastnosti jen pro čtení, jak uvidíte později v tomto článku.

Můžete také definovat úložiště sami, jak je znázorněno níže:

[!code-csharp[Person class with properties and backing field](../../samples/snippets/csharp/properties/Person.cs#4)]

Pokud provádění vlastnost je jediný výraz, můžete použít *členové tvoření* pro getter nebo setter:

[!code-csharp[Person class with properties and expression bodied getters and setters](../../samples/snippets/csharp/properties/Person.cs#5)]

Tato zjednodušenou syntaxi se použije, případně v celém tomto článku.

Definice vlastnosti uvedené výše je vlastnost pro čtení i zápis. Všimněte si, že klíčové slovo `value` přístupového objektu set. `set` Přístupového objektu má vždy jeden parametr s názvem `value`. `get` Přístupového objektu musí vracet hodnotu, která je převoditelná na typ proměnné (`string` v tomto příkladu).

To je základní informace o syntaxi. Existuje mnoho různých změn, které podporují širokou škálu návrhů idiomy. Pojďme prozkoumat a další možnosti syntaxe pro každý.

## <a name="scenarios"></a>Scénáře

Výše uvedené příklady nám ukázaly, jedním z nejjednodušší případů definici vlastnosti: vlastnost pro čtení a zápis bez ověřování. Napsáním kódu, které chcete v `get` a `set` přístupové objekty, můžete vytvořit mnoho různých scénářů.

### <a name="validation"></a>Ověřování

Můžete napsat kód `set` přistupující k zajištění, že je vlastnost reprezentována jsou hodnoty vždycky platné. Předpokládejme například, že jedno pravidlo pro `Person` třída je, že název nemůže být prázdné nebo prázdný znak. Měli byste napsat následující:

[!code-csharp[Validating property setters](../../samples/snippets/csharp/properties/Person.cs#6)]

V předchozím příkladu se dá zjednodušit pomocí`throw` výraz jako součást ověření setter vlastnosti:

[!code-csharp[Validating property setters](../../samples/snippets/csharp/properties/Person.cs#7)]

Výše uvedený příklad vynucuje pravidla, křestní jméno nesmí být prázdné nebo prázdný znak. Pokud vývojář zapíše

```csharp
hero.FirstName = "";
```

Vyvolá přiřazení `ArgumentException`. Protože přístupový objekt set vlastnosti musí mít typ vrácené hodnoty void, vám umožňuje nahlásit chyby u přístupového objektu set vyvoláním výjimky.

Tahle stejné syntaxe cokoli, co je potřeba ve vašem scénáři můžete rozšířit. Můžete zkontrolovat vztahy mezi různými vlastnostmi nebo ověřovat proti všechny externí podmínky. Libovolný platný C# příkazy jsou platné v přistupujícího objektu vlastnosti.

### <a name="read-only"></a>jen pro čtení

Do této chvíle jsou všechny definice vlastností, které jste viděli vlastností čtení/zápisu s veřejnou přistupující objekty. To není jenom platné usnadnění přístupu pro vlastnosti.
Můžete vytvořit vlastnosti jen pro čtení, nebo poskytují různou přístupností. do sady a získat přístupové objekty. Předpokládejme, že vaše `Person` třída by měla pouze povolit, změna hodnoty `FirstName` vlastnost z jiné metody v dané třídě. Můžete zadat přístupový objekt set `private` usnadnění místo `public`:

[!code-csharp[Using a private setter for a publicly readonly property](../../samples/snippets/csharp/properties/Person.cs#8)]

Nyní `FirstName` vlastnost je přístupná z jakéhokoli kódu, ale lze přiřadit pouze od jiného kódu v `Person` třídy.

Můžete přidat libovolné modifikátor omezující přístupová buď sadu nebo získat přístupové objekty. Žádné modifikátor přístupu, který umístíte na jednotlivé přístupový objekt musí být omezeny více než modifikátor přístupu v definici vlastnosti. Výše uvedené je právní protože `FirstName` vlastnost `public`, ale přistupující objekt Jet není `private`. Nelze deklarovat `private` vlastnost s `public` přistupujícího objektu. Deklarace vlastností lze také deklarovat `protected`, `internal`, `protected internal`, nebo dokonce `private`.

Je také možné umístit na víc omezující modifikátor `get` přistupujícího objektu. Například můžete mít `public` vlastnost, ale omezit `get` přístupového objektu `private`. Tento scénář se jen zřídka provádí v praxi.

Můžete také omezit změny vlastnosti tak, aby lze nastavit pouze v konstruktoru nebo inicializátoru vlastnost. Můžete upravit `Person` třídy to následujícím způsobem:

[!code-csharp[A readonly auto implemented property](../../samples/snippets/csharp/properties/Person.cs#9)]

Tato funkce se nejčastěji používá pro inicializaci kolekce, které jsou vystaveny jako vlastnosti jen pro čtení:

```csharp
public class Measurements
{
    public ICollection<DataPoint> points { get; } = new List<DataPoint>();
}
```

### <a name="computed-properties"></a>Vypočítané vlastnosti

Vlastnost není potřeba jednoduše vrátit hodnotu člena pole. Můžete vytvořit vlastnosti, které vrací vypočítanou hodnotu. Můžeme rozšířit `Person` objekt vrátí úplný název, počítaný zřetězením jména a příjmení:

[!code-csharp[A computed property](../../samples/snippets/csharp/properties/Person.cs#10)]

V příkladu výše používá [interpolace](../csharp/language-reference/tokens/interpolated.md) funkci pro vytvoření formátovaný řetězec pro úplný název.

Můžete také použít *s výrazem v těle členské*, která poskytuje stručnější způsob, jak vytvořit počítaných `FullName` vlastnost:

[!code-csharp[A computed property using an expression bodied member](../../samples/snippets/csharp/properties/Person.cs#11)]

*Členové tvoření* použít *výraz lambda* syntaxe pro definování metod, které obsahují jeden výraz. Tady tento výraz vrátí úplný název objektu osoba.

### <a name="cached-evaluated-properties"></a>Vyhodnocený vlastnostem uloženým v mezipaměti

Můžete kombinovat koncept vypočítané vlastnosti s úložištěm a vytvářet *uložené v mezipaměti Vyhodnocená vlastnost*.  Například můžete aktualizovat `FullName` vlastnost tak, aby formátování řetězce pouze se stalo se použila poprvé:

[!code-csharp[Caching the value of a computed property](../../samples/snippets/csharp/properties/Person.cs#12)]

Výše uvedený kód však obsahuje chybu. Pokud kód aktualizuje hodnotu buď `FirstName` nebo `LastName` vlastnost, dříve Vyhodnocená `fullName` pole je neplatné. Můžete změnit `set` přistupující objekty `FirstName` a `LastName` vlastnost tak, aby `fullName` pole se vypočítá znovu:

[!code-csharp[Invalidating the cache correctly](../../samples/snippets/csharp/properties/Person.cs#13)]

Tento poslední verze vyhodnocuje `FullName` vlastnost jenom v případě potřeby.
Pokud dříve vypočtené verze je platný, se používá. Pokud jiná změna stavu zruší platnost dříve vypočtené verze, bude přepočítat. Vývojáři, kteří tuto třídu použít, není potřeba znát podrobnosti implementace. Žádná z těchto změn mají vliv na použití objektu osoba. To je důvod klíče pro použití vlastností ke zveřejnění datové členy objektu.

### <a name="attaching-attributes-to-auto-implemented-properties"></a>Atributy se připojuje k automaticky implementované vlastnosti

Počínaje C# 7.3, atributy polí lze připojit k pomocným polem generované kompilátorem v automaticky implementované vlastnosti. Představte si třeba revizi `Person` třídu, která přidá jedinečné celé `Id` vlastnost.
Při psaní`Id` vlastnost pomocí automaticky implementované vlastnosti, ale váš návrh nevolá pro trvalé `Id` vlastnost. <xref:System.NonSerializedAttribute> Lze připojit pouze na pole, nikoli vlastnosti. Můžete připojit <xref:System.NonSerializedAttribute> na pomocné pole `Id` vlastnost s použitím `field:` specifikátor atributu, jak je znázorněno v následujícím příkladu:

[!code-csharp[Attaching attributes to a backing field](../../samples/snippets/csharp/properties/Person.cs#14)]

Tento postup funguje pro všechny atributy, které můžete připojit na automaticky implementované vlastnosti pole zálohování.

### <a name="implementing-inotifypropertychanged"></a>Implementace rozhraní INotifyPropertyChanged.

Poslední scénář, kde budete muset psát kód v přistupující objekt vlastnosti je podpora <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní používá k upozornění klientů vazby dat, které byla hodnota změněna. Při změně hodnoty vlastnosti, vyvolá objekt <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged?displayProperty=nameWithType> událost označující změnu. Datové vazby knihovny, zase aktualizaci založené na tuto změnu zobrazení elementů. Následující kód ukazuje, jak by implementovat `INotifyPropertyChanged` pro `FirstName` vlastnosti třídy této osoby.

[!code-csharp[invalidating the cache correctly](../../samples/snippets/csharp/properties/Person.cs#15)]

`?.` Operátor je volána *null podmiňovací operátor*. Před vyhodnocením pravé straně operátoru zkontroluje odkaz s hodnotou null. Konečným výsledkem je, že pokud neexistují žádné Odběratelé `PropertyChanged` událostí, nebude spouštět kód pro vyvolání události. To vede `NullReferenceException` bez to zkontrolovat v takovém případě. Další informace najdete na webu [`events`](events-overview.md). Tento příklad také používá nový `nameof` operátor převodu ze symbolů vlastnost název na jeho textové vyjádření.
Pomocí `nameof` může snížit chyby, kde jste zadali název vlastnosti.

Znovu, implementace <xref:System.ComponentModel.INotifyPropertyChanged> je příkladem případem, kde psát kód v vaše přístupové objekty pro zajištění podpory scénářů, které potřebujete.

## <a name="summing-up"></a>Shrnutí

Vlastnosti jsou formou inteligentních polí ve třídě nebo objekt. Z mimo objektu, zobrazí se jako pole v objektu. Nicméně vlastnosti je možné implementovat pomocí úplné paletu C# funkce.
Můžete zadat ověření, různou přístupností, opožděné vyhodnocení nebo všechny požadavky potřebné pro vaše scénáře.
