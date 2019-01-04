---
title: Atributy – C#
description: Zjistěte, jak fungují atributy v jazyce C#.
author: mgroves
ms.date: 03/06/2017
ms.assetid: b152cf36-76e4-43a5-b805-1a1952e53b79
ms.openlocfilehash: 38d22e707dd8c9877183feb8446407c20a21b416
ms.sourcegitcommit: 3b9b7ae6771712337d40374d2fef6b25b0d53df6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/04/2019
ms.locfileid: "54029824"
---
# <a name="using-attributes-in-c"></a>Použití atributů v jazyce C# #

Atributy poskytují způsob, jak informace o přidružení kódu deklarativní způsobem. Můžete také poskytují opakovaně použitelné element, který lze použít pro širokou škálu cíli.

Vezměte v úvahu `[Obsolete]` atribut. Lze použít na třídy, struktury, metody, konstruktory a další. To _deklaruje_ element je zastaralý. Pak je kompilátor jazyka C# pro tento atribut, a provést některé akce v odpovědi.

V tomto kurzu se seznámíte k přidání atributů do kódu, jak vytvořit a použít vlastní atributy a jak používat některé atributy, které jsou integrované do .NET Core.

## <a name="prerequisites"></a>Požadavky
Budete potřebovat k nastavení vašeho počítače ke spuštění .NET core. Můžete najít pokyny k instalaci na [.NET Core](https://www.microsoft.com/net/core) stránky.
Tuto aplikaci můžete spustit na Windows, Ubuntu Linux, macOS nebo v kontejneru Dockeru. Bude potřeba nainstalovat váš oblíbený editor kódu. Popisy níže použití [Visual Studio Code](https://code.visualstudio.com/) což je open source pro různé platformy editoru. Ale můžete použít jakýkoli nástroje jste obeznámeni.

## <a name="create-the-application"></a>Vytvoření aplikace

Teď, když si nainstalujete všechny nástroje, vytvořte novou aplikaci .NET Core. Použití generátoru příkazového řádku, spusťte následující příkaz, v oblíbeném prostředí:

`dotnet new console`

Tento příkaz vytvoří nejzákladnější soubory projektu .NET core. Budete muset provést `dotnet restore` Obnovit závislosti potřebné ke kompilaci tohoto projektu.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Chcete-li spustit program, použijte `dotnet run`. Měli byste vidět "Hello, World" výstup na konzolu.

## <a name="how-to-add-attributes-to-code"></a>Postup přidání atributů do kódu

V jazyce C#, atributy se tříd, které dědí z `Attribute` základní třídy. Všechny třídy, která dědí z `Attribute` lze použít jako typ "značka" na jiných částí kódu.
Například je atribut s názvem `ObsoleteAttribute`. Slouží k signalizaci, že kód je zastaralá a neměl by se už nebudete používat. Můžete umístit tento atribut na třídu, například pomocí hranatých závorek.

[!code-csharp[Obsolete attribute example](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ObsoleteExample1)]  

Všimněte si, že zatímco třídy se nazývá `ObsoleteAttribute`, pouze je nutné použít `[Obsolete]` v kódu. Toto je konvence, C# následujícím.
Můžete použít celý název `[ObsoleteAttribute]` Pokud zvolíte.

Při označení zastaralé třídy, je vhodné poskytnout určité informace jako *proč* je zastaralé, a/nebo *co* místo toho použít. To proveďte předáním parametru řetězce na atribut zastaralé.

[!code-csharp[Obsolete attribute example with parameters](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ObsoleteExample2)]

Řetězec je předávána jako argument `ObsoleteAttribute` konstruktoru, stejně jako kdybyste psali `var attr = new ObsoleteAttribute("some string")`.

Parametry pro konstruktor atributem jsou omezené na jednoduché typy/literálů: `bool, int, double, string, Type, enums, etc` a pole těchto typů.
Nelze použít výraz nebo proměnné. Můžete libovolně udělovat použít poziční nebo pojmenované parametry.

## <a name="how-to-create-your-own-attribute"></a>Jak vytvořit vlastní atribut

Vytvoření atributu je stejně jednoduché jako dědění z `Attribute` základní třídy.

[!code-csharp[Create your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CreateAttributeExample1)]

Pomocí výše uvedeného lze nyní použít `[MySpecial]` (nebo `[MySpecialAttribute]`) jako atribut jinde v základu kódu.

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CreateAttributeExample2)]

Atributy v knihovně základních tříd .NET, například `ObsoleteAttribute` aktivovat určité chování v rámci kompilátor. Všechny atributy, které vytvoříte však funguje pouze jako metadata a nevede žádný kód v rámci třídy atributů, které se spouští. To je na vás tak, aby fungoval na těchto metadat jinde ve vašem kódu (více zabývat později v tomto kurzu).

Zde je "gotcha zde dávejte pozor na. Jak je uvedeno výše, jsou povoleny pouze určité typy mají být předány jako argumenty při použití atributů. Ale při vytváření typ atributu, kompilátor jazyka C# nezpůsobí ukončení můžete vytvářet tyto parametry. V následujícím příkladu, jsem vytvořil atribut s konstruktorem, který zkompiluje zcela v pořádku.

[!code-csharp[Valid constructor used in an attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeGothca1)]

Nicméně nebude možné použít tento konstruktor s syntaxe atributu.

