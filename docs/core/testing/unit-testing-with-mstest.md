---
title: Testování C# s MSTest a .NET Core
description: Další koncepty testů jednotek v C# a .NET Core prostřednictvím interaktivního prostředí sestavení krok za krokem ukázkové řešení pomocí příkazu dotnet test a MSTest.
author: ncarandini
ms.author: wiwagn
ms.date: 09/08/2017
ms.openlocfilehash: efeb12eb43539b0a85168b1162e0f8b94ad67e90
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2018
ms.locfileid: "43257419"
---
# <a name="unit-testing-c-with-mstest-and-net-core"></a>Testování C# s MSTest a .NET Core

Tento kurz vás provede interaktivní prostředí pro sestavování ukázkové řešení podrobné další testování konceptů. Pokud chcete postupovat podle kurzu pomocí předem připravených řešení [zobrazení nebo stažení ukázkového kódu](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/) předtím, než začnete. Pokyny ke stažení najdete v tématu [ukázek a kurzů](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

### <a name="creating-the-source-project"></a>Vytvoření projektu zdroje

Otevřete okno prostředí. Vytvořte adresář s názvem *jednotky – testování použití mstest* pro uložení řešení. Uvnitř tohoto nového adresáře, spusťte [ `dotnet new sln` ](../tools/dotnet-new.md) vytvořte nový soubor řešení pro knihovny tříd a testovací projekt. Dále vytvořte *PrimeService* adresáře. Následující osnovy doposud znázorňuje strukturu adresáře a souboru:

```
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
```

Ujistěte se, *PrimeService* aktuální adresář a spusťte [ `dotnet new classlib` ](../tools/dotnet-new.md) vytvoření zdrojového projektu. Přejmenovat *Class1.cs* k *PrimeService.cs*. Chcete-li použít vývoj řízený testováním (TDD), vytvoříte selhání provádění `PrimeService` třídy:

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

Vraťte do adresáře *jednotky – testování použití mstest* adresáře. Spustit [ `dotnet sln add PrimeService/PrimeService.csproj` ](../tools/dotnet-sln.md) přidat do řešení projekt knihovny tříd. 

### <a name="creating-the-test-project"></a>Vytvoření testovacího projektu

Dále vytvořte *PrimeService.Tests* adresáře. Zobrazí následující osnova adresářovou strukturu:

```
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

Ujistěte se, *PrimeService.Tests* adresář aktuálního adresáře a vytvořte nový projekt pomocí [ `dotnet new mstest` ](../tools/dotnet-new.md). Nový příkaz dotnet vytvoří projekt testů, který používá MStest jako knihovna testu. Nakonfiguruje nástroj test runner v vygenerovanou šablonu *PrimeServiceTests.csproj* souboru:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

Projekt testů vyžaduje další balíčky pro vytváření a spouštění testování částí. `dotnet new` v předchozím kroku přidat testovací sady SDK MSTest, MSTest rozhraní framework a MSTest runner. Teď přidejte `PrimeService` knihovny tříd jako další závislost do projektu. Použití [ `dotnet add reference` ](../tools/dotnet-add-reference.md) příkaz:

```
dotnet add reference ../PrimeService/PrimeService.csproj
```

Zobrazí celý soubor v [úložiště ukázek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj) na Githubu.

Následující osnovy ukazuje rozložení konečné řešení:

```
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.csproj
```

Spustit [ `dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj` ](../tools/dotnet-sln.md) v *testování použití dotnet testování částí* adresáře. 

## <a name="creating-the-first-test"></a>Vytvoření prvního testu

Volá TDD přístup pro zápis jednoho selhává testování, takže předat a potom zopakováním postupu. Odebrat *UnitTest1.cs* z *PrimeService.Tests* adresář a vytvořit nový soubor jazyka C# s názvem *PrimeService_IsPrimeShould.cs* s následujícím obsahem:

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
        public void ReturnFalseGivenValueOf1()
        {
            var result = _primeService.IsPrime(1);

            Assert.IsFalse(result, "1 should not be prime");
        }
    }
}
```

`[TestClass]` Atribut označuje třídu, která obsahuje testy jednotek. `[TestMethod]` Atribut označuje, že metoda je testovací metodu. 

Tento soubor uložte a spusťte [ `dotnet test` ](../tools/dotnet-test.md) pro sestavení, testy a knihovny tříd a následné spuštění testů. Nástroj test runner MSTest obsahuje vstupní bod programu pro spouštění vašich testů. `dotnet test` Spustí nástroj test runner pomocí projektu testování částí, kterou jste vytvořili.

Test se nezdaří. Nevytvořili jste ještě implementace. Ujistěte se, tento test předat napsáním kódu nejjednodušší v `PrimeService` třídu, která funguje:

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

V *jednotky – testování použití mstest* adresáře, spusťte `dotnet test` znovu. `dotnet test` Sestavení pro spuštění příkazu `PrimeService` projekt a potom `PrimeService.Tests` projektu. Po vytvoření oba projekty, poběží tento jeden test. Předá.

## <a name="adding-more-features"></a>Přidání další funkce

Teď, když jste provedli, předejte jeden test, je čas zápisu informace. Existuje několik dalších jednoduché případů pro prvočísel: 0, -1. Můžete přidat nové testy s `[TestMethod]` atribut, ale rychle stane únavné. Existují jiné atributy MSTest, které umožňují také napsat sady podobné testování.  A `[DataTestMethod]`atribut představuje sadu testů, které spuštění stejný kód, ale mají různé vstupní argumenty. Můžete použít `[DataRow]` atribut můžete zadat hodnoty pro tyto vstupy.

Místo vytváření nové testy, platí tyto dva atributy pro vytvoření testu jedné řízené daty. Test na základě dat je metoda, která porovná několik méně než dvě hodnoty, což je nejnižší číslo prime:

[!code-csharp[Sample_TestCode](../../../samples/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

Spustit `dotnet test`, a dvě z nich selhání testů. Chcete-li všechny průchodu testů, změňte `if` klauzule na začátku metody:

```csharp
if (candidate < 2)
```

Pokračujte k iteraci tak, že přidáte další testy, další teorií a další kód v hlavní knihovny. Máte [hotovou verzi testy](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs) a [úplnou implementaci knihovny](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs).

Začlenění malé knihovny a sadu testů jednotek pro knihovny. Řešení jsme strukturovaná, takže přidání nové balíčky a testů je součástí normálního pracovního postupu. Jste koncentrované většinu času a úsilí na řešení cíle aplikace.
