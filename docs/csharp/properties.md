---
title: Vlastnosti
description: Další informace o C# vlastnosti, které obsahují funkce pro ověření, počítaný hodnoty, opožděné vyhodnocení, a vlastnost změnit oznámení.
keywords: Rozhraní .NET, .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 04/03/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 6950d25a-bba1-4744-b7c7-a3cc90438c55
ms.openlocfilehash: 05e51d527dc3c05301fc85d7717c751dc46bf9fa
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2018
---
# <a name="properties"></a>Vlastnosti

Vlastnosti jsou prvotřídní občanů v jazyce C#. Jazyk definuje syntaxi, která umožňuje vývojářům psát kód, který přesně vyjadřoval jejich záměr návrhu.

Vlastnosti chovat jako pole, když k nim.
Na rozdíl od pole, ale vlastnosti jsou u přistupující objekty, které definují příkazy spustit, když je vlastnost získat přístup nebo přiřazená implementován.

## <a name="property-syntax"></a>Syntaxe vlastností

Syntaxe vlastností v představuje přirozené rozšíření na pole. Pole definuje umístění úložiště:

```csharp
public class Person
{
    public string FirstName;
    // remaining implementation removed from listing
}
```

Obsahuje deklarace pro definici vlastnosti `get` a `set` přistupujícího objektu, který načítá a přiřadí hodnota této vlastnosti:

```csharp
public class Person
{
    public string FirstName { get; set; }

    // remaining implementation removed from listing
}
```

Syntaxe uvedené výše je *automaticky vlastnost* syntaxe. Kompilátor generuje umístění úložiště pro pole, který zálohuje vlastnost. Kompilátor také implementuje text `get` a `set` přistupující objekty.

V některých případech je nutné inicializovat vlastnost na jinou hodnotu než výchozí u tohoto typu.  C# umožňuje který nastavením hodnoty po pravé složené závorce pro vlastnost. Dáte možná přednost počáteční hodnota `FirstName` vlastnost, která má být prázdný řetězec místo `null`. Zadáte, jak je uvedeno níže:

```csharp
public class Person
{
    public string FirstName { get; set; } = string.Empty;

    // remaining implementation removed from listing
}
```

To je velmi užitečné pro vlastnosti jen pro čtení, jak uvidíte později v tomto tématu.

Můžete také definovat úložiště sami, jak je uvedeno níže:

```csharp
public class Person
{
    public string FirstName
    {
        get { return firstName; }
        set { firstName = value; }
    }
    private string firstName;
    // remaining implementation removed from listing
}
```

Pokud implementace vlastností jeden výraz, můžete použít *výraz vozidlo členy* pro mechanismu získání nebo nastavení:

```csharp
public class Person
{
    public string FirstName
    {
        get => firstName;
        set => firstName = value;
    }
    private string firstName;
    // remaining implementation removed from listing
}
```

Tato zjednodušenou syntaxi se použije v případě potřeby v tomto tématu.

Definici vlastnosti uvedené výše je vlastnost pro čtení a zápis. Všimněte si klíčové slovo `value` v přistupující objekt set. `set` Přistupujícího objektu má vždy jeden parametr s názvem `value`. `get` Přistupujícího objektu musí vracet hodnotu, která je převést na typ vlastnosti (`string` v tomto příkladu).
 
To je základní informace o syntaxi. Existuje mnoho různých variant, které podporují celou řadu různých idioms. Umožňuje prozkoumat ty a další možnosti syntaxe pro každou.

## <a name="scenarios"></a>Scénáře

Výše uvedených příkladech vám ukázal, jedním z nejjednodušších definice vlastnost: vlastnost pro čtení a zápis bez ověřování. Zápis kódu chcete `get` a `set` přístupové objekty, můžete vytvořit mnoho různých scénářů.

### <a name="validation"></a>Ověřování

Můžete napsat kód ve `set` přistupujícího objektu hodnoty reprezentována vlastnost musí být vždy platné. Předpokládejme například, pro jedno pravidlo `Person` třída je, že název nemůže být prázdný nebo mezer. By zápisu, následujícím způsobem:

```csharp
public class Person
{
    public string FirstName
    {
        get => firstName;
        set
        {
            if (string.IsNullOrWhiteSpace(value))
                throw new ArgumentException("First name must not be blank");
            firstName = value;
        }
    }
    private string firstName;
    // remaining implementation removed from listing
}
```

