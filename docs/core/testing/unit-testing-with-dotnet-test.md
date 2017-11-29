---
title: "Testování kódu C# v .NET Core pomocí testovacích dotnet a xUnit částí"
description: "Další koncepty test jednotky v C# a .NET Core prostřednictvím interaktivní prostředí sestavování podrobné ukázkové řešení pomocí testovacích dotnet a xUnit."
author: ardalis
ms.author: wiwagn
ms.date: 09/08/2017
ms.topic: article
ms.prod: .net-core
ms.openlocfilehash: 6e986e89d47ba4de9b8563f1a95cb1ae89accc89
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="unit-testing-c-in-net-core-using-dotnet-test-and-xunit"></a>Testování C# v .NET Core pomocí testovacích dotnet a xUnit částí

Tento kurz vás provede interaktivní prostředí vytváření ukázkové řešení podrobné další koncepty testování částí. Pokud chcete postupovat v kurzu pomocí předdefinovaných řešení, [zobrazení nebo stažení ukázkového kódu](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-using-dotnet-test/) před zahájením. Pokyny ke stažení najdete v tématu [ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="creating-the-source-project"></a>Vytvoření projektu zdroje

Otevřete okno prostředí. Vytvořte adresář s názvem *testování pomocí dotnet – testování* pro uložení řešení.
Uvnitř tohoto nového adresáře, spusťte [ `dotnet new sln` ](../tools/dotnet-new.md) k vytvoření nové řešení. Díky tomu je snazší správa knihovny tříd a projektu testování částí.
V adresáři řešení vytvořit *PrimeService* adresáře. Strukturu adresáře a souboru proto mnohem je zobrazena níže:

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
```

Ujistěte se, *PrimeService* aktuální adresář a spusťte [ `dotnet new classlib` ](../tools/dotnet-new.md) a vytvořte tak projekt zdroje. Přejmenování *Class1.cs* k *PrimeService.cs*. Použití vývoje řízeného testováním (TDD), vytvoříte selhání provádění `PrimeService` třídy:

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

Změnit adresář zpět do *testování pomocí dotnet – testování* adresáře. Spustit [ `dotnet sln add .\PrimeService\PrimeService.csproj` ](../tools/dotnet-sln.md) přidání projektu knihovny tříd do řešení.

## <a name="creating-the-test-project"></a>Vytvoření projektu testů

Dále vytvořte *PrimeService.Tests* adresáře. Zobrazí následující osnova adresářovou strukturu:

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

Ujistěte se, *PrimeService.Tests* adresář aktuální adresář a vytvoření nového projektu pomocí [ `dotnet new xunit` ](../tools/dotnet-new.md). Tím se vytvoří testovací projekt, který používá xUnit jako knihovně testu. Nástroj test runner v nakonfiguruje vygenerované šablony *PrimeServiceTests.csproj*:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

K testovacímu projektu vyžaduje další balíčky k vytváření a spouštění testování částí. `dotnet new`v předchozím kroku přidat xUnit a xUnit runner. Nyní přidejte `PrimeService` knihovny tříd jako další závislosti do projektu. Použití [ `dotnet add reference` ](../tools/dotnet-add-reference.md) příkaz:

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

Zobrazí celý soubor v [ukázky úložiště](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.csproj) na Githubu.

Na obrázku rozložení konečné řešení:

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.csproj
```

Spuštění [ `dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj` ](../tools/dotnet-sln.md) v *testování pomocí dotnet – testování* adresáře. 

## <a name="creating-the-first-test"></a>Vytvoření prvního testu

Volá TDD přístup pro zápis jeden selhání test, což předat a zopakováním postupu. Odebrat *UnitTest1.cs* z *PrimeService.Tests* adresáře a vytvořte nový soubor C# s s názvem *PrimeService_IsPrimeShould.cs*. Přidejte následující kód:

```csharp
using Xunit;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    public class PrimeService_IsPrimeShould
    {
        private readonly PrimeService _primeService;

        public PrimeService_IsPrimeShould()
        {
            _primeService = new PrimeService();
        }

        [Fact]
        public void ReturnFalseGivenValueOf1()
        {
            var result = _primeService.IsPrime(1);

            Assert.False(result, "1 should not be prime");
        }
    }
}
```

`[Fact]` Atribut označuje testovací metodu, která spustí nástroj test runner. Z *testování pomocí dotnet – testování*, provést [ `dotnet test` ](../tools/dotnet-test.md) vytvářet testy a knihovny tříd a poté spusťte testy. Nástroj test runner xUnit obsahuje vstupní bod programu ke spuštění testů. `dotnet test`Spustí nástroj test runner pomocí projektu testů jednotek, které jste vytvořili.

Test se nezdaří. Nevytvořili jste ještě implementace. Psaní kódu nejjednodušší v, aby tento test `PrimeService` třídu, která funguje:

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

V *testování pomocí dotnet – testování* spusťte `dotnet test` znovu. `dotnet test` Příkaz spustí sestavení pro `PrimeService` projektu a pak `PrimeService.Tests` projektu. Po sestavení obou projektů, spustí se tento jeden test. Pak předá.

## <a name="adding-more-features"></a>Přidání další funkce

Teď, když jste udělali jeden testovací předání, je čas zapsat informace. Existuje několik dalších jednoduchý případů pro prvočísel: 0, -1. Můžete přidat jako nový testování pomocí těchto případech `[Fact]` atribut, ale které rychle stane zdlouhavé. Existují další xUnit atributy, které vám umožní zápisu sada testů, podobně jako.  A `[Theory]` atribut představuje sada testů, které provést stejný kód, ale mají jinou vstupní argumenty. Můžete použít `[InlineData]` atribut zadat hodnoty pro tyto vstupy.

Místo vytváření nové testů, platí tyto dva atributy pro vytvoření jedné teoreticky. Teorie je metoda, která porovná několik hodnoty menší než dva, což je nejnižší prime číslo:

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

Spustit `dotnet test`, a dvě z nich testy nezdaří. Chcete-li všechny testy průchodu, změnit `if` klauzule na začátku metody:

```csharp
if (candidate < 2)
```

Pokračujte k iteraci v přidáním další testy, další teorií a další kód v knihovně hlavní. Máte [dokončení verzi testy](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) a [dokončení implementace knihovny](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).

### <a name="additional-resources"></a>Další zdroje

[Testování řadiče logiku v ASP.NET Core](https://docs.microsoft.com/aspnet/core/mvc/controllers/testing)
