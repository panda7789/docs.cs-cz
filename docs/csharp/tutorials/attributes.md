---
title: 'Kurz: Použití atributů - C #'
description: Zjistěte, jak atributy fungují v c#.
author: mgroves
ms.technology: csharp-fundamentals
ms.date: 03/06/2017
ms.assetid: b152cf36-76e4-43a5-b805-1a1952e53b79
ms.openlocfilehash: 24cb7d35a89fda78511dc4ba725b69c5d601a008
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937474"
---
# <a name="use-attributes-in-c"></a>Použití atributů v C\#

Atributy poskytují způsob, jak připojovat informace s kódem deklarativním způsobem. Mohou také poskytnout opakovaně použitelný prvek, který lze použít na různé cíle.

Zvažte `[Obsolete]` atribut. Lze použít pro třídy, struktury, metody, konstruktory a další. _Deklaruje,_ že prvek je zastaralý. Je pak až kompilátor jazyka C# hledat tento atribut a provést nějakou akci v reakci.

V tomto kurzu se seznámíte s tím, jak přidat atributy do kódu, jak vytvořit a používat vlastní atributy a jak používat některé atributy, které jsou integrovány do .NET Core.

## <a name="prerequisites"></a>Požadavky
Budete muset nastavit počítač pro spuštění jádra .NET. Pokyny k instalaci naleznete na stránce [Ke stažení jádra .NET.](https://dotnet.microsoft.com/download)
Tuto aplikaci můžete spustit ve Windows, Ubuntu Linux, macOS nebo v kontejneru Dockeru.
Budete muset nainstalovat svůj oblíbený editor kódu. Níže uvedené popisy používají [Visual Studio Code,](https://code.visualstudio.com/) který je open source, cross platform editor. Nicméně, můžete použít bez ohledu na nástroje, které jsou pohodlné s.

## <a name="create-the-application"></a>Vytvoření aplikace

Teď, když jste nainstalovali všechny nástroje, vytvořte novou aplikaci .NET Core. Chcete-li použít generátor příkazového řádku, proveďte ve svém oblíbeném prostředí následující příkaz:

`dotnet new console`

Tento příkaz vytvoří soubory základního projektu .NET. Budete muset spustit `dotnet restore` obnovit závislosti potřebné ke kompilaci tohoto projektu.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Chcete-li spustit `dotnet run`program, použijte . Měli byste vidět výstup "Hello, World" do konzoly.

## <a name="how-to-add-attributes-to-code"></a>Jak přidat atributy do kódu

V jazyce C# jsou atributy `Attribute` třídy, které dědí ze základní třídy. Všechny třídy, `Attribute` které dědí z lze použít jako druh "tag" na jiné části kódu.
Například je atribut s `ObsoleteAttribute`názvem . Používá se k signalizaci, že kód je zastaralý a už by se neměl používat. Tento atribut můžete umístit do třídy, například pomocí hranatých závorek.

[!code-csharp[Obsolete attribute example](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ObsoleteExample1)]

Všimněte si, že `ObsoleteAttribute`zatímco třída se nazývá `[Obsolete]` , je nutné použít pouze v kódu. Toto je konvence, které c# následuje.
Pokud se rozhodnete, `[ObsoleteAttribute]` můžete použít celé jméno.

Při označování třídy zastaralé, je vhodné poskytnout některé informace o tom, *proč* je zastaralý, a / nebo *co* použít místo. To provést předáním parametru řetězce zastaralé atributu.

[!code-csharp[Obsolete attribute example with parameters](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ObsoleteExample2)]

Řetězec je předáván jako `ObsoleteAttribute` argument konstruktoru, stejně `var attr = new ObsoleteAttribute("some string")`jako jste psali .

Parametry konstruktoru atributu jsou omezeny na `bool, int, double, string, Type, enums, etc` jednoduché typy/literály: a pole těchto typů.
Nelze použít výraz nebo proměnnou. Můžete použít poziční nebo pojmenované parametry.

## <a name="how-to-create-your-own-attribute"></a>Jak vytvořit svůj vlastní atribut

Vytvoření atributu je stejně jednoduché `Attribute` jako dědění ze základní třídy.

[!code-csharp[Create your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CreateAttributeExample1)]

S výše uvedeným, nyní `[MySpecial]` mohu `[MySpecialAttribute]`použít (nebo ) jako atribut jinde v základu kódu.

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CreateAttributeExample2)]

Atributy v knihovně základní `ObsoleteAttribute` třídy .NET, jako je aktivace určitých chování v rámci kompilátoru. Však každý atribut, který vytvoříte funguje pouze jako metadata a nemá za následek žádný kód v rámci třídy atributu, které jsou prováděny. Je na vás, abyste na základě těchto metadat jednali jinde ve vašem kódu (více o tom později v kurzu).

Tam je 'gotcha' zde dávat pozor. Jak bylo uvedeno výše, pouze určité typy mohou být předány jako argumenty při použití atributů. Však při vytváření typu atributu kompilátor jazyka C# nezastaví vás od vytváření těchto parametrů. V níže uvedeném příkladu jsem vytvořil atribut s konstruktorem, který se zkompiluje v pohodě.

[!code-csharp[Valid constructor used in an attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeGothca1)]

Však nebude možné použít tento konstruktor s atributem syntaxe.

