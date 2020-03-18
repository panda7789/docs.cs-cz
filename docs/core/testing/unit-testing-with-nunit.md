---
title: Testování jednotek u kódu v jazyce C# s použitím NUnit a .NET Core
description: Naučte koncepty testování částí v C# a .NET Core prostřednictvím interaktivní ho dání prostřednictvím vytváření ukázkového řešení krok za krokem pomocí dotnet test a NUnit.
author: rprouse
ms.date: 08/31/2018
ms.openlocfilehash: 283aa5a28ed213d4290eb3c73a98af56ec074ad0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240880"
---
# <a name="unit-testing-c-with-nunit-and-net-core"></a>Testování jednotek u kódu v jazyce C# s použitím NUnit a .NET Core

Tento kurz vás provede interaktivní prostředí vytváření ukázkové řešení krok za krokem se dozvíte koncepty testování částí. Pokud dáváte přednost postupujte podle kurzu pomocí předem sestaveného řešení, [zobrazte nebo stáhněte ukázkový kód,](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/) než začnete. Pokyny ke stažení naleznete v [tématu Ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="prerequisites"></a>Požadavky

- [Sada .NET Core 2.1 SDK](https://dotnet.microsoft.com/download) nebo novější verze.
- Textový editor nebo editor kódu podle vašeho výběru.

## <a name="creating-the-source-project"></a>Vytvoření zdrojového projektu

Otevřete okno prostředí. Vytvořte adresář s názvem *unit-testing-using-nunit* pro uložení řešení. V tomto novém adresáři spusťte následující příkaz a vytvořte nový soubor řešení pro knihovnu tříd a testovací projekt:

```dotnetcli
dotnet new sln
```

Dále vytvořte adresář *PrimeService.* Následující osnova ukazuje adresář a strukturu souborů tak daleko:

```console
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
```

Vytvořte *primeservice* jako aktuální adresář a spusťte následující příkaz k vytvoření zdrojového projektu:

```dotnetcli
dotnet new classlib
```

Přejmenujte *Class1.cs* na *PrimeService.cs*. Můžete vytvořit selhání implementace `PrimeService` třídy:

```csharp
using System;

namespace Prime.Services
{
    public class PrimeService
    {
        public bool IsPrime(int candidate)
        {
            throw new NotImplementedException("Please create a test first.");
        }
    }
}
```

Změňte adresář zpět do adresáře *unit-testing-using-nunit.* Chcete-li do řešení přidat projekt knihovny tříd, spusťte následující příkaz:

```dotnetcli
dotnet sln add PrimeService/PrimeService.csproj
```

## <a name="creating-the-test-project"></a>Vytvoření testovacího projektu

Dále vytvořte adresář *PrimeService.Tests.* Následující osnova ukazuje adresářovou strukturu:

```console
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

Vytvořte adresář *PrimeService.Tests* jako aktuální adresář a vytvořte nový projekt pomocí následujícího příkazu:

```dotnetcli
dotnet new nunit
```

[Dotnet new](../tools/dotnet-new.md) příkaz vytvoří testovací projekt, který používá NUnit jako testovací knihovnu. Vygenerovaná šablona konfiguruje testovacího běžce v souboru *PrimeService.Tests.csproj:*

[!code-xml[Packages](~/samples/snippets/core/testing/unit-testing-using-nunit/csharp/PrimeService.Tests/PrimeService.Tests.csproj#Packages)]

Testovací projekt vyžaduje další balíčky k vytvoření a spuštění testů částí. `dotnet new`V předchozím kroku přidánmicrosoft test SDK, NUnit testovací rámec a NUnit testovací adaptér. Nyní přidejte `PrimeService` knihovnu tříd jako jinou závislost do projektu. Použijte [`dotnet add reference`](../tools/dotnet-add-reference.md) příkaz:

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.csproj
```

Celý soubor můžete vidět v [úložišti ukázek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj) na GitHubu.

Následující osnova ukazuje konečné rozložení řešení:

```console
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeService.Tests.csproj
```

V adresáři *jednotky testování nunit proveďte* následující příkaz:

```dotnetcli
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
```

## <a name="creating-the-first-test"></a>Vytvoření prvního testu

Napíšete jeden neúspěšný test, provedete jeho předání a pak zopakujete proces. V adresáři *PrimeService.Tests* přejmenujte soubor *UnitTest1.cs* na *soubor PrimeService_IsPrimeShould.cs* a nahraďte celý jeho obsah následujícím kódem:

[!code-csharp[Sample_FirstTest](~/samples/snippets/core/testing/unit-testing-using-nunit/csharp/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_FirstTest)]

Atribut `[TestFixture]` označuje třídu, která obsahuje testy částí. Atribut `[Test]` označuje, že metoda je zkušební metoda.

Uložte tento [`dotnet test`](../tools/dotnet-test.md) soubor a spusťte k sestavení testů a knihovny tříd a pak spusťte testy. Testovací běžec NUnit obsahuje vstupní bod programu pro spuštění testů. `dotnet test`spustí testovací houska pomocí projektu testování částí, který jste vytvořili.

Váš test se nezdaří. Ještě jste nevytvořili implementaci. Proveďte tento test projít napsáním `PrimeService` nejjednodušší kód ve třídě, která funguje:

```csharp
public bool IsPrime(int candidate)
{
    if (candidate == 1)
    {
        return false;
    }
    throw new NotImplementedException("Please create a test first.");
}
```

V adresáři *unit-testing-using-nunit* spusťte `dotnet test` znovu. Příkaz `dotnet test` spustí sestavení pro `PrimeService` projekt a `PrimeService.Tests` potom pro projekt. Po sestavení obou projektů spustí tento jediný test. Už to přejde.

## <a name="adding-more-features"></a>Přidání dalších funkcí

Nyní, když jste provedli jeden test projít, je čas napsat více. Existuje několik dalších jednoduchých případů pro prvočísla: 0, -1. Můžete přidat nové testy `[Test]` s atributem, ale to se rychle stává únavné. Existují další Atributy NUnit, které umožňují napsat sadu podobných testů.  Atribut `[TestCase]` se používá k vytvoření sady testů, které spouštějí stejný kód, ale mají různé vstupní argumenty. `[TestCase]` Atribut můžete použít k určení hodnot pro tyto vstupy.

Namísto vytváření nových testů použijte tento atribut k vytvoření jednoho testu řízeného daty. Test řízený daty je metoda, která testuje několik hodnot menší než dvě, což je nejnižší prvočíslo:

[!code-csharp[Sample_TestCode](~/samples/snippets/core/testing/unit-testing-using-nunit/csharp/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

Spustit `dotnet test`a dva z těchto testů nezdaří. Chcete-li provést všechny testy `if` projít, změňte `Main` klauzuli na začátku metody v *souboru PrimeService.cs:*

```csharp
if (candidate < 2)
```

Pokračujte v iterátu přidáním dalších testů, dalších teorií a dalšího kódu v hlavní knihovně. Máte [hotovou verzi testů](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs) a [kompletní implementaci knihovny](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService/PrimeService.cs).

Vytvořili jste malou knihovnu a sadu testů částí pro tuto knihovnu. Strukturovali jste řešení tak, aby přidání nových balíčků a testů bylo součástí normálního pracovního postupu. Soustředili jste většinu svého času a úsilí na řešení cílů aplikace.
