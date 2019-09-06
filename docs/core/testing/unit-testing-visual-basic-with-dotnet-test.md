---
title: Testování částí Visual Basic v .NET Core pomocí příkazu dotnet test a xUnit
description: Seznamte se s koncepty testování částí v .NET Core pomocí interaktivního prostředí, které vytváří ukázkové Visual Basic řešení, pomocí příkazu dotnet test a xUnit.
author: billwagner
ms.author: wiwagn
ms.date: 09/01/2017
ms.custom: seodec18
ms.openlocfilehash: 63898f23f7c70a96409c6de9029fb0c067223016
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2019
ms.locfileid: "70373881"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-xunit"></a>Testování částí Visual Basic knihoven .NET Core pomocí příkazu dotnet test a xUnit

Tento kurz vás provede interaktivním vytvořením ukázkového řešení, které vás seznámí s koncepty testování částí. Pokud chcete postupovat podle kurzu s předdefinovaným řešením, zobrazte si [ukázkový kód](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-dotnet-test) před jeho zahájením nebo si ho stáhněte. Pokyny ke stažení najdete v tématu [ukázky a kurzy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="creating-the-source-project"></a>Vytvoření zdrojového projektu

Otevřete okno prostředí. Vytvořte adresář s názvem *Unit-Testing-VB-using-dotnet-test* pro uložení řešení.
V tomto novém adresáři spusťte příkaz [`dotnet new sln`](../tools/dotnet-new.md) a vytvořte nové řešení. Tento postup usnadňuje správu knihovny tříd i projektu testu jednotek.
V adresáři řešení vytvořte adresář *PrimeService* . Máte zatím následující strukturu adresářů a souborů:

```console
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
```

Vytvořte *PrimeService* aktuální adresář a spusťte příkaz [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) k vytvoření zdrojového projektu. Přejmenujte *Class1. vb* na *PrimeService. vb*. Vytvoříte selhání implementace `PrimeService` třídy:

```vb
Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first")
        End Function
    End Class
End Namespace
```

Změňte adresář zpátky na *test Unit-Test-VB-using-dotnet-test* Directory. Spusťte [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) , chcete-li přidat projekt knihovny tříd do řešení.

## <a name="creating-the-test-project"></a>Vytváření testovacího projektu

Dále vytvořte adresář *PrimeService. Tests* . Následující osnova znázorňuje adresářovou strukturu:

```console
/unit-testing-vb-using-dotnet-test
    unit-testing-vb-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

Nastavte adresář *PrimeService. Tests* na aktuální adresář a vytvořte nový projekt pomocí [`dotnet new xunit -lang VB`](../tools/dotnet-new.md). Tento příkaz vytvoří testovací projekt, který jako knihovnu testů používá xUnit. Vygenerovaná šablona konfiguruje Test Runner v *PrimeServiceTests. vbproj*:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.3.0-preview-20170628-02" />
  <PackageReference Include="xunit" Version="2.2.0" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0" />
</ItemGroup>
```

Testovací projekt vyžaduje pro vytvoření a spuštění testů jednotek další balíčky. `dotnet new`v předchozím kroku jsme přidali xUnit a xUnit Runner. Nyní přidejte `PrimeService` knihovnu tříd jako jinou závislost do projektu. [`dotnet add reference`](../tools/dotnet-add-reference.md) Použijte příkaz:

```console
dotnet add reference ../PrimeService/PrimeService.vbproj
```

Celý soubor můžete zobrazit v [úložišti ukázek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService.Tests.vbproj) na GitHubu.

Máte následující konečné rozložení složky:

```console
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.vbproj
```

Spusťte [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) v adresáři *Unit-Testing-VB-using-dotnet-test* . 

## <a name="creating-the-first-test"></a>Vytvoření prvního testu

Napíšete jeden neúspěšný test, udělejte ho a pak proces opakujte. Z adresáře *PrimeService. Tests* odeberte *UnitTest1. vb* a vytvořte nový soubor Visual Basic s názvem *PrimeService_IsPrimeShould. vb*. Přidejte následující kód:

```vb
Imports Xunit

Namespace PrimeService.Tests
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <Fact>
        Sub IsPrime_InputIs1_ReturnFalse()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

`<Fact>` Atribut označuje testovací metodu, která je spuštěna nástrojem Test Runner. Z rutiny *testování částí-using-dotnet-test*spusťte [`dotnet test`](../tools/dotnet-test.md) sestavení testů a knihovny tříd a poté spusťte testy. XUnit Test Runner obsahuje vstupní bod programu pro spuštění testů. `dotnet test`spustí Test Runner pomocí projektu testování částí, který jste vytvořili.

Test se nezdařil. Ještě jste nevytvořili implementaci. Proveďte tento test průchodu vytvořením nejjednoduššího kódu `PrimeService` ve třídě, která funguje:

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first.")
End Function
```

V adresáři *testování částí-VB-using-dotnet-test* spusťte `dotnet test` znovu. Příkaz spustí sestavení `PrimeService` pro`PrimeService.Tests` projekt a potom pro projekt. `dotnet test` Po sestavení obou projektů spustí tento jediný test. Předá.

## <a name="adding-more-features"></a>Přidání dalších funkcí

Teď, když jste udělali jeden test Pass, je čas zapsat další. Pro čísla apostrofů existuje několik dalších jednoduchých případů: 0, -1. Tyto případy můžete přidat jako nové testy s `<Fact>` atributem, ale to se rychle bude zdlouhavé. Existují další atributy xUnit, které umožňují napsat sadu podobných testů.  `<Theory>` Atribut představuje sadu testů, které spouštějí stejný kód, ale mají různé vstupní argumenty. `<InlineData>` Atribut můžete použít k zadání hodnot pro tyto vstupy.

Místo vytváření nových testů použijte tyto dva atributy pro vytvoření jedné teorie. Teoretická je metoda, která testuje několik hodnot menší než dvě, což je nejnižší číslo základny:

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

Spuštění `dotnet test`a dva z těchto testů selžou. Chcete-li provést všechny testy Pass, změňte `if` klauzuli na začátku metody:

```vb
if candidate < 2
```

Pokračujte v iteraci přidáním dalších testů, více teorie a další kód v hlavní knihovně. Máte [hotovou verzi testů](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb) a [úplnou implementaci knihovny](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService/PrimeService.vb).

Vytvořili jste malou knihovnu a sadu testů jednotek pro tuto knihovnu. Rozpracovali jste řešení, aby přidávání nových balíčků a testů bylo součástí normálního pracovního postupu. Vyrostli jste většinu času a úsilí při řešení cílů aplikace.