[!code-csharp[Invalid attempt to use the attribute constructor](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeGotcha2)]

Výše uvedené způsobí chybu kompilátoru, jako je`Attribute constructor parameter 'myClass' has type 'Foo', which is not a valid attribute parameter type`

## <a name="how-to-restrict-attribute-usage"></a>Jak omezit použití atributu

Atributy lze použít na několik "cílů". Výše uvedené příklady je zobrazují ve třídách, ale mohou být také použity na:

* Sestavení
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
* Returnvalue
* Struktura

Při vytváření třídy atributu ve výchozím nastavení c# vám umožní použít tento atribut na některý z možných cílů atributu. Pokud chcete omezit atribut na určité cíle, můžete tak `AttributeUsageAttribute` učinit pomocí na atribut třídy. To je pravda, atribut na atribut!

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeUsageExample1)]

Pokud se pokusíte dát výše uvedený atribut na něco, co není třída nebo struktura, dostanete chybu kompilátoru jako`Attribute 'MyAttributeForClassAndStructOnly' is not valid on this declaration type. It is only valid on 'class, struct' declarations`

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeUsageExample2)]

## <a name="how-to-use-attributes-attached-to-a-code-element"></a>Použití atributů připojených k prvku kódu

Atributy fungují jako metadata. Bez nějaké vnější síly, nebudou ve skutečnosti nic dělat.

Chcete-li najít a jednat na atributy, [Reflexe](../programming-guide/concepts/reflection.md) je obecně potřeba. Nebudu zahrnovat reflexe do hloubky v tomto kurzu, ale základní myšlenkou je, že reflexe umožňuje psát kód v jazyce C#, který zkoumá jiný kód.

Například můžete použít reflexe získat informace o `using System.Reflection;` třídě (přidat v čele kódu):

[!code-csharp[Getting type information with Reflection](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ReflectionExample1)]

To bude vytisknout něco jako:`The assembly qualified name of MyClass is ConsoleApplication.MyClass, attributes, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null`

Jakmile máte `TypeInfo` objekt (nebo `MemberInfo` `FieldInfo`, , atd.), `GetCustomAttributes` můžete použít metodu. Tím se vrátí `Attribute` kolekce objektů.
Můžete také `GetCustomAttribute` použít a určit typ atributu.

Zde je příklad použití `GetCustomAttributes` na `MemberInfo` instanci `MyClass` pro (které `[Obsolete]` jsme viděli dříve má atribut na to).

[!code-csharp[Getting type information with Reflection](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ReflectionExample2)]

To bude tisknout `Attribute on MyClass: ObsoleteAttribute`na konzoli: . Zkuste do `MyClass`hry přidat další atributy.

Je důležité si uvědomit, že tyto `Attribute` objekty jsou konsikovány líně. To znamená, že nebudou vytvořena instance, dokud `GetCustomAttribute` `GetCustomAttributes`nepoužijete nebo .
Jsou také konsitovány pokaždé. Volání `GetCustomAttributes` dvakrát za sebou vrátí dvě `ObsoleteAttribute`různé instance .

## <a name="common-attributes-in-the-base-class-library-bcl"></a>Běžné atributy v knihovně základních tříd (BCL)

Atributy jsou používány mnoha nástroji a rámci. NUnit používá atributy jako `[Test]` a `[TestFixture]` které jsou používány testovacíběžec NUnit. ASP.NET MVC používá `[Authorize]` atributy jako a poskytuje rozhraní filtru akce k provádění průřezových problémů s akcemi MVC. [PostSharp](https://www.postsharp.net) používá syntaxi atributu k povolení programování orientovaného na aspekt v jazyce C#.

Zde je několik pozoruhodných atributů integrovaných do knihoven základních tříd .NET Core:

* `[Obsolete]`. Tento byl použit ve výše uvedených příkladech `System` a žije v oboru názvů. Je užitečné poskytnout deklarativní dokumentaci o změně základu kódu. Zpráva může být poskytnuta ve formě řetězce a jiný logický parametr lze použít k eskalaci z upozornění kompilátoru na chybu kompilátoru.

* `[Conditional]`. Tento atribut je `System.Diagnostics` v oboru názvů. Tento atribut lze použít pro metody (nebo třídy atributů). Je nutné předat řetězec konstruktoru.
Pokud tento řetězec neodpovídá `#define` direktivě, budou všechna volání této metody (ale ne samotné metody) odebrána kompilátorem jazyka C#. Obvykle se používá pro účely ladění (diagnostiky).

* `[CallerMemberName]`. Tento atribut lze použít na parametry `System.Runtime.CompilerServices` a žije v oboru názvů. Toto je atribut, který se používá k vložení název metody, která volá jinou metodu. To se obvykle používá jako způsob, jak eliminovat 'magické řetězce' při implementaci INotifyPropertyChanged v různých architekturách ui. Příklad:

[!code-csharp[Using CallerMemberName when implementing INotifyPropertyChanged](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CallerMemberName1)]

Ve výše uvedeném kódu nemusíte mít literál `"Name"` řetězec. To může pomoci zabránit chybám souvisejícím s překlepy a také usnadňuje refaktoring/přejmenování.

## <a name="summary"></a>Souhrn

Atributy přinášejí deklarativní moc do jazyka C#, ale jsou metadatnou formou kódu a nejednají samy.
