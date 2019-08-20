---
title: Vlastnosti
description: Přečtěte C# si o vlastnostech, které zahrnují funkce pro ověřování, vypočítané hodnoty, opožděné vyhodnocení a oznámení o změně vlastností.
ms.date: 04/25/2018
ms.openlocfilehash: 6638ae74516d7546882c8a380eed9b03ff3d18e9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587399"
---
# <a name="properties"></a>Vlastnosti

Vlastnosti jsou prvními občany třídy C#v. Jazyk definuje syntaxi, která umožňuje vývojářům psát kód, který přesně vyjadřuje jejich záměr návrhu.

Vlastnosti se chovají jako pole při jejich použití.
Nicméně na rozdíl od polí jsou vlastnosti implementovány pomocí přistupujících objektů, které definují příkazy provedené při přístupu nebo přiřazení vlastnosti.

## <a name="property-syntax"></a>Syntaxe vlastnosti

Syntaxe vlastností je přirozené rozšíření polí. Pole definuje umístění úložiště:

[!code-csharp[Person class with public fields](../../samples/snippets/csharp/properties/Person.cs#1)]

Definice vlastnosti obsahuje deklarace pro `get` přistupující objekt a `set` , který načte a přiřadí hodnotu této vlastnosti:

[!code-csharp[Person class with public properties](../../samples/snippets/csharp/properties/Person.cs#2)]

Syntaxe uvedená výše je syntaxe *Automatické vlastnosti* . Kompilátor vygeneruje umístění úložiště pro pole, které zálohuje vlastnost. Kompilátor také implementuje tělo `get` a `set` přistupující objekty.

V některých případech je nutné inicializovat vlastnost na jinou hodnotu než výchozí pro svůj typ.  C#umožňuje nastavit hodnotu za pravou závorkou pro vlastnost. Můžete upřednostnit počáteční hodnotu `FirstName` vlastnosti jako prázdný řetězec, `null`nikoli. Zadejte, jak je uvedeno níže:

[!code-csharp[Person class with properties and initializer](../../samples/snippets/csharp/properties/Person.cs#3)]

Konkrétní inicializace je nejužitečnější pro vlastnosti určené jen pro čtení, jak je uvedeno dále v tomto článku.

Úložiště můžete také definovat sami, jak je znázorněno níže:

[!code-csharp[Person class with properties and backing field](../../samples/snippets/csharp/properties/Person.cs#4)]

Pokud je implementací vlastnosti jeden výraz, můžete použít *členy Expression-těle* pro metodu getter nebo setter:

[!code-csharp[Person class with properties and expression bodied getters and setters](../../samples/snippets/csharp/properties/Person.cs#5)]

Tato zjednodušená syntaxe se použije, pokud je to možné v celém rámci tohoto článku.

Výše uvedená definice vlastnosti je vlastnost pro čtení i zápis. Všimněte si klíčového slova `value` v přístupovém objektu set. Přistupující objekt má vždycky jeden parametr s názvem `value`. `set` Přistupující objekt musí vracet hodnotu, která je převoditelná na typ vlastnosti (`string` v tomto příkladu). `get`

Základní informace o syntaxi. Existuje mnoho různých variant, které podporují různé idiomy návrhu. Pojďme se podívat na Možnosti syntaxe pro každý z nich.

## <a name="scenarios"></a>Scénáře

Výše uvedené příklady ukázaly jeden z nejjednodušších případů definice vlastnosti: vlastnost pro čtení i zápis bez ověřování. Psaním kódu, který chcete v `get` přístupových, a `set` můžete vytvořit mnoho různých scénářů.

### <a name="validation"></a>Ověřování

V `set` přistupujícím objektu můžete napsat kód, aby se zajistilo, že hodnoty reprezentované vlastností jsou vždycky platné. Předpokládejme například, že jedno pravidlo pro `Person` třídu je, že název nemůže být prázdný nebo obsahovat prázdné znaky. Zapíšete to takto:

[!code-csharp[Validating property setters](../../samples/snippets/csharp/properties/Person.cs#6)]

Předchozí příklad lze zjednodušit pomocí`throw` výrazu jako součást ověřování vlastností setter:

[!code-csharp[Validating property setters](../../samples/snippets/csharp/properties/Person.cs#7)]

Výše uvedený příklad vynutil pravidlo, že první název nesmí být prázdný nebo obsahovat prázdné znaky. Pokud Vývojář zapíše

```csharp
hero.FirstName = "";
```

Toto přiřazení vyvolá `ArgumentException`výjimku. Vzhledem k tomu, že přístupový objekt set vlastnosti musí mít návratový typ void, nahlásíte chybu v přístupovém objektu set vyvoláním výjimky.

Stejnou syntaxi můžete ve svém scénáři roztáhnout na cokoli potřebné. Můžete zkontrolovat vztahy mezi různými vlastnostmi nebo je ověřit proti jakýmkoli externím podmínkám. V přistupujícím objektu vlastnosti jsou platné všechny platné C# příkazy.

### <a name="read-only"></a>Jen pro čtení

Až do tohoto okamžiku se zobrazí všechny definice vlastností, které jste viděli, do vlastností pro čtení a zápis s veřejnými přistupujícími objekty. Nejedná se o jedinou platnou přístupnost pro vlastnosti.
Můžete vytvořit vlastnosti jen pro čtení nebo udělit přístup k množině a přístupovým modulům přístupu jiným uživatelům. Předpokládejme, že `Person` vaše třída by měla povolit pouze změnu hodnoty `FirstName` vlastnosti z jiných metod v této třídě. Můžete nastavit přístupnost přístupového objektu `private` `public`místo:

[!code-csharp[Using a private setter for a publicly readonly property](../../samples/snippets/csharp/properties/Person.cs#8)]

Nyní může `Person` být vlastnostkdispozicizlibovolnéhokódu,alelzejipřiřaditpouzezjiného`FirstName` kódu ve třídě.

Libovolný modifikátor omezujícího přístupu můžete přidat buď do sady, nebo přístupových objektů Get. Jakýkoli modifikátor přístupu, který umístíte na jednotlivé přistupující objekty, musí být omezenější než modifikátor přístupu v definici vlastnosti. Výše uvedená je právní, protože `FirstName` vlastnost je `public`, ale přistupující objekt set je `private`. `private` Nepodařilo`public` se deklarovat vlastnost s přistupujícím objektem. Deklarace vlastností lze `protected`také deklarovat `protected internal`, `internal`, nebo dokonce `private`.

Je také nutné umístit více omezující modifikátor na `get` přistupující objekt. Můžete mít `public` například vlastnost, ale `get` omezit přístup k `private`. Tento scénář se zřídka provádí v praxi.

Můžete také omezit změny vlastnosti tak, aby ji bylo možné nastavit pouze v konstruktoru nebo inicializátoru vlastnosti. `Person` Třídu můžete upravit takto:

[!code-csharp[A readonly auto implemented property](../../samples/snippets/csharp/properties/Person.cs#9)]

Tato funkce se nejčastěji používá pro inicializaci kolekcí, které jsou vystavené jako vlastnosti jen pro čtení:

```csharp
public class Measurements
{
    public ICollection<DataPoint> points { get; } = new List<DataPoint>();
}
```

### <a name="computed-properties"></a>Vypočítané vlastnosti

Vlastnost nemusí jednoduše vracet hodnotu pole člena. Můžete vytvořit vlastnosti, které vracejí vypočítanou hodnotu. Nyní rozbalíme `Person` objekt, který vrátí úplný název vypočítaný zřetězením prvního a posledního jména:

[!code-csharp[A computed property](../../samples/snippets/csharp/properties/Person.cs#10)]

Výše uvedený příklad používá funkci [interpolace řetězce](./language-reference/tokens/interpolated.md) k vytvoření formátovaného řetězce pro úplný název.

Můžete také použít *člen Expression-těle*, který poskytuje výstižnější způsob vytvoření vypočítané `FullName` vlastnosti:

[!code-csharp[A computed property using an expression bodied member](../../samples/snippets/csharp/properties/Person.cs#11)]

*Členové výrazu-těle* používají syntaxi *výrazu lambda* k definování metod, které obsahují jeden výraz. Zde tento výraz vrátí úplný název objektu Person.

### <a name="cached-evaluated-properties"></a>Vlastnosti vyhodnocené v mezipaměti

Můžete kombinovat koncept vypočítané vlastnosti s úložištěm a vytvořit *vlastnost vyhodnocenou v mezipaměti*.  Například můžete aktualizovat `FullName` vlastnost tak, aby formátování řetězce bylo provedeno pouze při prvním použití:

[!code-csharp[Caching the value of a computed property](../../samples/snippets/csharp/properties/Person.cs#12)]

Výše uvedený kód obsahuje chybu, i když. Pokud kód aktualizuje hodnotu `FirstName` vlastnosti nebo `LastName` , dříve vyhodnocené `fullName` pole je neplatné. Upravte `set` přístupové objekty `FirstName` `LastName` vlastnosti`fullName` a tak, aby bylo pole vypočítáno znovu:

[!code-csharp[Invalidating the cache correctly](../../samples/snippets/csharp/properties/Person.cs#13)]

Tato finální verze vyhodnocuje vlastnost `FullName` pouze v případě potřeby.
Pokud je dříve vypočtená verze platná, použije se. Pokud jiná změna stavu zruší platnost dříve vypočítané verze, přepočítá se. Vývojáři, kteří používají tuto třídu, nepotřebují znát podrobnosti implementace. Žádná z těchto vnitřních změn nemá vliv na použití objektu Person. To je klíčovým důvodem pro použití vlastností k vystavení datových členů objektu.

### <a name="attaching-attributes-to-auto-implemented-properties"></a>Připojení atributů k automaticky implementovaným vlastnostem

Počínaje C# 7,3, atributy polí lze připojit k poli pro zálohování generované kompilátorem v automaticky implementovaných vlastnostech. Zvažte například revizi `Person` třídy, která přidá jedinečnou vlastnost Integer `Id` .
`Id` Vlastnost napíšete pomocí automaticky implementované vlastnosti, ale návrh nevolá pro zachování `Id` vlastnosti. <xref:System.NonSerializedAttribute> Lze připojit pouze k polím, nikoli k vlastnostem. Můžete připojit <xref:System.NonSerializedAttribute> k poli `Id` pro zálohování pro vlastnost pomocí `field:` specifikátoru u atributu, jak je znázorněno v následujícím příkladu:

[!code-csharp[Attaching attributes to a backing field](../../samples/snippets/csharp/properties/Person.cs#14)]

Tento postup funguje pro všechny atributy, které se připojují k poli pro zálohování u automaticky implementované vlastnosti.

### <a name="implementing-inotifypropertychanged"></a>Implementace INotifyPropertyChanged

Konečný scénář, kdy je nutné napsat kód v přistupujícím objektu vlastnosti, je podporovat <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní používané pro oznamování klientům datových vazeb, že došlo ke změně hodnoty. Když se změní hodnota vlastnosti, objekt vyvolá <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged?displayProperty=nameWithType> událost, aby označovala změnu. Knihovny datových vazeb zase aktualizují prvky zobrazení na základě této změny. Následující kód ukazuje, jak byste implementovali `INotifyPropertyChanged` `FirstName` pro vlastnost této třídy Person.

[!code-csharp[invalidating the cache correctly](../../samples/snippets/csharp/properties/Person.cs#15)]

Operátor se nazývá *podmíněný operátor s hodnotou null.* `?.` Před vyhodnocením pravé strany operátoru kontroluje odkaz na hodnotu null. Konečným výsledkem je, že pokud neexistují předplatitelé `PropertyChanged` události, kód pro vyvolání události nebude spuštěn. V takovém případě `NullReferenceException` by vyvolala bez této kontroly. Další informace najdete na webu [`events`](events-overview.md). Tento příklad také používá operátor New `nameof` k převodu z symbolu názvu vlastnosti na jeho textovou reprezentaci.
Použití `nameof` může snížit počet chyb, u kterých jste nezadali název vlastnosti.

Opětovná implementace <xref:System.ComponentModel.INotifyPropertyChanged> je příkladem případu, kde můžete ve svých přístupových objektech napsat kód pro podporu scénářů, které potřebujete.

## <a name="summing-up"></a>Sčítání

Vlastnosti jsou formulářem inteligentních polí ve třídě nebo objektu. Mimo objekt se zobrazí jako pole v objektu. Vlastnosti však lze implementovat pomocí celé palety C# funkcí.
Můžete poskytnout ověřování, jiné přístupnost, opožděné vyhodnocení nebo požadavky, které vaše scénáře potřebují.
