---
title: Vlastnosti
description: Další informace o vlastnostech jazyka C#, které zahrnují funkce pro ověřování, vypočítané hodnoty, opožděné vyhodnocení a oznámení o změně vlastnosti.
ms.technology: csharp-fundamentals
ms.date: 04/25/2018
ms.openlocfilehash: bda8a4f58f71b57248296dd4ba9f9bf4cbed40d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399411"
---
# <a name="properties"></a>Vlastnosti

Vlastnosti jsou občané první třídy v C#. Jazyk definuje syntaxi, která umožňuje vývojářům psát kód, který přesně vyjadřuje jejich záměr návrhu.

Vlastnosti se chovají jako pole při přístupu.
Na rozdíl od polí jsou však vlastnosti implementovány s přistupujícími objekty, které definují příkazy provedené při přístupu k vlastnosti nebo jejich přiřazení.

## <a name="property-syntax"></a>Syntaxe vlastnosti

Syntaxe vlastností je přirozeným rozšířením polí. Pole definuje umístění úložiště:

[!code-csharp[Person class with public fields](../../samples/snippets/csharp/properties/Person.cs#1)]

Definice vlastnosti obsahuje deklarace pro `get` a `set` přistupující objekt, který načte a přiřadí hodnotu této vlastnosti:

[!code-csharp[Person class with public properties](../../samples/snippets/csharp/properties/Person.cs#2)]

Syntaxe uvedená výše je syntaxe *vlastnosti auto.* Kompilátor generuje umístění úložiště pro pole, které zálohuje vlastnost. Kompilátor také implementuje `get` tělo `set` přístupové body a.

V některých případě je třeba inicializovat vlastnost na hodnotu jinou než výchozí pro její typ.  C# umožňuje, že nastavením hodnoty za uzavírací složená závorka pro vlastnost. Můžete dát přednost počáteční `FirstName` hodnotu vlastnosti být `null`prázdný řetězec spíše než . Určit, jak je znázorněno níže:

[!code-csharp[Person class with properties and initializer](../../samples/snippets/csharp/properties/Person.cs#3)]

Konkrétní inicializace je nejužitečnější pro vlastnosti jen pro čtení, jak uvidíte dále v tomto článku.

Úložiště můžete také definovat sami, jak je znázorněno níže:

[!code-csharp[Person class with properties and backing field](../../samples/snippets/csharp/properties/Person.cs#4)]

Pokud je implementace vlastnosti jeden výraz, můžete použít *členy s výrazem pro* getter nebo setter:

[!code-csharp[Person class with properties and expression bodied getters and setters](../../samples/snippets/csharp/properties/Person.cs#5)]

Tato zjednodušená syntaxe bude použita tam, kde je to možné v tomto článku.

Definice vlastnosti je vlastnost pro čtení a zápis. Všimněte `value` si klíčového slova v přistupujícím přístupovém oru sady. Přistupující `set` objekt má `value`vždy jeden parametr s názvem . Přistupující `get` objekt musí vrátit hodnotu, která`string` je konvertibilní na typ vlastnosti ( v tomto příkladu).

To jsou základy syntaxe. Existuje mnoho různých variant, které podporují různé designové idiomy. Pojďme prozkoumat, a naučit se možnosti syntaxe pro každého.

## <a name="scenarios"></a>Scénáře

Výše uvedené příklady ukázaly jeden z nejjednodušších případů definice vlastnosti: vlastnost pro čtení a zápis bez ověření. Psaníkódu, který chcete `get` v `set` přístupových prostředcích a, můžete vytvořit mnoho různých scénářů.

### <a name="validation"></a>Ověřování

Můžete napsat kód `set` v přistupujícím objektu k zajištění, že hodnoty reprezentované vlastností jsou vždy platné. Předpokládejme například, že `Person` jedno pravidlo pro třídu je, že název nemůže být prázdný nebo prázdné. Dalo byste napsat, že takto:

[!code-csharp[Validating property setters](../../samples/snippets/csharp/properties/Person.cs#6)]

Předchozí příklad lze zjednodušit pomocí`throw` výrazu jako součást ověření nastavení vlastností:

[!code-csharp[Validating property setters](../../samples/snippets/csharp/properties/Person.cs#7)]

Výše uvedený příklad vynucuje pravidlo, že křestní jméno nesmí být prázdné nebo prázdné. Pokud vývojář zapíše

```csharp
hero.FirstName = "";
```

Toto přiřazení `ArgumentException`vyvolá . Vzhledem k tomu, že přistupující objekt sady vlastností musí mít prázdný návratový typ, ohlásíte chyby v přistupujícím objektu set vyvoláním výjimky.

Můžete rozšířit stejnou syntaxi na vše potřebné ve vašem scénáři. Můžete zkontrolovat vztahy mezi různými vlastnostmi nebo ověřit proti jakékoli externí podmínky. Všechny platné příkazy Jazyka C# jsou platné v přistupujícím objektu vlastnosti.

### <a name="read-only"></a>Jen pro čtení

Až do tohoto okamžiku jsou všechny definice vlastností, které jste viděli, vlastnosti pro čtení a zápis s veřejnými přistupujícími objekty. To není jediná platná přístupnost pro vlastnosti.
Můžete vytvořit vlastnosti jen pro čtení nebo dát různé usnadnění přístupu k sadě a získat přístupové objekty. Předpokládejme, `Person` že vaše třída by `FirstName` měla povolit pouze změnu hodnoty vlastnosti z jiných metod v této třídě. Můžete poskytnout přístupkový `private` nástroj `public`pro přístup k nastavení namísto:

[!code-csharp[Using a private setter for a publicly readonly property](../../samples/snippets/csharp/properties/Person.cs#8)]

Nyní `FirstName` vlastnost lze přistupovat z libovolného kódu, ale lze ji `Person` přiřadit pouze z jiného kódu ve třídě.

Můžete přidat libovolný omezující modifikátor přístupu buď nastavit nebo získat přístupové(."Můžete přidat všechny omezující přístup modifikátor y set nebo získat přístupové(."Můžete přidat všechny omezující přístup modifikátor y set nebo získat přístupové(."Access Všechny modifikátory přístupu, které umístíte na jednotlivé přistupující objekt, musí být omezenější než modifikátor přístupu v definici vlastnosti. Výše uvedené je `FirstName` legální, `public`protože vlastnost je `private`, ale nastavit přistupující objekt je . Nelze deklarovat `private` vlastnost `public` s přistupujícím objektem. Prohlášení o vlastnostech `protected`lze `internal` `protected internal`také deklarovat , , nebo dokonce `private`.

Je také legální umístit více omezující modifikátor na přistupujícího oru. `get` Můžete mít například `public` vlastnost, ale `get` omezit přistupující objekt na `private`. Tento scénář se v praxi provádí jen zřídka.

Můžete také omezit změny vlastnosti tak, aby ji lze nastavit pouze v konstruktoru nebo inicializátorvlastnosti. Třídu `Person` můžete upravit takto:

[!code-csharp[A readonly auto implemented property](../../samples/snippets/csharp/properties/Person.cs#9)]

Tato funkce se nejčastěji používá pro inicializaci kolekcí, které jsou vystaveny jako vlastnosti jen pro čtení:

```csharp
public class Measurements
{
    public ICollection<DataPoint> points { get; } = new List<DataPoint>();
}
```

### <a name="computed-properties"></a>Vypočítané vlastnosti

Vlastnost nemusí jednoduše vrátit hodnotu členského pole. Můžete vytvořit vlastnosti, které vrátí vypočítanou hodnotu. Rozbalíme objekt `Person` a vrátíme celé jméno vypočítané zřetězením křestního jména a příjmení:

[!code-csharp[A computed property](../../samples/snippets/csharp/properties/Person.cs#10)]

Výše uvedený příklad používá funkci [interpolace řetězce](./language-reference/tokens/interpolated.md) k vytvoření formátovaného řetězce pro celý název.

Můžete také použít *člen s výrazem ,* který poskytuje stručnější způsob vytvoření `FullName` vypočítané vlastnosti:

[!code-csharp[A computed property using an expression bodied member](../../samples/snippets/csharp/properties/Person.cs#11)]

*Členové s výrazem* používají syntaxi *výrazu lambda* k definování metod, které obsahují jeden výraz. Zde tento výraz vrátí celé jméno objektu osoby.

### <a name="cached-evaluated-properties"></a>Vlastnosti vyhodnocované v mezipaměti

Můžete kombinovat koncept vypočítané vlastnosti s úložištěm a vytvořit *vlastnost vyhodnocovanou v mezipaměti*.  Můžete například aktualizovat `FullName` vlastnost tak, aby formátování řetězce proběhlo pouze při prvním přístupu:

[!code-csharp[Caching the value of a computed property](../../samples/snippets/csharp/properties/Person.cs#12)]

Výše uvedený kód obsahuje chybu ačkoli. Pokud kód aktualizuje hodnotu `FirstName` `LastName` vlastnosti nebo, `fullName` je dříve vyhodnocené pole neplatné. Můžete upravit `set` přístupové objekty vlastnosti `FirstName` a `LastName` tak, aby `fullName` se pole znovu vypočítala:

[!code-csharp[Invalidating the cache correctly](../../samples/snippets/csharp/properties/Person.cs#13)]

Tato konečná verze `FullName` vyhodnotí vlastnost pouze v případě potřeby.
Pokud je dříve vypočtená verze platná, použije se. Pokud jiná změna stavu zruší platnost dříve vypočtené verze, bude přepočítána. Vývojáři, kteří používají tuto třídu, nepotřebují znát podrobnosti implementace. Žádná z těchto vnitřních změn nemá vliv na použití objektu Person. To je hlavní důvod pro použití Vlastnosti vystavit datové členy objektu.

### <a name="attaching-attributes-to-auto-implemented-properties"></a>Připojení atributů k automaticky implementovaným vlastnostem

Počínaje C# 7.3, atributy pole lze připojit k kompilátoru generované záložní pole v automaticky implementované vlastnosti. Zvažte například revizi `Person` třídy, která přidá `Id` jedinečnou celou vlastnost.
Vlastnost napíšete`Id` pomocí automaticky implementované vlastnosti, ale váš `Id` návrh nevolá pro zachování vlastnosti. Lze <xref:System.NonSerializedAttribute> připojit pouze k polím, nikoli k vlastnostem. K záložnímu <xref:System.NonSerializedAttribute> poli vlastnosti `Id` můžete připojit `field:` pomocí specifikátoru atributu, jak je znázorněno v následujícím příkladu:

[!code-csharp[Attaching attributes to a backing field](../../samples/snippets/csharp/properties/Person.cs#14)]

Tato technika funguje pro všechny atributy, které připojíte k záložnímu poli v automaticky implementované vlastnosti.

### <a name="implementing-inotifypropertychanged"></a>Implementace vlastnosti INotifyPropertyZměněn

Konečný scénář, kde je třeba napsat kód v přistupujícím objektu vlastnosti je podporovat <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní používané k upozornění klientů datové vazby, že hodnota se změnila. Když se změní hodnota vlastnosti, <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged?displayProperty=nameWithType> objekt vyvolá událost k označení změny. Knihovny datových vazeb zase aktualizují prvky zobrazení na základě této změny. Níže uvedený kód ukazuje, `INotifyPropertyChanged` jak `FirstName` byste implementovat pro vlastnost této třídy osoby.

[!code-csharp[invalidating the cache correctly](../../samples/snippets/csharp/properties/Person.cs#15)]

Operátor `?.` se nazývá *operátor null conditional*. Zkontroluje odkaz null před vyhodnocením pravé straně operátoru. Konečným výsledkem je, že pokud neexistují `PropertyChanged` žádné předplatitelé události, kód pro zvýšení události se nespustí. V tom `NullReferenceException` kufříku by to bez kontroly. Další informace naleznete [`events`](events-overview.md)v tématu . Tento příklad také `nameof` používá nový operátor k převodu ze symbolu názvu vlastnosti na jeho textovou reprezentaci.
Použití `nameof` může snížit chyby, kde jste nesprávně zadali název vlastnosti.

Opět platí, <xref:System.ComponentModel.INotifyPropertyChanged> že implementace je příkladem případu, kde můžete napsat kód v přístupových objektech pro podporu scénáře, které potřebujete.

## <a name="summing-up"></a>Sečtením

Vlastnosti jsou formou inteligentních polí ve třídě nebo objektu. Mimo objekt vypadají jako pole v objektu. Vlastnosti však mohou být implementovány pomocí úplné palety c# funkce.
Můžete poskytnout ověření, různé usnadnění přístupu, opožděné vyhodnocení nebo všechny požadavky, které vaše scénáře potřebují.
