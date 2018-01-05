---
title: "V jazyce Visual Basic v .NET Core pomocí testovacích dotnet a xUnit testování částí"
description: "Další koncepty test jednotky v .NET Core prostřednictvím interaktivní prostředí vytváření ukázkové řešení Visual Basic podrobné pomocí testovacích dotnet a xUnit."
author: billwagner
ms.author: wiwagn
ms.date: 09/01/2017
ms.topic: article
dev_langs: vb
ms.prod: .net-core
ms.workload: dotnetcore
ms.openlocfilehash: 01922e3ad3b19e13ebea755decf21c6b09e4be37
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-xunit"></a>Knihovny jazyka Visual Basic .NET Core pomocí testovacích dotnet a xUnit testování částí

Tento kurz vás provede interaktivní prostředí vytváření ukázkové řešení podrobné další koncepty testování částí. Pokud chcete postupovat v kurzu pomocí předdefinovaných řešení, [zobrazení nebo stažení ukázkového kódu](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/unit-testing-using-dotnet-test/) před zahájením. Pokyny ke stažení najdete v tématu [ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="creating-the-source-project"></a>Vytvoření projektu zdroje

Otevřete okno prostředí. Vytvořte adresář s názvem *unit-testing-vb-using-dotnet-test* pro uložení řešení.
Uvnitř tohoto nového adresáře, spusťte [ `dotnet new sln` ](../tools/dotnet-new.md) k vytvoření nové řešení. Tento postup je snazší správa knihovny tříd a projektu testování částí.
V adresáři řešení vytvořit *PrimeService* adresáře. Proto pokud máte následující strukturu adresáře a souboru:

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
```

Ujistěte se, *PrimeService* aktuální adresář a spusťte [ `dotnet new classlib -lang VB` ](../tools/dotnet-new.md) a vytvořte tak projekt zdroje. Přejmenování *Class1.VB* k *PrimeService.VB*. Použití vývoje řízeného testováním (TDD), vytvořte na selhání implementace `PrimeService` třídy:

```vb
Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first")
        End Function
    End Class
End Namespace
```

Změna adresáře zpět do *unit-testing-vb-using-dotnet-test* adresáře. Spustit [ `dotnet sln add .\PrimeService\PrimeService.vbproj` ](../tools/dotnet-sln.md) přidání projektu knihovny tříd do řešení.

## <a name="creating-the-test-project"></a>Vytvoření projektu testů

Dále vytvořte *PrimeService.Tests* adresáře. Zobrazí následující osnova adresářovou strukturu:

```
/unit-testing-vb-using-dotnet-test
    unit-testing-vb-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

Ujistěte se, *PrimeService.Tests* adresář aktuální adresář a vytvoření nového projektu pomocí [ `dotnet new xunit -lang VB` ](../tools/dotnet-new.md). Tento příkaz vytvoří testovací projekt, který používá xUnit jako knihovně testu. Nástroj test runner v nakonfiguruje vygenerované šablony *PrimeServiceTests.vbproj*:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

K testovacímu projektu vyžaduje další balíčky k vytváření a spouštění testování částí. `dotnet new`v předchozím kroku přidat xUnit a xUnit runner. Nyní přidejte `PrimeService` knihovny tříd jako další závislosti do projektu. Použití [ `dotnet add reference` ](../tools/dotnet-add-reference.md) příkaz:

```
dotnet add reference ../PrimeService/PrimeService.vbproj
```

Zobrazí celý soubor v [ukázky úložiště](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-vb-using-dotnet-test/PrimeService.Tests/PrimeService.Tests.vbproj) na Githubu.

Máte následující rozložení poslední složky:

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

Spuštění [ `dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj` ](../tools/dotnet-sln.md) v *unit-testing-vb-using-dotnet-test* adresáře. 

## <a name="creating-the-first-test"></a>Vytvoření prvního testu

Volá TDD přístup pro zápis jeden selhání test, což předat a zopakováním postupu. Odebrat *UnitTest1.vb* z *PrimeService.Tests* adresáře a vytvořte nový soubor jazyka Visual Basic s názvem *PrimeService_IsPrimeShould.VB*. Přidejte následující kód:

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

`<Fact>` Atribut označuje testovací metodu, která spustí nástroj test runner. Z *testování pomocí dotnet – testování*, provést [ `dotnet test` ](../tools/dotnet-test.md) vytvářet testy a knihovny tříd a poté spusťte testy. Nástroj test runner xUnit obsahuje vstupní bod programu ke spuštění testů. `dotnet test`Spustí nástroj test runner pomocí projektu testů jednotek, které jste vytvořili.

Test se nezdaří. Nevytvořili jste ještě implementace. Psaní kódu nejjednodušší v, aby tento test `PrimeService` třídu, která funguje:

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first")
End Function
```

V *unit-testing-vb-using-dotnet-test* spusťte `dotnet test` znovu. `dotnet test` Příkaz spustí sestavení pro `PrimeService` projektu a pak `PrimeService.Tests` projektu. Po sestavení obou projektů, spustí se tento jeden test. Pak předá.

## <a name="adding-more-features"></a>Přidání další funkce

Teď, když jste udělali jeden testovací předání, je čas zapsat informace. Existuje několik dalších jednoduchý případů pro prvočísel: 0, -1. Můžete přidat jako nový testování pomocí těchto případech `<Fact>` atribut, ale které rychle stane zdlouhavé. Existují další xUnit atributy, které vám umožní zápisu sada testů, podobně jako.  A `<Theory>` atribut představuje sada testů, které provést stejný kód, ale mají jinou vstupní argumenty. Můžete použít `<InlineData>` atribut zadat hodnoty pro tyto vstupy.

Místo vytváření nové testů, platí tyto dva atributy pro vytvoření jedné teoreticky. Teorie je metoda, která porovná několik hodnoty menší než dva, což je nejnižší prime číslo:

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

Spustit `dotnet test`, a dvě z nich testy nezdaří. Chcete-li všechny testy průchodu, změnit `if` klauzule na začátku metody:

```vb
if candidate < 2
```

Pokračujte k iteraci v přidáním další testy, další teorií a další kód v knihovně hlavní. Máte [dokončení verzi testy](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-vb-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb) a [dokončení implementace knihovny](https://github.com/dotnet/docs/blob/master/samples/core/getting-started/unit-testing-vb-using-dotnet-test/PrimeService/PrimeService.vb).

Když jste sestavili malé knihovny a sadu testů jednotek pro danou knihovnu. Řešení si strukturovaná, tak, aby přidání nové balíčky a testy je součástí normálním pracovním postupu. Jste soustředí většinu čas a úsilí na řešení cílů aplikace.
