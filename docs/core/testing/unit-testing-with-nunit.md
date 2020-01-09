---
title: Testování C# částí pomocí nunit a .NET Core
description: Seznamte se s koncepty C# testování částí v a .NET Core pomocí interaktivního prostředí, které vytváří ukázkové řešení pomocí příkazu dotnet test a nunit.
author: rprouse
ms.date: 08/31/2018
ms.openlocfilehash: 1ea17d9f830d8ac20e2bad79eebab5db767e0af8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714217"
---
# <a name="unit-testing-c-with-nunit-and-net-core"></a>Testování C# částí pomocí nunit a .NET Core

Tento kurz vás provede interaktivním vytvořením ukázkového řešení, které vás seznámí s koncepty testování částí. Pokud chcete postupovat podle kurzu s předdefinovaným řešením, zobrazte si [ukázkový kód](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/) před jeho zahájením nebo si ho stáhněte. Pokyny ke stažení najdete v tématu [ukázky a kurzy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="prerequisites"></a>Požadavky

- [.NET Core 2,1 SDK](https://dotnet.microsoft.com/download) nebo novější verze.
- Textový editor nebo editor kódu podle vašeho výběru.

## <a name="creating-the-source-project"></a>Vytvoření zdrojového projektu

Otevřete okno prostředí. Vytvořte adresář s názvem *Unit-Testing-using-nunit* pro uložení řešení. V tomto novém adresáři spusťte následující příkaz, který vytvoří nový soubor řešení pro knihovnu tříd a testovací projekt:

```dotnetcli
dotnet new sln
```
 
Potom vytvořte adresář *PrimeService* . Následující osnova ukazuje strukturu adresářů a souborů, které jsou tak daleko:

```console
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
```

Vytvořte *PrimeService* aktuální adresář a spusťte následující příkaz pro vytvoření zdrojového projektu:

```dotnetcli
dotnet new classlib
```

Přejmenujte *Class1.cs* na *PrimeService.cs*. Vytvoříte selhání implementace `PrimeService` třídy:

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

Změňte adresář zpátky na adresář s *testováním jednotek pomocí-nunit* . Spuštěním následujícího příkazu přidejte projekt knihovny tříd do řešení:

```dotnetcli
dotnet sln add PrimeService/PrimeService.csproj
```

## <a name="creating-the-test-project"></a>Vytváření testovacího projektu

Dále vytvořte adresář *PrimeService. Tests* . Následující osnova znázorňuje adresářovou strukturu:

```console
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

Vytvořte adresář *PrimeService. Tests* pro aktuální adresář a vytvořte nový projekt pomocí následujícího příkazu:

```dotnetcli
dotnet new nunit
```

Příkaz [dotnet New](../tools/dotnet-new.md) vytvoří testovací projekt, který jako knihovnu testů používá nunit. Vygenerovaná šablona konfiguruje Test Runner v souboru *PrimeService. Tests. csproj* :

[!code-xml[Packages](~/samples/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj#Packages)]

Testovací projekt vyžaduje pro vytvoření a spuštění testů jednotek další balíčky. `dotnet new` v předchozím kroku se přidala sada Microsoft Test SDK, testovací rozhraní NUnit a testovací adaptér NUnit. Nyní přidejte knihovnu tříd `PrimeService` jako jinou závislost do projektu. Použijte příkaz [`dotnet add reference`](../tools/dotnet-add-reference.md) :

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.csproj
```

Celý soubor můžete zobrazit v [úložišti ukázek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj) na GitHubu.

Následující osnova znázorňuje konečné rozložení řešení:

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

Spusťte následující příkaz v adresáři *Unit-Test-Using-nunit* :

```dotnetcli
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
```

## <a name="creating-the-first-test"></a>Vytvoření prvního testu

Napíšete jeden neúspěšný test, udělejte ho a pak proces opakujte. V adresáři *PrimeService. Tests* přejmenujte soubor *UnitTest1.cs* na *PrimeService_IsPrimeShould. cs* a nahraďte jeho celý obsah následujícím kódem:

```csharp
using NUnit.Framework;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    [TestFixture]
    public class PrimeService_IsPrimeShould
    {
        [Test]
        public void IsPrime_InputIs1_ReturnFalse()
        {
            PrimeService primeService = CreatePrimeService();
            var result = primeService.IsPrime(1);

            Assert.IsFalse(result, "1 should not be prime");
        }
        
        /*
        More tests
        */
        
        private PrimeService CreatePrimeService()
        {
             return new PrimeService();
        }
    }
}
```

Atribut `[TestFixture]` označuje třídu, která obsahuje testy jednotek. Atribut `[Test]` označuje metodu, která je metodou testu.

Uložte tento soubor a spusťte [`dotnet test`](../tools/dotnet-test.md) pro sestavení testů a knihovny tříd a potom spusťte testy. NUnit Test Runner obsahuje vstupní bod programu pro spuštění testů. `dotnet test` spustí Test Runner pomocí projektu testování částí, který jste vytvořili.

Test se nezdařil. Ještě jste nevytvořili implementaci. Proveďte tento test průchodu tak, že napíšete nejjednodušší kód ve třídě `PrimeService`, která funguje:

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

V adresáři *Unit-Testing-using-nunit* znovu spusťte `dotnet test`. Příkaz `dotnet test` spustí sestavení pro projekt `PrimeService` a potom pro projekt `PrimeService.Tests`. Po sestavení obou projektů spustí tento jediný test. Předá.

## <a name="adding-more-features"></a>Přidání dalších funkcí

Teď, když jste udělali jeden test Pass, je čas zapsat další. Pro čísla apostrofů existuje několik dalších jednoduchých případů: 0,-1. Můžete přidat nové testy s atributem `[Test]`, ale to se rychle bude zdlouhavé. Existují další atributy NUnit, které umožňují napsat sadu podobných testů.  Atribut `[TestCase]` slouží k vytvoření sady testů, které spouštějí stejný kód, ale mají různé vstupní argumenty. Pomocí atributu `[TestCase]` můžete zadat hodnoty pro tyto vstupy.

Místo vytváření nových testů použijte tento atribut k vytvoření jednoho testu řízeného daty. Test řízený daty je metoda, která testuje několik hodnot menší než dvě, což je nejnižší číslo základny:

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

Spusťte `dotnet test`a dva z těchto testů selžou. Chcete-li provést všechny testy Pass, změňte klauzuli `if` na začátku `Main` metody v souboru *PrimeService.cs* :

```csharp
if (candidate < 2)
```

Pokračujte v iteraci přidáním dalších testů, více teorie a další kód v hlavní knihovně. Máte [hotovou verzi testů](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs) a [úplnou implementaci knihovny](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService/PrimeService.cs).

Vytvořili jste malou knihovnu a sadu testů jednotek pro tuto knihovnu. Rozpracovali jste řešení, aby přidávání nových balíčků a testů bylo součástí normálního pracovního postupu. Vyrostli jste většinu času a úsilí při řešení cílů aplikace.
