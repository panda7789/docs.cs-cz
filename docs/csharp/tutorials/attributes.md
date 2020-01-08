---
title: AtributC#
description: Přečtěte si, jak C#atributy fungují v.
author: mgroves
ms.technology: csharp-fundamentals
ms.date: 03/06/2017
ms.assetid: b152cf36-76e4-43a5-b805-1a1952e53b79
ms.openlocfilehash: 6e200b151f3b2d84764dcdb379186d72f560eb22
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346823"
---
# <a name="use-attributes-in-c"></a>Použití atributů v jazyce C\#

Atributy poskytují způsob, jak přidružit informace s kódem deklarativním způsobem. Mohou také poskytovat opakovaně použitelný prvek, který lze použít na celou řadu cílů.

Vezměte v úvahu atribut `[Obsolete]`. Dá se použít na třídy, struktury, metody, konstruktory a další. _Deklaruje_ , že prvek je zastaralý. Následně až do C# kompilátoru vyhledáte tento atribut a v reakci Udělejte nějakou akci.

V tomto kurzu se seznámíte s postupem přidávání atributů do kódu, vytváření a používání vlastních atributů a používání některých atributů, které jsou součástí .NET Core.

## <a name="prerequisites"></a>Požadavky
Budete muset nastavit počítač tak, aby běžel .NET Core. Pokyny k instalaci najdete na stránce [soubory ke stažení pro .NET Core](https://dotnet.microsoft.com/download) .
Tuto aplikaci můžete spustit ve Windows, Ubuntu Linux, macOS nebo v kontejneru Docker.
Budete muset nainstalovat svůj oblíbený editor kódu. Níže uvedené popisy používají [Visual Studio Code](https://code.visualstudio.com/) , což je Open Source Editor pro různé platformy. Můžete ale použít jakékoli nástroje, se kterými máte v pohodlí.

## <a name="create-the-application"></a>Vytvoření aplikace

Teď, když jste nainstalovali všechny nástroje, vytvořte novou aplikaci .NET Core. Pokud chcete použít generátor příkazového řádku, spusťte ve svém oblíbeném prostředí následující příkaz:

`dotnet new console`

Tento příkaz vytvoří holé soubory projektu .NET Core. Aby bylo možné obnovit závislosti potřebné k zkompilování tohoto projektu, bude nutné provést `dotnet restore`.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Chcete-li spustit program, použijte `dotnet run`. Měl by se zobrazit výstup "Hello, World" do konzoly.

## <a name="how-to-add-attributes-to-code"></a>Postup přidání atributů do kódu

V C#rozhraní jsou atributy třídy, které dědí z `Attribute` základní třídy. Libovolnou třídu, která dědí z `Attribute` lze použít jako řazení "značky" v jiných částech kódu.
Například existuje atribut nazvaný `ObsoleteAttribute`. Používá se k signalizaci, že kód je zastaralý a neměl by se už používat. Tento atribut lze umístit na třídu například pomocí hranatých závorek.

[!code-csharp[Obsolete attribute example](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ObsoleteExample1)]

Všimněte si, že i když je třída volána `ObsoleteAttribute`, je nutné použít `[Obsolete]` v kódu. Toto je konvence, C# která následuje.
Pokud zvolíte, můžete použít celé jméno `[ObsoleteAttribute]`.

Když označíte třídu jako zastaralou, je vhodné poskytnout nějaké informace, *Proč* je zastaralá a/nebo *co* použít místo toho. Provedete to tak, že předáte řetězcový parametr do zastaralého atributu.

[!code-csharp[Obsolete attribute example with parameters](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ObsoleteExample2)]

Řetězec je předáván jako argument konstruktoru `ObsoleteAttribute`, stejně jako při psaní `var attr = new ObsoleteAttribute("some string")`.

Parametry konstruktoru atributu jsou omezeny na jednoduché typy/literály: `bool, int, double, string, Type, enums, etc` a pole těchto typů.
Nelze použít výraz ani proměnnou. Pro použití pozičních nebo pojmenovaných parametrů je zdarma.

## <a name="how-to-create-your-own-attribute"></a>Vytvoření vlastního atributu

Vytvoření atributu je jednoduché jako dědění z `Attribute` základní třídy.

[!code-csharp[Create your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CreateAttributeExample1)]

Výše uvedeným způsobem teď můžu použít `[MySpecial]` (nebo `[MySpecialAttribute]`) jako atribut jinde v základu kódu.

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CreateAttributeExample2)]

Atributy v knihovně základních tříd .NET, jako `ObsoleteAttribute`, spouštějí určité chování v rámci kompilátoru. Jakýkoli atribut, který vytvoříte, ale funguje pouze jako metadata a nevede se o spuštění kódu v rámci třídy atributů. Je to až na to, abyste mohli pracovat s metadaty jinde v kódu (Další informace najdete v tomto kurzu dále).

Tady je Gotcha, kde můžete sledovat. Jak je uvedeno výše, při použití atributů můžou být jako argumenty předány jenom určité typy. Při vytváření typu atributu ale C# kompilátor nebrání v vytváření těchto parametrů. V následujícím příkladu jsem vytvořil atribut s konstruktorem, který se zkompiluje přesně.

[!code-csharp[Valid constructor used in an attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeGothca1)]

Tento konstruktor však nebude možné použít se syntaxí atributu.

