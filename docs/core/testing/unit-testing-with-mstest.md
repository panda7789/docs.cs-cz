---
title: Testování C# částí pomocí MSTest a .NET Core
description: Seznamte se s koncepty C# testování částí v a .NET Core pomocí interaktivního prostředí, které vytváří ukázkové řešení pomocí příkazu dotnet test a MSTest.
author: ncarandini
ms.author: wiwagn
ms.date: 09/08/2017
ms.openlocfilehash: bd7891243d84277a7578089f8b4629ff5bada577
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240906"
---
# <a name="unit-testing-c-with-mstest-and-net-core"></a>Testování C# částí pomocí MSTest a .NET Core

Tento kurz vás provede interaktivním vytvořením ukázkového řešení, které vás seznámí s koncepty testování částí. Pokud chcete postupovat podle kurzu s předdefinovaným řešením, zobrazte si [ukázkový kód](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/) před jeho zahájením nebo si ho stáhněte. Pokyny ke stažení najdete v tématu [ukázky a kurzy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="create-the-source-project"></a>Vytvořit zdrojový projekt

Otevřete okno prostředí. Vytvořte adresář s názvem *Unit-Testing-using-MSTest* pro uložení řešení. V tomto novém adresáři spusťte [`dotnet new sln`](../tools/dotnet-new.md) a vytvořte nový soubor řešení pro knihovnu tříd a testovací projekt. Potom vytvořte adresář *PrimeService* . Následující osnova ukazuje strukturu adresářů a souborů, které jsou tak daleko:

```console
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
```

Vytvořte *PrimeService* aktuální adresář a spusťte [`dotnet new classlib`](../tools/dotnet-new.md) pro vytvoření zdrojového projektu. Přejmenujte *Class1.cs* na *PrimeService.cs*. Vytvoříte selhání implementace `PrimeService` třídy:

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

Změňte adresář zpátky na adresář s *testováním jednotek pomocí-MSTest* . Spusťte [`dotnet sln add PrimeService/PrimeService.csproj`](../tools/dotnet-sln.md) pro přidání projektu knihovny tříd do řešení.

## <a name="create-the-test-project"></a>Vytvořte projekt testu

Dále vytvořte adresář *PrimeService. Tests* . Následující osnova znázorňuje adresářovou strukturu:

```console
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

Nastavte adresář *PrimeService. Tests* na aktuální adresář a vytvořte nový projekt pomocí [`dotnet new mstest`](../tools/dotnet-new.md). Příkaz dotnet New vytvoří testovací projekt, který jako knihovnu testů používá MSTest. Vygenerovaná šablona konfiguruje Test Runner v souboru *PrimeServiceTests. csproj* :

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

Testovací projekt vyžaduje pro vytvoření a spuštění testů jednotek další balíčky. `dotnet new` v předchozím kroku jsme přidali sadu SDK MSTest, rozhraní MSTest test Framework a MSTest Runner. Nyní přidejte knihovnu tříd `PrimeService` jako jinou závislost do projektu. Použijte příkaz [`dotnet add reference`](../tools/dotnet-add-reference.md) :

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.csproj
```

Celý soubor můžete zobrazit v [úložišti ukázek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj) na GitHubu.

Následující osnova znázorňuje konečné rozložení řešení:

```console
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.csproj
```

Spusťte [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) v adresáři *Unit-Testing-using-MSTest* .

## <a name="create-the-first-test"></a>Vytvoření prvního testu

Napíšete jeden neúspěšný test, udělejte ho a pak proces opakujte. Odeberte *UnitTest1.cs* z adresáře *PrimeService. Tests* a vytvořte nový C# soubor s názvem *PrimeService_IsPrimeShould. cs* s následujícím obsahem:

```csharp
using Microsoft.VisualStudio.TestTools.UnitTesting;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    [TestClass]
    public class PrimeService_IsPrimeShould
    {
        private readonly PrimeService _primeService;

        public PrimeService_IsPrimeShould()
        {
            _primeService = new PrimeService();
        }

        [TestMethod]
        public void IsPrime_InputIs1_ReturnFalse()
        {
            var result = _primeService.IsPrime(1);

            Assert.IsFalse(result, "1 should not be prime");
        }
    }
}
```

[Atribut TestClass](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) označuje třídu, která obsahuje testy jednotek. [Atribut TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) označuje, že metoda je metodou testu.

Uložte tento soubor a spusťte [`dotnet test`](../tools/dotnet-test.md) pro sestavení testů a knihovny tříd a potom spusťte testy. MSTest Test Runner obsahuje vstupní bod programu pro spuštění testů. `dotnet test` spustí Test Runner pomocí projektu testování částí, který jste vytvořili.

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

V adresáři *Unit-Testing-using-MSTest* znovu spusťte `dotnet test`. Příkaz `dotnet test` spustí sestavení pro projekt `PrimeService` a potom pro projekt `PrimeService.Tests`. Po sestavení obou projektů spustí tento jediný test. Předá.

## <a name="add-more-features"></a>Přidat další funkce

Teď, když jste udělali jeden test Pass, je čas zapsat další. Pro čísla apostrofů existuje několik dalších jednoduchých případů: 0,-1. Můžete přidat nové testy s [atributem TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute), ale to se rychle bude zdlouhavé. Existují další atributy MSTest, které umožňují napsat sadu podobných testů.  [Atribut DataTestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataTestMethodAttribute) představuje sadu testů, které spouštějí stejný kód, ale mají různé vstupní argumenty. Pomocí [atributu DataRow](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataRowAttribute) můžete zadat hodnoty pro tyto vstupy.

Namísto vytváření nových testů použijte tyto dva atributy k vytvoření jednoho testu řízeného daty. Test řízený daty je metoda, která testuje několik hodnot menší než dvě, což je nejnižší číslo základny:

[!code-csharp[Sample_TestCode](../../../samples/snippets/core/testing/unit-testing-using-mstest/csharp/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

Spusťte `dotnet test`a dva z těchto testů selžou. Chcete-li provést všechny testy Pass, změňte klauzuli `if` na začátku metody:

```csharp
if (candidate < 2)
```

Pokračujte v iteraci přidáním dalších testů, více teorie a další kód v hlavní knihovně. Máte [hotovou verzi testů](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs) a [úplnou implementaci knihovny](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs).

Vytvořili jste malou knihovnu a sadu testů jednotek pro tuto knihovnu. Rozpracovali jste řešení, aby přidávání nových balíčků a testů bylo součástí normálního pracovního postupu. Vyrostli jste většinu času a úsilí při řešení cílů aplikace.

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting>
- [Použití rozhraní MSTest v testování částí](/visualstudio/test/using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests)
- [Dokumentace k testovacímu rozhraní MSTest v2](https://github.com/Microsoft/testfx-docs)
