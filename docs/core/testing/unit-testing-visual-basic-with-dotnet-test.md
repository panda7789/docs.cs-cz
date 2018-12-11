---
title: Testování částí pomocí jazyka Visual Basic v rozhraní .NET Core pomocí příkazu dotnet test a xUnit
description: Další koncepty testů jednotek v .NET Core prostřednictvím vytváření ukázkové řešení jazyka Visual Basic podrobné interaktivní prostředí pomocí příkazu dotnet test a xUnit.
author: billwagner
ms.author: wiwagn
ms.date: 09/01/2017
dev_langs:
- vb
ms.custom: seodec18
ms.openlocfilehash: eae5f0727d2d75044c072e8cc1d9a1c6faf53a9a
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170532"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-xunit"></a>Testování knihovny jazyka Visual Basic .NET Core pomocí příkazu dotnet test a xUnit

Tento kurz vás provede interaktivní prostředí pro sestavování ukázkové řešení podrobné další testování konceptů. Pokud chcete postupovat podle kurzu pomocí předem připravených řešení [zobrazení nebo stažení ukázkového kódu](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-dotnet-test) předtím, než začnete. Pokyny ke stažení najdete v tématu [ukázek a kurzů](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="creating-the-source-project"></a>Vytvoření projektu zdroje

Otevřete okno prostředí. Vytvořte adresář s názvem *unit-testing-vb-using-dotnet-test* pro uložení řešení.
Uvnitř tohoto nového adresáře, spusťte [ `dotnet new sln` ](../tools/dotnet-new.md) k vytvoření nového řešení. Tento postup usnadňuje správu knihovny tříd a projekt testu jednotek.
V adresáři řešení, vytvářet *PrimeService* adresáře. Jaký máte následující strukturu adresáře a souboru:

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
```

Ujistěte se, *PrimeService* aktuální adresář a spusťte [ `dotnet new classlib -lang VB` ](../tools/dotnet-new.md) vytvoření zdrojového projektu. Přejmenovat *Class1.VB* k *PrimeService.VB*. Chcete-li použít vývoj řízený testováním (TDD), vytvoříte selhání provádění `PrimeService` třídy:

```vb
Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first")
        End Function
    End Class
End Namespace
```

Vraťte do adresáře *unit-testing-vb-using-dotnet-test* adresáře. Spustit [ `dotnet sln add .\PrimeService\PrimeService.vbproj` ](../tools/dotnet-sln.md) přidat do řešení projekt knihovny tříd.

## <a name="creating-the-test-project"></a>Vytvoření testovacího projektu

Dále vytvořte *PrimeService.Tests* adresáře. Zobrazí následující osnova adresářovou strukturu:

```
/unit-testing-vb-using-dotnet-test
    unit-testing-vb-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

Ujistěte se, *PrimeService.Tests* adresář aktuálního adresáře a vytvořte nový projekt pomocí [ `dotnet new xunit -lang VB` ](../tools/dotnet-new.md). Tento příkaz vytvoří testovací projekt, který používá xUnit jako knihovna testu. Nakonfiguruje nástroj test runner v vygenerovanou šablonu *PrimeServiceTests.vbproj*:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

Projekt testů vyžaduje další balíčky pro vytváření a spouštění testování částí. `dotnet new` v předchozím kroku přidat xUnit a xUnit runner. Teď přidejte `PrimeService` knihovny tříd jako další závislost do projektu. Použití [ `dotnet add reference` ](../tools/dotnet-add-reference.md) příkaz:

```
dotnet add reference ../PrimeService/PrimeService.vbproj
```

Zobrazí celý soubor v [úložiště ukázek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService.Tests.vbproj) na Githubu.

Máte následující poslední složky rozložení:

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.vbproj
```

Spustit [ `dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj` ](../tools/dotnet-sln.md) v *unit-testing-vb-using-dotnet-test* adresáře. 

## <a name="creating-the-first-test"></a>Vytvoření prvního testu

Volá TDD přístup pro zápis jednoho selhává testování, takže předat a potom zopakováním postupu. Odebrat *UnitTest1.vb* z *PrimeService.Tests* adresáře a vytvořte nový soubor jazyka Visual Basic s názvem *PrimeService_IsPrimeShould.VB*. Přidejte následující kód:

```vb
Imports Xunit

Namespace PrimeService.Tests
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <Fact>
        Sub ReturnFalseGivenValueOf1()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

`<Fact>` Označuje atribut testovací metody, která se spouští pomocí nástroje test runner. Z *testování použití dotnet testování částí*, spusťte [ `dotnet test` ](../tools/dotnet-test.md) pro sestavení, testy a knihovny tříd a následné spuštění testů. Nástroj test runner xUnit obsahuje vstupní bod programu pro spouštění vašich testů. `dotnet test` Spustí nástroj test runner pomocí projektu testování částí, kterou jste vytvořili.

Test se nezdaří. Nevytvořili jste ještě implementace. Tento test provést napsáním kódu nejjednodušší v `PrimeService` třídu, která funguje:

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first")
End Function
```

V *unit-testing-vb-using-dotnet-test* adresáře, spusťte `dotnet test` znovu. `dotnet test` Sestavení pro spuštění příkazu `PrimeService` projekt a potom `PrimeService.Tests` projektu. Po vytvoření oba projekty, poběží tento jeden test. Předá.

## <a name="adding-more-features"></a>Přidání další funkce

Teď, když jste provedli, předejte jeden test, je čas zápisu informace. Existuje několik dalších jednoduché případů pro prvočísel: 0, -1. Tyto případy můžete přidat jako nové testy s `<Fact>` atribut, ale rychle stane únavné. Existují jiné atributy xUnit, které umožňují také napsat sady podobné testování.  A `<Theory>` atribut představuje sadu testů, které spuštění stejný kód, ale mají různé vstupní argumenty. Můžete použít `<InlineData>` atribut můžete zadat hodnoty pro tyto vstupy.

Místo vytváření nové testy, platí tyto dva atributy k vytvoření jedné teorií. Teorie je metoda, která porovná několik méně než dvě hodnoty, což je nejnižší číslo prime:

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

Spustit `dotnet test`, a dvě z nich selhání testů. Chcete-li všechny průchodu testů, změňte `if` klauzule na začátku metody:

```vb
if candidate < 2
```

Pokračujte k iteraci tak, že přidáte další testy, další teorií a další kód v hlavní knihovny. Máte [hotovou verzi testy](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb) a [úplnou implementaci knihovny](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService/PrimeService.vb).

Začlenění malé knihovny a sadu testů jednotek pro knihovny. Řešení jsme strukturovaná, takže přidání nové balíčky a testů je součástí normálního pracovního postupu. Jste koncentrované většinu času a úsilí na řešení cíle aplikace.
