---
title: Testování jednotek jazyka Visual Basic v rozhraní .NET Core pomocí příkazu dotnet test a NUnit
description: Další koncepty testů jednotek v .NET Core prostřednictvím vytváření ukázkové řešení jazyka Visual Basic podrobné interaktivní prostředí pomocí NUnit.
author: rprouse
ms.date: 10/04/2018
dev_langs:
- vb
ms.openlocfilehash: bed43ac6b6f918b1ee45715101f9142c1add777f
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/06/2018
ms.locfileid: "48836904"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-nunit"></a>Testování pomocí příkazu dotnet test a NUnit knihovny jazyka Visual Basic .NET Core

Tento kurz vás provede interaktivní prostředí pro sestavování ukázkové řešení podrobné další testování konceptů. Pokud chcete postupovat podle kurzu pomocí předem připravených řešení [zobrazení nebo stažení ukázkového kódu](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-nunit/) předtím, než začnete. Pokyny ke stažení najdete v tématu [ukázek a kurzů](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="prerequisites"></a>Požadavky 
- [.NET core SDK 2.1 (vs. 2.1.400)](https://www.microsoft.com/net/download) nebo novější verze. 
- Textového editoru nebo editoru kódu podle vašeho výběru.

## <a name="creating-the-source-project"></a>Vytvoření projektu zdroje

Otevřete okno prostředí. Vytvořte adresář s názvem *jednotky – testování – vb-nunit* pro uložení řešení. Uvnitř tohoto nového adresáře spuštěním následujícího příkazu vytvořte nový soubor řešení pro knihovny tříd a testovacího projektu:

```console
dotnet new sln
```

Dále vytvořte *PrimeService* adresáře. Následující osnovy zatím znázorňuje strukturu souboru:

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
```

Ujistěte se, *PrimeService* aktuální adresář a spusťte následující příkaz k vytvoření zdrojového projektu:

```console
dotnet new classlib -lang VB
```

Přejmenovat *Class1.VB* k *PrimeService.VB*. Chcete-li použít vývoj řízený testováním (TDD), vytvoříte selhání provádění `PrimeService` třídy:

```vb
Imports System

Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first")
        End Function
    End Class
End Namespace
```

Vraťte do adresáře *jednotky – testování – vb použití stest* adresáře. Spusťte následující příkaz pro přidání do řešení projekt knihovny tříd:

```console
dotnet sln add .\PrimeService\PrimeService.vbproj
```

## <a name="creating-the-test-project"></a>Vytvoření testovacího projektu

Dále vytvořte *PrimeService.Tests* adresáře. Zobrazí následující osnova adresářovou strukturu:

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

Ujistěte se, *PrimeService.Tests* adresář aktuálního adresáře a vytvořte nový projekt pomocí následujícího příkazu:

```console
dotnet new nunit -lang VB
```

[Dotnet nové](../tools/dotnet-new.md) příkaz vytvoří testovací projekt, který používá NUnit jako knihovna testu. Nakonfiguruje nástroj test runner v vygenerovanou šablonu *PrimeServiceTests.vbproj* souboru:

[!code-xml[Packages](~/samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj#Packages)]

Projekt testů vyžaduje další balíčky pro vytváření a spouštění testování částí. `dotnet new` v předchozím kroku přidat že nunit a NUnit testovací adaptér. Teď přidejte `PrimeService` knihovny tříd jako další závislost do projektu. Použití [ `dotnet add reference` ](../tools/dotnet-add-reference.md) příkaz:

```console
dotnet add reference ../PrimeService/PrimeService.vbproj
```

Zobrazí celý soubor v [úložiště ukázek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) na Githubu.

Máte následující rozložení konečné řešení:

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeService.Tests.vbproj
```

Spusťte následující příkaz v *jednotky – testování – vb-nunit* adresáře:

```console
dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj
```

## <a name="creating-the-first-test"></a>Vytvoření prvního testu

Volá TDD přístup pro zápis jednoho selhává testování, takže předat a potom zopakováním postupu. V *PrimeService.Tests* adresáře, přejmenovat *UnitTest1.vb* do souboru *PrimeService_IsPrimeShould.VB* a jeho celý obsah nahraďte následujícím kódem:

```vb
Imports NUnit.Framework

Namespace PrimeService.Tests
    <TestFixture>
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <Test>
        Sub ReturnFalseGivenValueOf1()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

`<TestFixture>` Atribut určuje třídu, která obsahuje testy. `<Test>` Atribut označuje metodu, která se spouští pomocí nástroje test runner. Z *jednotky – testování – vb-nunit*, spusťte [ `dotnet test` ](../tools/dotnet-test.md) pro sestavení, testy a knihovny tříd a následné spuštění testů. Nástroj test runner NUnit obsahuje vstupní bod programu pro spouštění vašich testů. `dotnet test` Spustí nástroj test runner pomocí projektu testování částí, kterou jste vytvořili.

Test se nezdaří. Nevytvořili jste ještě implementace. Tento test provést napsáním kódu nejjednodušší v `PrimeService` třídu, která funguje:

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first")
End Function
```

V *jednotky – testování – vb-nunit* adresáře, spusťte `dotnet test` znovu. `dotnet test` Sestavení pro spuštění příkazu `PrimeService` projekt a potom `PrimeService.Tests` projektu. Po vytvoření oba projekty, poběží tento jeden test. Předá.

## <a name="adding-more-features"></a>Přidání další funkce

Teď, když jste provedli, předejte jeden test, je čas zápisu informace. Existuje několik dalších jednoduché případů pro prvočísel: 0, -1. Tyto případy můžete přidat jako nové testy s `<Test>` atribut, ale rychle stane únavné. Existují jiné atributy xUnit, které umožňují také napsat sady podobné testování.  A `<TestCase>` atribut představuje sadu testů, které spuštění stejný kód, ale mají různé vstupní argumenty. Můžete použít `<TestCase>` atribut můžete zadat hodnoty pro tyto vstupy.

Místo vytváření nové testy, platí tyto dva atributy k vytvoření série testů, které testují několik hodnot, které jsou kratší než dvě, což je nejnižší číslo prime:

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

Spustit `dotnet test`, a dvě z nich selhání testů. Pokud chcete, aby všechny průchodu testů, změňte `if` klauzule na začátku `Main` metoda ve *PrimeServices.cs* souboru:

```vb
if candidate < 2
```

Pokračujte k iteraci tak, že přidáte další testy, další teorií a další kód v hlavní knihovny. Máte [hotovou verzi testy](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) a [úplnou implementaci knihovny](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb).

Začlenění malé knihovny a sadu testů jednotek pro knihovny. Řešení jsme strukturovaná, takže přidání nové balíčky a testů je součástí normálního pracovního postupu. Jste koncentrované většinu času a úsilí na řešení cíle aplikace.
