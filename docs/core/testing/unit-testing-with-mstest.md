---
title: Testování částí C# s MSTest a .NET Core
description: Naučte koncepty testování částí v C# a .NET Core prostřednictvím interaktivního prostředí, které buduje ukázkové řešení krok za krokem pomocí dotnet test a MSTest.
author: ncarandini
ms.author: wiwagn
ms.date: 09/08/2017
ms.openlocfilehash: bd7891243d84277a7578089f8b4629ff5bada577
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240906"
---
# <a name="unit-testing-c-with-mstest-and-net-core"></a>Testování částí C# s MSTest a .NET Core

Tento kurz vás provede interaktivní prostředí vytváření ukázkové řešení krok za krokem se dozvíte koncepty testování částí. Pokud dáváte přednost postupujte podle kurzu pomocí předem sestaveného řešení, [zobrazte nebo stáhněte ukázkový kód,](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/) než začnete. Pokyny ke stažení naleznete v [tématu Ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="create-the-source-project"></a>Vytvoření zdrojového projektu

Otevřete okno prostředí. Vytvořte adresář s názvem *unit-testing-using-mstest* pro uložení řešení. V tomto novém [`dotnet new sln`](../tools/dotnet-new.md) adresáři spusťte a vytvořte nový soubor řešení pro knihovnu tříd a testovací projekt. Dále vytvořte adresář *PrimeService.* Následující osnova ukazuje adresář a strukturu souborů tak daleko:

```console
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
```

Vytvořte *PrimeService* aktuální [`dotnet new classlib`](../tools/dotnet-new.md) adresář a spustit k vytvoření zdrojového projektu. Přejmenujte *Class1.cs* na *PrimeService.cs*. Můžete vytvořit selhání implementace `PrimeService` třídy:

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

Změňte adresář zpět do adresáře *unit-testing-using-mstest.* Spuštěním [`dotnet sln add PrimeService/PrimeService.csproj`](../tools/dotnet-sln.md) přidáte projekt knihovny tříd do řešení.

## <a name="create-the-test-project"></a>Vytvoření testovacího projektu

Dále vytvořte adresář *PrimeService.Tests.* Následující osnova ukazuje adresářovou strukturu:

```console
/unit-testing-using-mstest
    unit-testing-using-mstest.sln
    /PrimeService
        Source Files
        PrimeService.csproj
    /PrimeService.Tests
```

Vytvořte adresář *PrimeService.Tests* jako aktuální adresář [`dotnet new mstest`](../tools/dotnet-new.md)a vytvořte nový projekt pomocí aplikace . Dotnet new příkaz vytvoří testovací projekt, který používá MSTest jako testovací knihovny. Vygenerovaná šablona konfiguruje testovacího běžce v souboru *PrimeServiceTests.csproj:*

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

Testovací projekt vyžaduje další balíčky k vytvoření a spuštění testů částí. `dotnet new`v předchozím kroku přidánm MSTest SDK, MSTest testovací rámec a mstest runner. Nyní přidejte `PrimeService` knihovnu tříd jako jinou závislost do projektu. Použijte [`dotnet add reference`](../tools/dotnet-add-reference.md) příkaz:

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.csproj
```

Celý soubor můžete vidět v [úložišti ukázek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService.Tests.csproj) na GitHubu.

Následující osnova ukazuje konečné rozložení řešení:

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

Spusťte [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.csproj`](../tools/dotnet-sln.md) v adresáři *unit-testing-using-mstest.*

## <a name="create-the-first-test"></a>Vytvoření prvního testu

Napíšete jeden neúspěšný test, provedete jeho předání a pak zopakujete proces. Odeberte *UnitTest1.cs* z adresáře *PrimeService.Tests* a vytvořte nový soubor Jazyka C# s názvem *PrimeService_IsPrimeShould.cs* s následujícím obsahem:

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

TestClass [atribut](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) označuje třídu, která obsahuje testy částí. Atribut [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) označuje, že metoda je zkušební metoda.

Uložte tento [`dotnet test`](../tools/dotnet-test.md) soubor a spusťte k sestavení testů a knihovny tříd a pak spusťte testy. Testovací běžec MSTest obsahuje vstupní bod programu pro spuštění testů. `dotnet test`spustí testovací houska pomocí projektu testování částí, který jste vytvořili.

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

V adresáři *testování jednotky using-mstest* spusťte `dotnet test` znovu. Příkaz `dotnet test` spustí sestavení pro `PrimeService` projekt a `PrimeService.Tests` potom pro projekt. Po sestavení obou projektů spustí tento jediný test. Už to přejde.

## <a name="add-more-features"></a>Přidání dalších funkcí

Nyní, když jste provedli jeden test projít, je čas napsat více. Existuje několik dalších jednoduchých případů pro prvočísla: 0, -1. Můžete přidat nové testy s [TestMethod atribut](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute), ale to se rychle stane únavné. Existují další atributy MSTest, které umožňují napsat sadu podobných testů.  A [DataTestMethod atribut](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataTestMethodAttribute) představuje sadu testů, které spouštějí stejný kód, ale mají různé vstupní argumenty. [Atribut DataRow](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataRowAttribute) můžete použít k určení hodnot pro tyto vstupy.

Namísto vytváření nových testů použijte tyto dva atributy k vytvoření jednoho testu řízeného daty. Test řízený daty je metoda, která testuje několik hodnot menší než dvě, což je nejnižší prvočíslo:

[!code-csharp[Sample_TestCode](../../../samples/snippets/core/testing/unit-testing-using-mstest/csharp/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

Spustit `dotnet test`a dva z těchto testů nezdaří. Chcete-li provést všechny testy `if` projít, změňte klauzuli na začátku metody:

```csharp
if (candidate < 2)
```

Pokračujte v iterátu přidáním dalších testů, dalších teorií a dalšího kódu v hlavní knihovně. Máte [hotovou verzi testů](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.cs) a [kompletní implementaci knihovny](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-mstest/PrimeService/PrimeService.cs).

Vytvořili jste malou knihovnu a sadu testů částí pro tuto knihovnu. Strukturovali jste řešení tak, aby přidání nových balíčků a testů bylo součástí normálního pracovního postupu. Soustředili jste většinu svého času a úsilí na řešení cílů aplikace.

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting>
- [Použití architektury MSTest v jednotkových testech](/visualstudio/test/using-microsoft-visualstudio-testtools-unittesting-members-in-unit-tests)
- [Dokumenty testovacího rámce MSTest V2](https://github.com/Microsoft/testfx-docs)
