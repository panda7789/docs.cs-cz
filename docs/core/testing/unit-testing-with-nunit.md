---
title: Testování C# s použitím NUnit a .NET Core jednotky
description: Další koncepty test jednotky v C# a .NET Core prostřednictvím interaktivní prostředí sestavování podrobné ukázkové řešení pomocí testovacích dotnet a NUnit.
author: rprouse
ms.date: 12/01/2017
ms.openlocfilehash: 8cf9e28353dd4dad6143f0dc3f8c0a8245715ea2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="unit-testing-c-with-nunit-and-net-core"></a>Testování C# s použitím NUnit a .NET Core jednotky

Tento kurz vás provede interaktivní prostředí vytváření ukázkové řešení podrobné další koncepty testování částí. Pokud chcete postupovat v kurzu pomocí předdefinovaných řešení, [zobrazení nebo stažení ukázkového kódu](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/) před zahájením. Pokyny ke stažení najdete v tématu [ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="creating-the-source-project"></a>Vytvoření projektu zdroje

Otevřete okno prostředí. Vytvořte adresář s názvem *jednotky – testování pomocí nunit* pro uložení řešení. Uvnitř tohoto nového adresáře, spusťte [ `dotnet new sln` ](../tools/dotnet-new.md) vytvořit nový soubor řešení pro knihovny tříd a k testovacímu projektu. Dále vytvořte *PrimeService* adresáře. Následující obrys doposud ukazuje strukturu adresáře a souboru:

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
```

Ujistěte se, *PrimeService* aktuální adresář a spusťte [ `dotnet new classlib` ](../tools/dotnet-new.md) a vytvořte tak projekt zdroje. Přejmenování *Class1.cs* k *PrimeService.cs*. Použití vývoje řízeného testováním (TDD), vytvořte na selhání implementace `PrimeService` třídy:

```csharp
using System;

namespace Prime.Services
{
    public class PrimeService
    {
        public bool IsPrime(int candidate)
        {
            throw new NotImplementedException("Please create a test first");
        }
    }
}
```

Změna adresáře zpět do *jednotky – testování pomocí nunit* adresáře. Spustit [ `dotnet sln add PrimeService/PrimeService.csproj` ](../tools/dotnet-sln.md) přidání projektu knihovny tříd do řešení.

## <a name="install-the-nunit-project-template"></a>Šablona projektu NUnit instalace

NUnit testování projektu, který je potřeba nainstalovat před vytvořením testovacího projektu šablony. To jenom je nutné provést jednou na každém počítači vývojáře, kde vytvoříte nové projekty NUnit. Spustit [ `dotnet new -i NUnit3.DotNetNew.Template` ](../tools/dotnet-new.md) instalovat NUnit šablony.

```
dotnet new -i NUnit3.DotNetNew.Template
```

### <a name="creating-the-test-project"></a>Vytvoření projektu testů

Dále vytvořte *PrimeService.Tests* adresáře. Zobrazí následující osnova adresářovou strukturu:

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

Ujistěte se, *PrimeService.Tests* adresář aktuální adresář a vytvoření nového projektu pomocí [ `dotnet new nunit` ](../tools/dotnet-new.md). Nový příkaz dotnet vytvoří testovací projekt, který používá NUnit jako knihovně testu. Nástroj test runner v nakonfiguruje vygenerované šablony *PrimeServiceTests.csproj* souboru:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

K testovacímu projektu vyžaduje další balíčky k vytváření a spouštění testování částí. `dotnet new` v předchozím kroku přidat Microsoft test SDK, rozhraní test NUnit a adaptér testovací NUnit. Nyní přidejte `PrimeService` knihovny tříd jako další závislosti do projektu. Použití [ `dotnet add reference` ](../tools/dotnet-add-reference.md) příkaz:

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

Zobrazí celý soubor v [ukázky úložiště](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService.Tests.csproj) na Githubu.

Zobrazí následující osnova rozložení konečné řešení:

```
/unit-testing-using-nunit
    unit-testing-using-nunit.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.csproj
```

Spuštění [ `dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj` ](../tools/dotnet-sln.md) v *testování pomocí dotnet – testování* adresáře.

## <a name="creating-the-first-test"></a>Vytvoření prvního testu

Volá TDD přístup pro zápis jeden selhání test, což předat a zopakováním postupu. Odebrat *UnitTest1.cs* z *PrimeService.Tests* adresáře a vytvořte nový soubor C# s s názvem *PrimeService_IsPrimeShould.cs* s následujícím obsahem:

```csharp
using NUnit.Framework;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    [TestFixture]
    public class PrimeService_IsPrimeShould
    {
        private readonly PrimeService _primeService;

        public PrimeService_IsPrimeShould()
        {
            _primeService = new PrimeService();
        }

        [Test]
        public void ReturnFalseGivenValueOf1()
        {
            var result = _primeService.IsPrime(1);

            Assert.IsFalse(result, "1 should not be prime");
        }
    }
}
```

`[TestFixture]` Atribut označuje třídu, která obsahuje testování částí. `[Test]` Atribut uvádí, že je metoda metodou test.

Uložte tento soubor a spusťte [ `dotnet test` ](../tools/dotnet-test.md) vytvářet testy a knihovny tříd a poté spusťte testy. Nástroj test runner NUnit obsahuje vstupní bod programu ke spuštění testů. `dotnet test` Spustí nástroj test runner pomocí projektu testů jednotek, které jste vytvořili.

Test se nezdaří. Nevytvořili jste ještě implementace. Ujistěte se, tento test předat napsáním kód nejjednodušší `PrimeService` třídu, která funguje:

```csharp
public bool IsPrime(int candidate)
{
    if (candidate == 1)
    {
        return false;
    }
    throw new NotImplementedException("Please create a test first");
}
```

V *jednotky – testování pomocí nunit* spusťte `dotnet test` znovu. `dotnet test` Příkaz spustí sestavení pro `PrimeService` projektu a pak `PrimeService.Tests` projektu. Po sestavení obou projektů, spustí se tento jeden test. Pak předá.

## <a name="adding-more-features"></a>Přidání další funkce

Teď, když jste udělali jeden testovací předání, je čas zapsat informace. Existuje několik dalších jednoduchý případů pro prvočísel: 0, -1. Můžete přidat nové testování pomocí `[Test]` atribut, ale které rychle stane zdlouhavé. Existují další NUnit atributy, které vám umožní zápisu sada testů, podobně jako.  A `[TestCase]` atribut se používá k vytvoření sada testů, které provést stejný kód, ale mají jinou vstupní argumenty. Můžete použít `[TestCase]` atribut zadat hodnoty pro tyto vstupy.

Místo vytváření nové testů, Použíjte tento atribut k vytvoření testu jedné řízených daty. Řízených testovací daty je metoda, která porovná několik méně než dvě hodnoty, což je s nejnižším číslem prime:

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

Spustit `dotnet test`, a dvě z nich testy nezdaří. Chcete-li všechny testy průchodu, změnit `if` klauzule na začátku metody:

```csharp
if (candidate < 2)
```

Pokračujte k iteraci v přidáním další testy, další teorií a další kód v knihovně hlavní. Máte [dokončení verzi testy](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.cs) a [dokončení implementace knihovny](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-nunit/PrimeService/PrimeService.cs).

Když jste sestavili malé knihovny a sadu testů jednotek pro danou knihovnu. Řešení si strukturovaná, tak, aby přidání nové balíčky a testy je součástí normálním pracovním postupu. Jste soustředí většinu čas a úsilí na řešení cílů aplikace.