V předchozím příkladu vynucuje pravidlo, že křestní jméno nesmí být prázdný nebo mezer. Pokud vývojář zapíše

```csharp
hero.FirstName = "";
```

Vyvolá tuto přiřazení `ArgumentException`. Protože vlastnosti musí mít typ vrácené hodnoty void, sestavu chyb v přistupující objekt set podle došlo k výjimce.

Který je jednoduchý případ ověření. Tato stejná syntaxe k ničemu potřeba ve vašem scénáři můžete rozšířit. Můžete zkontrolovat vztahy mezi různé vlastnosti nebo vyhodnotit proti případné externí podmínky. Všechny platné příkazy jazyka C# jsou platné v přistupujícího objektu vlastnosti.

### <a name="read-only"></a>jen pro čtení

V tomto okamžiku jsou všechny definice vlastností, které jste viděli vlastností čtení/zápisu s veřejné přistupující objekty. Toto není platné pouze pro usnadnění přístupu pro vlastnosti.
Můžete vytvořit vlastnosti jen pro čtení, nebo poskytnout jiné usnadnění přístupu k sadě a získat přístupové objekty. Předpokládat, že vaše `Person` třída měli jenom povolit změna hodnoty `FirstName` vlastnost z jiné metody v dané třídě. Může poskytnout přistupující objekt set `private` usnadnění místo `public`:

```csharp
public class Person
{
    public string FirstName { get; private set; }

    // remaining implementation removed from listing
}
```

Nyní `FirstName` vlastnost je přístupná z žádný kód, ale lze přiřadit pouze z jiných kódu v `Person` třídy.

Můžete přidat všechny – modifikátor přístupu omezující buď sadu nebo získat přístupové objekty. Žádné – modifikátor přístupu u jednotlivých přistupujícího objektu musí být omezenější než – modifikátor přístupu na definici vlastnosti. Výše je právní protože `FirstName` vlastnost je `public`, ale je přistupující objekt set `private`. Nelze deklarovat `private` vlastnost s `public` přistupujícího objektu. Vlastnost deklarace lze také deklarovat `protected`, `internal`, `protected internal`, `private protected` nebo i `private`.   

Taky je platné umístit na víc omezující modifikátor `get` přistupujícího objektu. Například můžete mít `public` vlastnost, ale omezit `get` přistupujícího objektu `private`. Tento scénář se zřídka provádí v praxi.

Úpravy vlastností můžete taky omezit tak, aby lze nastavit pouze v konstruktoru nebo inicializátoru vlastnost. Můžete upravit `Person` třídy tak následujícím způsobem:

```csharp
public class Person
{
    public Person(string firstName)
    {
        this.FirstName = firstName;
    }

    public string FirstName { get; }

    // remaining implementation removed from listing
}
```

Tato funkce se nejčastěji používá pro inicializaci kolekce, které jsou zveřejněné jako jen pro čtení vlastnosti:

```csharp
public class Measurements
{
    public ICollection<DataPoint> points { get; } = new List<DataPoint>();
}
```

### <a name="computed-properties"></a>Počítané vlastnosti

Vlastnost není nutné jednoduše vrátí hodnotu pole členů. Můžete vytvořit vlastnosti, které vracejí vypočtená hodnota. Umožňuje rozšířit `Person` objekt, který chcete vrátit úplný název, počítaný zřetězením názvy první a poslední:

```csharp
public class Person
{
    public string FirstName { get; set; }

    public string LastName { get; set; }

    public string FullName { get { return $"{FirstName} {LastName}"; } }
}
```

V příkladu výše používá [řetězec interpolace](../csharp/language-reference/tokens/interpolated.md) funkce vytvořit formátovaný řetězec pro úplný název.

Můžete také použít *výraz vozidlo členy*, který poskytuje více stručného způsob, jak vytvořit použití počítaných `FullName` vlastnost:

```csharp
public class Person
{
    public string FirstName { get; set; }

    public string LastName { get; set; }

    public string FullName =>  $"{FirstName} {LastName}";
}
```
 
*Výraz vozidlo členy* použít *výrazu lambda* syntaxe zadat metodu, která obsahují jeden výraz. Tento výraz zde, vrátí úplný název pro objekt osoby.

