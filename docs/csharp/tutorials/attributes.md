---
title: Atributy - C#
description: Zjistěte, jak fungují atributy v jazyce C#.
author: mgroves
ms.date: 03/06/2017
ms.assetid: b152cf36-76e4-43a5-b805-1a1952e53b79
ms.openlocfilehash: db6db50ac59e804225bdc11c435fef3d53fa685e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352692"
---
# <a name="using-attributes-in-c"></a>Pomocí atributů v jazyce C# #

Atributy poskytují způsob přiřazení informace s kódem deklarativní způsobem. Můžete zadat taky opakovaně použitelné element, který lze použít na celou řadu cíle.

Vezměte v úvahu `[Obsolete]` atribut. Je možné použít pro třídy, struktury, metody, konstruktory a další. Ho _deklaruje_ , že prvek je zastaralé. Pak je kompilátor jazyka C# vyhledejte tento atribut a provádět některé akce v odpovědi.

V tomto kurzu se seznámíte k přidání atributů do vašeho kódu, jak vytvořit a používat vlastní atributy a použití některých atributů, které jsou součástí .NET Core.

## <a name="prerequisites"></a>Požadavky
Budete potřebovat k nastavení vašeho počítače ke spuštění .NET core. Pokyny k instalaci najdete na [.NET Core](https://www.microsoft.com/net/core) stránky.
Tuto aplikaci můžete spustit v systému Windows, Ubuntu Linux, systému macOS nebo v kontejner Docker. Budete muset nainstalovat editor vaše oblíbené kódu. Popisy níže použijte [Visual Studio Code](https://code.visualstudio.com/) který je typu open source pro různé platformy editor. Můžete však použít, ať nástroje umíte pracovat s.

## <a name="create-the-application"></a>Vytvoření aplikace

Teď, když jste nainstalovali všechny nástroje, vytvořte novou aplikaci .NET Core. Pokud chcete používat generátor příkazového řádku, spusťte následující příkaz v své oblíbené prostředí:

`dotnet new console`

Tento příkaz vytvoří jen nejzákladnější soubory projektu .NET core. Budete muset provést `dotnet restore` Obnovit závislosti potřebné ke kompilaci tento projekt.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Spuštění programu, použijte `dotnet run`. Měli byste vidět "Hello, World" výstup do konzoly.

## <a name="how-to-add-attributes-to-code"></a>Postup přidání atributů do kódu

V jazyce C#, atributy jsou třídy, které dědí od `Attribute` základní třídy. Všechny třídy, která dědí z `Attribute` lze použít jako řazení "značky" v další části kódu.
Například je atribut nazvaný `ObsoleteAttribute`. Používá se signál, že kód je zastaralé a už by se neměla používat. Tento atribut na třídu, můžete umístit například pomocí hranaté závorky.

[!code-csharp[Obsolete attribute example](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ObsoleteExample1)]  

Všimněte si, že když je volána třída `ObsoleteAttribute`, pouze je nutné použít `[Obsolete]` v kódu. Jedná se o konvenci, která následuje C#.
Můžete použít úplný název `[ObsoleteAttribute]` Pokud si zvolíte.

Při označování třídu zastaralé, je vhodné zajistit nějaké informace, které jako *proč* je zastaralý, nebo *co* místo toho chcete použít. To provedete v předávání do atribut zastaralý parametr řetězce.

[!code-csharp[Obsolete attribute example with parameters](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ObsoleteExample2)]

Řetězec je předávána jako argument pro `ObsoleteAttribute` konstruktoru, stejně, jako by byly zápis `var attr = new ObsoleteAttribute("some string")`.

Parametry, které atributu konstruktoru jsou omezeny na jednoduché typy nebo literály: `bool, int, double, string, Type, enums, etc` a pole těchto typů.
Nelze použít výraz nebo proměnnou. Budete používat poziční nebo pojmenované parametry.

## <a name="how-to-create-your-own-attribute"></a>Jak vytvořit vlastní atribut

Vytváření atribut je jednoduché, která dědí z `Attribute` základní třídy.

[!code-csharp[Create your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CreateAttributeExample1)]

Pomocí výše uvedeného I teď můžete použít `[MySpecial]` (nebo `[MySpecialAttribute]`) jako atribut jinde v základu kódu.

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CreateAttributeExample2)]

Atributy v knihovně základní třídy rozhraní .NET, například `ObsoleteAttribute` aktivovat určitého chování v kompilátoru. Ale všechny atributy, které vytvoříte slouží pouze jako metadata a nevede k žádný kód v rámci třídy atributů spouštěna. Je to na vám tak, aby fungoval na aby metadata někde v kódu (podrobnosti o této později v tomto kurzu).

Není gotcha zde sledujte. Jak je uvedeno nahoře, jsou povoleny pouze určité typy mají být předány jako argumenty, při použití atributů. Ale při vytváření typ atributu, kompilátor jazyka C# neukončí můžete z vytváření těchto parametrů. V následujícím příkladu, vytvořili jste atribut s konstruktor, který se zkompiluje stejně dobře.

[!code-csharp[Valid constructor used in an attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeGothca1)]

Však nebude možné použít tento konstruktor se syntaxí atributu.

[!code-csharp[Invalid attempt to use the attribute constructor](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeGotcha2)]