[!code-csharp[Invalid attempt to use the attribute constructor](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeGotcha2)]

Výše uvedené způsobí chybu kompilátoru jako `Attribute constructor parameter 'myClass' has type 'Foo', which is not a valid attribute parameter type`

## <a name="how-to-restrict-attribute-usage"></a>Jak omezit použití atributu

Atributy lze použít na celé řadě "cíle". Ukazují výše uvedené příklady na třídy, ale je také možné používat podle:

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
* returnValue
* Struktura

Při vytváření třídy atributu, ve výchozím nastavení jazyka C# vám umožní použít tento atribut na žádném z cíle atributů je to možné. Pokud chcete omezit atribut na určité cíle, můžete to provést pomocí `AttributeUsageAttribute` na třídě atribut. Který má klikněte pravým tlačítkem myši, atribut u atributu!

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeUsageExample1)]

Pokud se pokusíte vložit výše uvedené atributu na libovolnou položku, která není třída nebo struktura, obdržíte chybu kompilátoru jako `Attribute 'MyAttributeForClassAndStructOnly' is not valid on this declaration type. It is only valid on 'class, struct' declarations`

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeUsageExample2)]

## <a name="how-to-use-attributes-attached-to-a-code-element"></a>Jak používat atributy připojené k prvek kódu

Atributy fungují jako metadata. Bez některé pasivního platnost se nespustí skutečně žádnou akci.

Chcete-li najít a zpracovat atributy, [reflexe](../programming-guide/concepts/reflection.md) je obvykle potřeba. Nebudeme se zabývat odraz podrobný v tomto kurzu, ale základní myšlenka je, že reflexe umožňuje psát kód v jazyce C#, který prověří jiného kódu.

Například můžete použít reflexe a získat informace o třídě (Přidat `using System.Reflection;` v čele váš kód): 

[!code-csharp[Getting type information with Reflection](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ReflectionExample1)]

Který vytiskne vypadat: `The assembly qualified name of MyClass is ConsoleApplication.MyClass, attributes, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null`

Jakmile budete mít `TypeInfo` objektu (nebo `MemberInfo`, `FieldInfo`atd), můžete použít `GetCustomAttributes` metoda. Vrátí kolekci `Attribute` objekty.
Můžete také použít `GetCustomAttribute` a zadejte typ atributu.

Tady je příklad použití `GetCustomAttributes` na `MemberInfo` instanci `MyClass` (které jsme viděli výše má `[Obsolete]` atribut na něj).

[!code-csharp[Getting type information with Reflection](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ReflectionExample2)]

Vytiskne, který se do konzoly: `Attribute on MyClass: ObsoleteAttribute`. Pokuste se přidat dalších atributů, které mají `MyClass`.

Je důležité si uvědomit, že tyto `Attribute` laxně instalace objektů. To znamená, že nebude spuštěna dokud nepoužijete `GetCustomAttribute` nebo `GetCustomAttributes`.
Jsou také vytvořena instance pokaždé, když. Volání `GetCustomAttributes` dvakrát za sebou vrátí dva různé instance `ObsoleteAttribute`.

## <a name="common-attributes-in-the-base-class-library-bcl"></a>Běžné atributy v knihovně základních tříd (BCL)

Atributy jsou používány mnoho nástrojů a platforem. NUnit používá atributů, jako je `[Test]` a `[TestFixture]` , které používá nástroj test runner NUnit. ASP.NET MVC pomocí atributů, jako je `[Authorize]` a poskytuje rozšiřovatelnou platformu pro filtr akce k provedení vyskytující aspekty na akce MVC. [PostSharp](https://www.postsharp.net) umožňující aspektově orientované programování v jazyce C# používá syntaxi atributů.

Tady je pár významné atributy, které jsou součástí knihovny základních tříd .NET Core:

* `[Obsolete]`. Tohle byl použit v předchozích příkladech a nachází `System` oboru názvů. To je užitečné poskytují deklarativní dokumentaci o změnu základu kódu. Zprávy lze zadat v podobě řetězce a další logický parametr je možné předat z upozornění kompilátoru chybu kompilátoru.

* `[Conditional]`. Tento atribut je `System.Diagnostics` oboru názvů. Tento atribut lze použít u metody (nebo třídy atributů). Je nutné předat řetězec do konstruktoru.
Pokud, který řetězce shody `#define` direktiv, pak všechna volání do metody (ale ne metodu) se odeberou kompilátorem jazyka C#. To je obvykle používá pro účely (Diagnostika) ladění.

* `[CallerMemberName]`. Tento atribut lze použít parametry a odpovídající `System.Runtime.CompilerServices` oboru názvů. Toto je atribut, který slouží k vložení název metody, která volá jinou metodu. To se obvykle používá jako způsob, jak eliminovat "magic řetězce" při implementaci v různých architektury uživatelského rozhraní INotifyPropertyChanged. Jako příklad:

[!code-csharp[Using CallerMemberName when implementing INotifyPropertyChanged](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CallerMemberName1)]

Ve výše uvedeném kódu, nemusíte mít literál `"Name"` řetězec. To pomáhá zabránit překlep související chyby a také udržuje pro hladší refaktoring/přejmenování.

## <a name="summary"></a>Souhrn

Atributy deklarativního power přenést do jazyka C#. Ale jsou formou kódem jako metadata a doby něco neuděláte samy o sobě.