### <a name="lazy-evaluated-properties"></a>Opožděné vyhodnotí vlastnosti

Můžete kombinovat koncept vypočítané vlastnosti s úložištěm a vytvořit *opožděné vyhodnocení vlastnost*.  Například můžete aktualizovat `FullName` vlastnost tak, aby formátování řetězce pouze došlo při prvním byl přístup:

```csharp
public class Person
{
    public string FirstName { get; set; }

    public string LastName { get; set; }

    private string fullName;
    public string FullName
    {
        get
        {
            if (fullName == null)
                fullName = $"{FirstName} {LastName}";
            return fullName;
        }
    }
}
```

Výše uvedený kód obsahuje chybu, když. Pokud kód aktualizace hodnotu buď `FirstName` nebo `LastName` vlastnost, dříve vyhodnotí `fullName` pole je neplatné. Je potřeba aktualizovat `set` přístupových objektů `FirstName` a `LastName` vlastnost tak, aby `fullName` pole se vypočítává znovu:

```csharp
public class Person
{
    private string firstName;
    public string FirstName
    {
        get => firstName;
        set
        {
            firstName = value;
            fullName = null;
        }
    }

    private string lastName;
    public string LastName
    {
        get => lastName;
        set
        {
            lastName = value;
            fullName = null;
        }
    }

    private string fullName;
    public string FullName
    {
        get
        {
            if (fullName == null)
                fullName = $"{FirstName} {LastName}";
            return fullName;
        }
    }
}
```

Vyhodnotí této poslední verzi `FullName` vlastnost pouze v případě potřeby.
Pokud je platný dříve počítané verze, se používá. Další změnou stavu by způsobila neplatnost dříve počítané verze, bude přepočítána. Vývojáři, které používají tuto třídu není potřeba znát podrobnosti implementace. Žádná z těchto interní změny mají vliv na použití objektu osoby. To je klíče důvod pomocí vlastnosti vystavit data členům v objektu.
 
### <a name="inotifypropertychanged"></a>Rozhraní INotifyPropertyChanged.

Poslední scénář, kde je potřeba psát kód v přistupujícího objektu vlastnosti je podpora `INotifyPropertyChanged` rozhraní sloužící k upozornění klientů vazby dat, která byla hodnota změněna. Při změně hodnoty vlastnosti, vyvolá objekt `PropertyChanged` události označit změny. Datové vazby knihovny, pak aktualizovat zobrazení prvky založené na tuto změnu. Následující kód ukazuje, jak můžete implementovat `INotifyPropertyChanged` pro `FirstName` vlastnost této třídy osoby.

```csharp
public class Person : INotifyPropertyChanged
{
    public string FirstName
    {
        get => firstName;
        set
        {
            if (string.IsNullOrWhiteSpace(value))
                throw new ArgumentException("First name must not be blank");
            if (value != firstName)
            {
                PropertyChanged?.Invoke(this, 
                    new PropertyChangedEventArgs(nameof(FirstName)));
            }
            firstName = value;
        }
    }
    private string firstName;

    public event PropertyChangedEventHandler PropertyChanged;
    // remaining implementation removed from listing
}
```

`?.` Operátor je volána *null podmíněný operátor*. Před vyhodnocením pravé straně operátoru zkontroluje pro odkaz s hodnotou null. Konečným výsledkem je, že pokud neexistují žádné odběratele, kteří mají `PropertyChanged` událostí, neprovede se kód pro vyvolání události. By throw `NullReferenceException` bez zkontrolujte v takovém případě. Naleznete na stránce na [ `events` ](delegates-events.md) další podrobnosti. Tento příklad také používá nové `nameof` operátor převést z názvu symbolu vlastnost textové reprezentace.
Pomocí `nameof` můžete snížit počet chyb, které jste zadali název vlastnosti.

Znovu jedná se o příklad případu, kde můžete napsat kód ve vaší přístupových objektů pro podporu scénáře, které potřebujete.

## <a name="summing-up"></a>Shrnutí

Vlastnosti jsou formuláře inteligentních polí ve třídě nebo objekt. Z mimo objekt, zobrazí se jako pole v objektu. Však vlastnosti se dají implementovat pomocí úplné palety funkcí jazyka C#.
Můžete zadat ověřování, jiný usnadnění, opožděné vyhodnocení nebo všechny požadavky potřebné pro vaše scénáře.
