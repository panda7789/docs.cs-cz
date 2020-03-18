---
title: Testování částí visual basicu v rozhraní .NET Core s dotnet testem a NUnit
description: Naučte koncepty testování částí v .NET Core prostřednictvím interaktivní prostředí vytváření ukázkové řešení jazyka krok za krokem pomocí NUnit.
author: rprouse
ms.date: 10/04/2018
ms.openlocfilehash: a33447457344b241b4c2376d777b0deb7f556874
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240919"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-nunit"></a>Testování částí knihoven Jazyka .NET Core pomocí dotnet test a NUnit

Tento kurz vás provede interaktivní prostředí vytváření ukázkové řešení krok za krokem se dozvíte koncepty testování částí. Pokud dáváte přednost postupujte podle kurzu pomocí předem sestaveného řešení, [zobrazte nebo stáhněte ukázkový kód,](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-nunit/) než začnete. Pokyny ke stažení naleznete v [tématu Ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="prerequisites"></a>Požadavky

- [Sada .NET Core 2.1 SDK](https://dotnet.microsoft.com/download) nebo novější verze.
- Textový editor nebo editor kódu podle vašeho výběru.

## <a name="creating-the-source-project"></a>Vytvoření zdrojového projektu

Otevřete okno prostředí. Vytvořte adresář s názvem *unit-testing-vb-nunit* pro uložení řešení. V tomto novém adresáři spusťte následující příkaz a vytvořte nový soubor řešení pro knihovnu tříd a testovací projekt:

```dotnetcli
dotnet new sln
```

Dále vytvořte adresář *PrimeService.* Následující osnova ukazuje strukturu souborů tak daleko:

```console
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
```

Vytvořte *primeservice* jako aktuální adresář a spusťte následující příkaz k vytvoření zdrojového projektu:

```dotnetcli
dotnet new classlib -lang VB
```

Přejmenujte *třídu 1.VB* na *PrimeService.VB*. Můžete vytvořit selhání implementace `PrimeService` třídy:

```vb
Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first.")
        End Function
    End Class
End Namespace
```

Změňte adresář zpět do adresáře *unit-testing-vb-using-mstest.* Chcete-li do řešení přidat projekt knihovny tříd, spusťte následující příkaz:

```dotnetcli
dotnet sln add .\PrimeService\PrimeService.vbproj
```

## <a name="creating-the-test-project"></a>Vytvoření testovacího projektu

Dále vytvořte adresář *PrimeService.Tests.* Následující osnova ukazuje adresářovou strukturu:

```console
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

Vytvořte adresář *PrimeService.Tests* jako aktuální adresář a vytvořte nový projekt pomocí následujícího příkazu:

```dotnetcli
dotnet new nunit -lang VB
```

[Dotnet new](../tools/dotnet-new.md) příkaz vytvoří testovací projekt, který používá NUnit jako testovací knihovnu. Vygenerovaná šablona konfiguruje testovacího běžce v souboru *PrimeServiceTests.vbproj:*

[!code-xml[Packages](~/samples/snippets/core/testing/unit-testing-vb-nunit/vb/PrimeService.Tests/PrimeService.Tests.vbproj#Packages)]

Testovací projekt vyžaduje další balíčky k vytvoření a spuštění testů částí. `dotnet new`v předchozím kroku přidánn NUnit a NUnit testovací adaptér. Nyní přidejte `PrimeService` knihovnu tříd jako jinou závislost do projektu. Použijte [`dotnet add reference`](../tools/dotnet-add-reference.md) příkaz:

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.vbproj
```

Celý soubor můžete vidět v [úložišti ukázek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) na GitHubu.

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

V adresáři *unit-testing-vb-nunit proveďte* následující příkaz:

```dotnetcli
dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj
```

## <a name="creating-the-first-test"></a>Vytvoření prvního testu

Napíšete jeden neúspěšný test, provedete jeho předání a pak zopakujete proces. V adresáři *PrimeService.Tests* přejmenujte soubor *UnitTest1.vb* na *PrimeService_IsPrimeShould.VB* a nahraďte celý jeho obsah následujícím kódem:

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

Atribut `<TestFixture>` označuje třídu, která obsahuje testy. Atribut `<Test>` označuje metodu, která je spuštěna testovacím běžcem. Z *jednotky unit-testing-vb-nunit*spusťte [`dotnet test`](../tools/dotnet-test.md) k sestavení testů a knihovny tříd a spusťte testy. Testovací běžec NUnit obsahuje vstupní bod programu pro spuštění testů. `dotnet test`spustí testovací houska pomocí projektu testování částí, který jste vytvořili.

Váš test se nezdaří. Ještě jste nevytvořili implementaci. Proveďte tento test projít napsáním `PrimeService` nejjednodušší kód ve třídě, která funguje:

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first.")
End Function
```

V adresáři *unit-testing-vb-nunit* spusťte `dotnet test` znovu. Příkaz `dotnet test` spustí sestavení pro `PrimeService` projekt a `PrimeService.Tests` potom pro projekt. Po sestavení obou projektů spustí tento jediný test. Už to přejde.

## <a name="adding-more-features"></a>Přidání dalších funkcí

Nyní, když jste provedli jeden test projít, je čas napsat více. Existuje několik dalších jednoduchých případů pro prvočísla: 0, -1. Tyto případy můžete přidat jako `<Test>` nové testy s atributem, ale to se rychle stane únavné. Existují další atributy xUnit, které umožňují napsat sadu podobných testů.  Atribut `<TestCase>` představuje sadu testů, které spouštějí stejný kód, ale mají různé vstupní argumenty. `<TestCase>` Atribut můžete použít k určení hodnot pro tyto vstupy.

Namísto vytváření nových testů použijte tyto dva atributy k vytvoření řady testů, které testují několik hodnot menší než dvě, což je nejnižší prvočíslo:

[!code-vb[Sample_TestCode](../../../samples/snippets/core/testing/unit-testing-vb-nunit/vb/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

Spustit `dotnet test`a dva z těchto testů nezdaří. Chcete-li provést všechny testy `if` projít, změňte `Main` klauzuli na začátku metody v *souboru PrimeServices.cs:*

```vb
if candidate < 2
```

Pokračujte v iterátu přidáním dalších testů, dalších teorií a dalšího kódu v hlavní knihovně. Máte [hotovou verzi testů](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) a [kompletní implementaci knihovny](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb).

Vytvořili jste malou knihovnu a sadu testů částí pro tuto knihovnu. Strukturovali jste řešení tak, aby přidání nových balíčků a testů bylo součástí normálního pracovního postupu. Soustředili jste většinu svého času a úsilí na řešení cílů aplikace.
