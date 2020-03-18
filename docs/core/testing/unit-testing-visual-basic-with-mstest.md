---
title: Testování částí jazyka Visual Basic v rozhraní .NET Core s dotnet testem a MSTest
description: Naučte koncepty testování částí v .NET Core prostřednictvím interaktivního prostředí, které buduje ukázkové řešení jazyka Visual Basic krok za krokem pomocí MSTest.
author: billwagner
ms.author: wiwagn
ms.date: 09/01/2017
ms.openlocfilehash: df167e0559c841510df17ba39801e43315036241
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240932"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-mstest"></a>Testování částí knihoven Jazyka .NET Core pomocí dotnet test a MSTest

Tento kurz vás provede interaktivní prostředí vytváření ukázkové řešení krok za krokem se dozvíte koncepty testování částí. Pokud dáváte přednost postupujte podle kurzu pomocí předem sestaveného řešení, [zobrazte nebo stáhněte ukázkový kód,](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-mstest/) než začnete. Pokyny ke stažení naleznete v [tématu Ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

[!INCLUDE [testing an ASP.NET Core project from .NET Core](../../../includes/core-testing-note-aspnet.md)]

## <a name="creating-the-source-project"></a>Vytvoření zdrojového projektu

Otevřete okno prostředí. Vytvořte adresář s názvem *unit-testing-vb-mstest* pro uložení řešení.
V tomto novém [`dotnet new sln`](../tools/dotnet-new.md) adresáři spusťte a vytvořte nové řešení. Tento postup usnadňuje správu knihovny tříd a projektu testování částí.
V adresáři řešení vytvořte adresář *PrimeService.* Zatím máte následující adresářovou a souborovou strukturu:

```console
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
```

Vytvořte *PrimeService* aktuální [`dotnet new classlib -lang VB`](../tools/dotnet-new.md) adresář a spustit k vytvoření zdrojového projektu. Přejmenujte *třídu 1.VB* na *PrimeService.VB*. Můžete vytvořit selhání implementace `PrimeService` třídy:

```vb
Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first")
        End Function
    End Class
End Namespace
```

Změňte adresář zpět do adresáře *unit-testing-vb-using-mstest.* Spuštěním [`dotnet sln add .\PrimeService\PrimeService.vbproj`](../tools/dotnet-sln.md) přidáte projekt knihovny tříd do řešení.

## <a name="creating-the-test-project"></a>Vytvoření testovacího projektu

Dále vytvořte adresář *PrimeService.Tests.* Následující osnova ukazuje adresářovou strukturu:

```console
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

Vytvořte adresář *PrimeService.Tests* jako aktuální adresář [`dotnet new mstest -lang VB`](../tools/dotnet-new.md)a vytvořte nový projekt pomocí aplikace . Tento příkaz vytvoří testovací projekt, který používá MSTest jako testovací knihovnu. Vygenerovaná šablona konfiguruje testovacího běžce v *souboru PrimeServiceTests.vbproj*:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.18" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.18" />
</ItemGroup>
```

Testovací projekt vyžaduje další balíčky k vytvoření a spuštění testů částí. `dotnet new`v předchozím kroku přidánm MSTest a MSTest runner. Nyní přidejte `PrimeService` knihovnu tříd jako jinou závislost do projektu. Použijte [`dotnet add reference`](../tools/dotnet-add-reference.md) příkaz:

```dotnetcli
dotnet add reference ../PrimeService/PrimeService.vbproj
```

Celý soubor můžete vidět v [úložišti ukázek](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService.Tests.vbproj) na GitHubu.

Máte následující konečné rozložení řešení:

```console
/unit-testing-vb-mstest
    unit-testing-vb-mstest.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.vbproj
```

Spusťte [`dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj`](../tools/dotnet-sln.md) v adresáři *unit-testing-vb-mstest.*

## <a name="creating-the-first-test"></a>Vytvoření prvního testu

Napíšete jeden neúspěšný test, provedete jeho předání a pak zopakujete proces. Odeberte *soubor UnitTest1.vb* z adresáře *PrimeService.Tests* a vytvořte nový soubor jazyka Visual Basic s názvem *PrimeService_IsPrimeShould.VB*. Přidejte následující kód:

```vb
Imports Microsoft.VisualStudio.TestTools.UnitTesting

Namespace PrimeService.Tests
    <TestClass>
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <TestMethod>
        Sub IsPrime_InputIs1_ReturnFalse()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.IsFalse(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

Atribut `<TestClass>` označuje třídu, která obsahuje testy. Atribut `<TestMethod>` označuje metodu, která je spuštěna testovacím běžcem. Z *jednotky testing-vb-mstest*, [`dotnet test`](../tools/dotnet-test.md) spusťte k sestavení testů a knihovny tříd a potom spusťte testy. Testovací běžec MSTest obsahuje vstupní bod programu pro spuštění testů. `dotnet test`spustí testovací houska pomocí projektu testování částí, který jste vytvořili.

Váš test se nezdaří. Ještě jste nevytvořili implementaci. Proveďte tento test projít napsáním `PrimeService` nejjednodušší kód ve třídě, která funguje:

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first.")
End Function
```

V adresáři *unit-testing-vb-mstest* spusťte `dotnet test` znovu. Příkaz `dotnet test` spustí sestavení pro `PrimeService` projekt a `PrimeService.Tests` potom pro projekt. Po sestavení obou projektů spustí tento jediný test. Už to přejde.

## <a name="adding-more-features"></a>Přidání dalších funkcí

Nyní, když jste provedli jeden test projít, je čas napsat více. Existuje několik dalších jednoduchých případů pro prvočísla: 0, -1. Tyto případy můžete přidat jako `<TestMethod>` nové testy s atributem, ale to se rychle stane únavné. Existují další atributy MSTest, které umožňují napsat sadu podobných testů.  Atribut `<DataTestMethod>` představuje sadu testů, které spouštějí stejný kód, ale mají různé vstupní argumenty. `<DataRow>` Atribut můžete použít k určení hodnot pro tyto vstupy.

Namísto vytváření nových testů použijte tyto dva atributy k vytvoření jedné teorie. Teorie je metoda, která testuje několik hodnot menší než dvě, což je nejnižší prvočíslo:

[!code-vb[Sample_TestCode](../../../samples/snippets/core/testing/unit-testing-vb-mstest/vb/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

Spustit `dotnet test`a dva z těchto testů nezdaří. Chcete-li provést všechny testy `if` projít, změňte klauzuli na začátku metody:

```vb
if candidate < 2
```

Pokračujte v iterátu přidáním dalších testů, dalších teorií a dalšího kódu v hlavní knihovně. Máte [hotovou verzi testů](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService.Tests/PrimeService_IsPrimeShould.vb) a [kompletní implementaci knihovny](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-mstest/PrimeService/PrimeService.vb).

Vytvořili jste malou knihovnu a sadu testů částí pro tuto knihovnu. Strukturovali jste řešení tak, aby přidání nových balíčků a testů bylo součástí normálního pracovního postupu. Soustředili jste většinu svého času a úsilí na řešení cílů aplikace.
