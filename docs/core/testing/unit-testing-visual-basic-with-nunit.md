---
title: Testování částí Visual Basic v .NET Core pomocí příkazu dotnet test a NUnit
description: Seznamte se s koncepty testování částí v .NET Core pomocí interaktivního prostředí, které vytváří ukázkové Visual Basic řešení, pomocí NUnit.
author: rprouse
ms.date: 10/04/2018
ms.openlocfilehash: 8f05d25a0add76f5c552f5b9ac1eb310c3d6407a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715410"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-nunit"></a>Testování částí Visual Basic knihoven .NET Core pomocí příkazu dotnet test a NUnit

Tento kurz vás provede interaktivním vytvořením ukázkového řešení, které vás seznámí s koncepty testování částí. Pokud chcete postupovat podle kurzu s předdefinovaným řešením, zobrazte si [ukázkový kód](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-nunit/) před jeho zahájením nebo si ho stáhněte. Pokyny ke stažení najdete v tématu [ukázky a kurzy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="prerequisites"></a>Požadavky

- [.NET Core 2,1 SDK](https://dotnet.microsoft.com/download) nebo novější verze.
- Textový editor nebo editor kódu podle vašeho výběru.

## <a name="creating-the-source-project"></a>Vytvoření zdrojového projektu

Otevřete okno prostředí. Vytvořte adresář s názvem *Unit-Testing-VB-nunit* , který bude obsahovat řešení. V tomto novém adresáři spusťte následující příkaz, který vytvoří nový soubor řešení pro knihovnu tříd a testovací projekt:

```dotnetcli
dotnet new sln
```

Potom vytvořte adresář *PrimeService* . Následující osnova znázorňuje strukturu souborů tak daleko:

```console
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
```

Vytvořte *PrimeService* aktuální adresář a spusťte následující příkaz pro vytvoření zdrojového projektu:

```dotnetcli
dotnet new classlib -lang VB
```

Přejmenujte *Class1. vb* na *PrimeService. vb*. Vytvoříte selhání implementace `PrimeService` třídy:

```vb
Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first.")
        End Function
    End Class
End Namespace
```

Změňte adresář zpátky na adresář *testování částí-VB-using-MSTest* . Spuštěním následujícího příkazu přidejte projekt knihovny tříd do řešení:

```dotnetcli
dotnet sln add .\PrimeService\PrimeService.vbproj
```

## <a name="creating-the-test-project"></a>Vytváření testovacího projektu

Dále vytvořte adresář *PrimeService. Tests* . Následující osnova znázorňuje adresářovou strukturu:

```console
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

Vytvořte adresář *PrimeService. Tests* pro aktuální adresář a vytvořte nový projekt pomocí následujícího příkazu:

```dotnetcli
dotnet new nunit -lang VB
```

Příkaz [dotnet New](../tools/dotnet-new.md) vytvoří testovací projekt, který jako knihovnu testů používá nunit. Vygenerovaná šablona konfiguruje Test Runner v souboru *PrimeServiceTests. vbproj* :

[!code-xml[Packages](~/samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj#Packages)]

Testovací projekt vyžaduje pro vytvoření a spuštění testů jednotek další balíčky. `dotnet new` v předchozím kroku jsme přidali NUnit a adaptér testu NUnit. Nyní přidejte knihovnu tříd `PrimeService` jako jinou závislost do projektu. Použijte příkaz [`dotnet add reference`](../tools/dotnet-add-reference.md) :

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.vbproj
```

Celý soubor můžete zobrazit v [úložišti ukázek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) na GitHubu.

Máte následující konečné rozložení řešení:

```console
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeService.Tests.vbproj
```

Spusťte následující příkaz v adresáři *Unit-Testing-VB-nunit* :

```dotnetcli
dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj
```

## <a name="creating-the-first-test"></a>Vytvoření prvního testu

Napíšete jeden neúspěšný test, udělejte ho a pak proces opakujte. V adresáři *PrimeService. Tests* přejmenujte soubor *UnitTest1. vb* na *PrimeService_IsPrimeShould. vb* a nahraďte jeho celý obsah následujícím kódem:

```vb
Imports NUnit.Framework

Namespace PrimeService.Tests
    <TestFixture>
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <Test>
        Sub IsPrime_InputIs1_ReturnFalse()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

Atribut `<TestFixture>` označuje třídu, která obsahuje testy. Atribut `<Test>` označuje metodu, která je spuštěna nástrojem Test Runner. Z rutiny *testování částí-VB-nunit*spusťte [`dotnet test`](../tools/dotnet-test.md) pro sestavení testů a knihovny tříd a poté spusťte testy. NUnit Test Runner obsahuje vstupní bod programu pro spuštění testů. `dotnet test` spustí Test Runner pomocí projektu testování částí, který jste vytvořili.

Test se nezdařil. Ještě jste nevytvořili implementaci. Proveďte tento test průchodu tak, že napíšete nejjednodušší kód ve třídě `PrimeService`, která funguje:

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first.")
End Function
```

V adresáři *Unit-Testing-VB-nunit* znovu spusťte `dotnet test`. Příkaz `dotnet test` spustí sestavení pro projekt `PrimeService` a potom pro projekt `PrimeService.Tests`. Po sestavení obou projektů spustí tento jediný test. Předá.

## <a name="adding-more-features"></a>Přidání dalších funkcí

Teď, když jste udělali jeden test Pass, je čas zapsat další. Pro čísla apostrofů existuje několik dalších jednoduchých případů: 0,-1. Tyto případy můžete přidat jako nové testy s atributem `<Test>`, ale to se rychle bude zdlouhavé. Existují další atributy xUnit, které umožňují napsat sadu podobných testů.  Atribut `<TestCase>` představuje sadu testů, které spouštějí stejný kód, ale mají různé vstupní argumenty. Pomocí atributu `<TestCase>` můžete zadat hodnoty pro tyto vstupy.

Namísto vytváření nových testů, použijte tyto dva atributy k vytvoření řady testů, které testují několik hodnot menší než dvě, což je nejnižší číslo základny:

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

Spusťte `dotnet test`a dva z těchto testů selžou. Chcete-li provést všechny testy Pass, změňte klauzuli `if` na začátku `Main` metody v souboru *PrimeServices.cs* :

```vb
if candidate < 2
```

Pokračujte v iteraci přidáním dalších testů, více teorie a další kód v hlavní knihovně. Máte [hotovou verzi testů](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) a [úplnou implementaci knihovny](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb).

Vytvořili jste malou knihovnu a sadu testů jednotek pro tuto knihovnu. Rozpracovali jste řešení, aby přidávání nových balíčků a testů bylo součástí normálního pracovního postupu. Vyrostli jste většinu času a úsilí při řešení cílů aplikace.