Výše způsobí chybu kompilátoru jako `Attribute constructor parameter 'myClass' has type 'Foo', which is not a valid attribute parameter type`

## <a name="how-to-restrict-attribute-usage"></a>Jak omezit použití atributu

Atributy lze použít na několika "cíle". Příklady uvedené nahoře je pro třídy, ale můžete je také použít na:

* Assembly
* Třída
* Konstruktor
* Delegát
* Výčet
* Událost
* Pole
* GenericParameter
* Rozhraní
* Metoda
* Modul
* Parametr
* Vlastnost
* ReturnValue
* Struktura

Když vytvoříte třídy atributu, ve výchozím nastavení, C# vám umožní použít tento atribut na žádném z cíle možné atributů. Pokud chcete omezit na určité cíle vaší atribut, můžete tak učinit pomocí `AttributeUsageAttribute` na vaší třídě atribut. Který má pravým, atribut na atribut!

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeUsageExample1)]

Pokud se pokusíte umístí výše uvedený atribut něco, co není třídu nebo struktury, zobrazí se chyba kompilátoru jako `Attribute 'MyAttributeForClassAndStructOnly' is not valid on this declaration type. It is only valid on 'class, struct' declarations`

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeUsageExample2)]

## <a name="how-to-use-attributes-attached-to-a-code-element"></a>Jak používat atributy připojené k element kódu

Atributy fungují jako metadata. Bez některé pasivního platnost se nebude nijak ve skutečnosti.

K vyhledání a fungovat na atributy, [reflexe](../programming-guide/concepts/reflection.md) je obvykle potřeba. I nebude pokrývat reflexe podrobný v tomto kurzu, ale Základní myšlenkou je, že reflexe umožňuje psaní kódu v C#, která hledá jiný kód.

Například můžete reflexe a získat informace o třídě: 

[!code-csharp[Getting type information with Reflection](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ReflectionExample1)]

Ta vypíše se něco podobného jako: `The assembly qualified name of MyClass is ConsoleApplication.MyClass, attributes, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null`

Jakmile máte `TypeInfo` objektu (nebo `MemberInfo`, `FieldInfo`atd), můžete použít `GetCustomAttributes` metoda. Tato možnost vrátí kolekci `Attribute` objekty.
Můžete také použít `GetCustomAttribute` a zadejte typ atributu.

Tady je příklad použití `GetCustomAttributes` na `MemberInfo` instanci pro `MyClass` (které jsme viděli dříve došlo `[Obsolete]` atribut na něm).

[!code-csharp[Getting type information with Reflection](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ReflectionExample2)]

Ta vypíše do konzoly: `Attribute on MyClass: ObsoleteAttribute`. Zkuste přidat další atributy, které mají `MyClass`.

Je důležité si uvědomit, že tyto `Attribute` líné instance objektů. To znamená, že nebude spuštěna dokud `GetCustomAttribute` nebo `GetCustomAttributes`.
Pokaždé, když jsou také vytvořeny instance. Volání metody `GetCustomAttributes` dvakrát v řádku vrátí dva různé instance `ObsoleteAttribute`.

## <a name="common-attributes-in-the-base-class-library-bcl"></a>Běžné atributy v knihovně základní třídu (BCL)

Atributy se používají tak, že mnoho nástroje a rozhraní. NUnit používá atributů, například `[Test]` a `[TestFixture]` jsou používány nástroj test runner NUnit. ASP.NET MVC používá atributů, například `[Authorize]` a poskytuje rámec filtru akce k provedení mezi vyjímání obavy na akce MVC. [PostSharp](https://www.postsharp.net) používá syntaxi atribut umožňující aspekt orientované programování v C#.

Zde je několik významné atributy integrovaný do knihovny .NET Core základní třídy:

* `[Obsolete]`. Tato byl použit v uvedených příkladech a je umístěn v `System` oboru názvů. Je vhodné zajistit deklarativní dokumentaci o základní změny kódu. Zprávu lze zadat v podobě řetězce a jiné logického parametru lze použít pro zvýšení z kompilátoru upozornění k chybě kompilátoru.

* `[Conditional]`. Tento atribut je v `System.Diagnostics` oboru názvů. Tento atribut lze použít metody (nebo třídy atributů). Řetězec je nutné předat do konstruktoru.
Pokud se, řetězce odpovídá `#define` direktivy, pak všechny volání této metody (ale ne metoda sama) se odeberou kompilátorem C#. Obvykle to se používá pro ladění (Diagnostika).

* `[CallerMemberName]`. Tento atribut lze použít na parametry a život v `System.Runtime.CompilerServices` oboru názvů. Toto je atribut, který slouží k vložení název metody, která volá jinou metodu. Obvykle se používá jako způsob, jak eliminovat "kouzelná řetězce" při implementaci v různých architektury uživatelského rozhraní INotifyPropertyChanged. Jako příklad:

[!code-csharp[Using CallerMemberName when implementing INotifyPropertyChanged](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CallerMemberName1)]

Ve výše uvedeném kódu, nemusíte mít literál `"Name"` řetězec. To pomáhá zabránit překlepem související chyby a také zajišťuje pro hladší refaktoring nebo přejmenování.

## <a name="summary"></a>Souhrn

Atributy přepněte deklarativní power jazyka C#. Ale nejsou formu kód jako metadata a není fungovat samostatně.