[!code-csharp[Invalid attempt to use the attribute constructor](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeGotcha2)]

Výše uvedené způsobí chybu kompilátoru, například `Attribute constructor parameter 'myClass' has type 'Foo', which is not a valid attribute parameter type`

## <a name="how-to-restrict-attribute-usage"></a>Jak omezit použití atributů

Atributy lze použít v řadě "cíle". Výše uvedené příklady je ukazují na třídy, ale lze je použít také na:

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
* – modul
* Parametr
* Vlastnost
* ReturnValue
* Struktura

Když vytvoříte třídu atributu, ve výchozím nastavení C# vám umožní použít tento atribut u libovolné možné cíle atributu. Pokud chcete omezit atribut na určité cíle, můžete tak učinit pomocí `AttributeUsageAttribute` ve třídě atributů. To je správné, atribut u atributu!

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeUsageExample1)]

Pokud se pokusíte umístit výše uvedený atribut na něco, co není třídou nebo strukturou, zobrazí se chyba kompilátoru, například `Attribute 'MyAttributeForClassAndStructOnly' is not valid on this declaration type. It is only valid on 'class, struct' declarations`

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeUsageExample2)]

## <a name="how-to-use-attributes-attached-to-a-code-element"></a>Jak používat atributy připojené k elementu kódu

Atributy fungují jako metadata. Bez některých pasivních sil nebudou ve skutečnosti dělat cokoli.

Chcete-li najít atributy a pracovat s nimi, je obvykle potřeba [reflexe](../programming-guide/concepts/reflection.md) . V tomto kurzu nevidím podrobně zamyšlení, ale základní nápad je, že reflexe umožňuje psát kód v C# , který prověřuje jiný kód.

Například můžete použít reflexi k získání informací o třídě (přidejte `using System.Reflection;` v hlavičce kódu):

[!code-csharp[Getting type information with Reflection](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ReflectionExample1)]

Tím se vytiskne něco jako: `The assembly qualified name of MyClass is ConsoleApplication.MyClass, attributes, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null`

Jakmile budete mít objekt `TypeInfo` (nebo `MemberInfo`, `FieldInfo`atd.), můžete použít metodu `GetCustomAttributes`. Tím se vrátí kolekce objektů `Attribute`.
Můžete také použít `GetCustomAttribute` a zadat typ atributu.

Tady je příklad použití `GetCustomAttributes` u instance `MemberInfo` pro `MyClass` (u kterých se dřív ukázala, že má atribut `[Obsolete]`).

[!code-csharp[Getting type information with Reflection](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ReflectionExample2)]

Který bude tisknout do konzoly: `Attribute on MyClass: ObsoleteAttribute`. Zkuste do `MyClass`přidat další atributy.

Je důležité si uvědomit, že tyto objekty `Attribute` jsou instancemi laxně vytvářená. To znamená, že nebudou vytvořeny instance, dokud nepoužijete `GetCustomAttribute` nebo `GetCustomAttributes`.
Jsou také vytvořeny instance. Volání `GetCustomAttributes` dvakrát v řádku vrátí dvě různé instance `ObsoleteAttribute`.

## <a name="common-attributes-in-the-base-class-library-bcl"></a>Běžné atributy v knihovně základních tříd (BCL)

Atributy používá mnoho nástrojů a platforem. NUnit používá atributy jako `[Test]` a `[TestFixture]`, které jsou používány nástrojem NUnit Test Runner. ASP.NET MVC používá atributy jako `[Authorize]` a poskytuje rozhraní filtru akcí, které umožňuje provádět průřezy na akcích MVC. [PostSharp](https://www.postsharp.net) používá syntaxi atributu k umožnění programování orientovaného na jednotlivé C#aspekty v.

Tady je několik významných atributů integrovaných do knihoven základních tříd .NET Core:

* `[Obsolete]`. Tato verze se použila ve výše uvedených příkladech a je v oboru názvů `System`. Je užitečné poskytnout deklarativní dokumentaci ke změně základu kódu. Zpráva může být poskytnuta ve formě řetězce a další logický parametr lze použít k eskalaci z upozornění kompilátoru na chybu kompilátoru.

* `[Conditional]`. Tento atribut je v oboru názvů `System.Diagnostics`. Tento atribut lze použít na metody (nebo třídy atributů). Do konstruktoru musíte předat řetězec.
Pokud se tento řetězec neshoduje s direktivou `#define`, pak C# kompilátor odebere všechna volání této metody (ale ne samotné metody). Obvykle se používá pro účely ladění (diagnostiky).

* `[CallerMemberName]`. Tento atribut lze použít pro parametry a v oboru názvů `System.Runtime.CompilerServices`. Toto je atribut, který se používá k vložení názvu metody, která volá jinou metodu. Obvykle se používá jako způsob, jak eliminovat řetězce Magic při implementaci INotifyPropertyChanged v různých architekturách uživatelského rozhraní. Jako příklad:

[!code-csharp[Using CallerMemberName when implementing INotifyPropertyChanged](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CallerMemberName1)]

Ve výše uvedeném kódu není nutné mít literál `"Name"` řetězec. To může přispět k tomu, aby se předešlo chybám souvisejícím s překlepem a také docházelo k plynulejšímu refaktoringu/přejmenování

## <a name="summary"></a>Přehled

Atributy přinášejí deklarativní sílu C#na, ale jsou meta datovým formulářem kódu a nejednají sami sebe.
