---
title: Testování částí Visual Basic v .NET Core pomocí příkazu dotnet test a xUnit
description: Seznamte se s koncepty testování částí v .NET Core pomocí interaktivního prostředí, které vytváří ukázkové Visual Basic řešení, pomocí příkazu dotnet test a xUnit.
author: billwagner
ms.author: wiwagn
ms.date: 05/18/2020
ms.openlocfilehash: d87550d692e0b7f3bfee1633bd00cbf501cc2e67
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502753"
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-xunit"></a>Testování částí Visual Basic knihoven .NET Core pomocí příkazu dotnet test a xUnit

V tomto kurzu se dozvíte, jak vytvořit řešení obsahující projekt testování částí a projekt knihovny. Pokud chcete postupovat podle kurzu s použitím předem připraveného řešení, [Zobrazte si ukázkový kód nebo si ho stáhněte](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/). Pokyny ke stažení najdete v tématu [ukázky a kurzy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="create-the-solution"></a>Vytvoření řešení

V této části se vytvoří řešení, které obsahuje zdrojové a testovací projekty. Dokončené řešení má následující adresářovou strukturu:

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        PrimeService.vb
        PrimeService.vbproj
    /PrimeService.Tests
        PrimeService_IsPrimeShould.vb
        PrimeServiceTests.vbproj
```

Následující pokyny popisují postup vytvoření testovacího řešení. Pokyny k vytvoření testovacího řešení v jednom kroku naleznete v tématu [příkazy k vytvoření testovacího řešení](#create-test-cmd) .

* Otevřete okno prostředí.
* Spusťte následující příkaz:

  ```dotnetcli
  dotnet new sln -o unit-testing-using-dotnet-test
  ```

  [`dotnet new sln`](../tools/dotnet-new.md)Příkaz vytvoří nové řešení v adresáři *Unit-Testing-using-dotnet-test* .
* Změňte adresář na složku- *Test-Using-dotnet-test* .
* Spusťte následující příkaz:

  ```dotnetcli
  dotnet new classlib -o PrimeService --lang VB
  ```

   [`dotnet new classlib`](../tools/dotnet-new.md)Příkaz vytvoří nový projekt knihovny tříd ve složce *PrimeService* . Nová knihovna tříd bude obsahovat kód, který chcete testovat.
* Přejmenujte *Class1. vb* na *PrimeService. vb*.
* Nahraďte kód v *PrimeService. vb* následujícím kódem:
  
  ```vb
  Imports System
  
  Namespace Prime.Services
      Public Class PrimeService
          Public Function IsPrime(candidate As Integer) As Boolean
              Throw New NotImplementedException("Not implemented.")
          End Function
      End Class
  End Namespace
  ```

* Předcházející kód:
  * Vyvolá <xref:System.NotImplementedException> zprávu oznamující, že není implementována.
  * Se aktualizuje později v tomto kurzu.

<!-- preceding code shows an english bias. Message makes no sense outside english -->

* V adresáři *testování částí-using-dotnet-test* spusťte následující příkaz pro přidání projektu knihovny tříd do řešení:

  ```dotnetcli
  dotnet sln add ./PrimeService/PrimeService.vbproj
  ```

* Vytvořte projekt *PrimeService. Tests* spuštěním následujícího příkazu:

  ```dotnetcli
  dotnet new xunit -o PrimeService.Tests
  ```

* Předchozí příkaz:
  * Vytvoří projekt *PrimeService. Tests* v adresáři *PrimeService. Tests* . Testovací projekt používá [xUnit](https://xunit.net/) jako knihovnu testů.
  * Konfiguruje Test Runner přidáním následujících `<PackageReference />` prvků do souboru projektu:
    * Microsoft. NET. test. SDK
    * xUnit
    * "xUnit. Runner. VisualStudio"

* Přidejte testovací projekt do souboru řešení spuštěním následujícího příkazu:

  ```dotnetcli
  dotnet sln add ./PrimeService.Tests/PrimeService.Tests.vbproj
  ```

* Přidejte `PrimeService` knihovnu tříd jako závislost do projektu *PrimeService. Tests* :

  ```dotnetcli
  dotnet add ./PrimeService.Tests/PrimeService.Tests.vbproj reference ./PrimeService/PrimeService.vbproj  
  ```

<a name="create-test-cmd"></a>

### <a name="commands-to-create-the-solution"></a>Příkazy k vytvoření řešení

Tato část shrnuje všechny příkazy v předchozí části. Pokud jste dokončili kroky v předchozí části, přeskočte tuto část.

Následující příkazy vytvoří testovací řešení na počítači s Windows. Pro macOS a UNIX aktualizujte `ren` příkaz na verzi operačního systému `ren` pro přejmenování souboru:

```dotnetcli
dotnet new sln -o unit-testing-using-dotnet-test
cd unit-testing-using-dotnet-test
dotnet new classlib -o PrimeService
ren .\PrimeService\Class1.vb PrimeService.vb
dotnet sln add ./PrimeService/PrimeService.vbproj
dotnet new xunit -o PrimeService.Tests
dotnet add ./PrimeService.Tests/PrimeService.Tests.vbproj reference ./PrimeService/PrimeService.vbproj
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.vbproj
```

Postupujte podle pokynů v části "nahrazení kódu v *PrimeService. vb* následujícím kódem" v předchozí části.

## <a name="create-a-test"></a>Vytvořit test

Oblíbeným přístupem v rámci vývoje řízených testů (TDD) je napsat test před implementací cílového kódu. V tomto kurzu se používá přístup TDD. `IsPrime`Metoda je volat, ale není implementovaná. Testovací volání se `IsPrime` nezdařilo. Pomocí TDD je napsán test, u kterého se říká selhání. Cílový kód je aktualizován, aby provedl test Pass. Tento přístup se opakuje, napíše se neúspěšný test a pak se aktualizuje cílový kód, který se má předat.

Aktualizujte projekt *PrimeService. Tests* :

* Odstraňte *PrimeService. Tests/UnitTest1. vb*.
* Vytvořte soubor *PrimeService. Tests/PrimeService_IsPrimeShould. vb* .
* Kód v *jazyce PrimeService_IsPrimeShould. vb* nahraďte následujícím kódem:

```vb
Imports Xunit

Namespace PrimeService.Tests
    Public Class PrimeService_IsPrimeShould
        Private ReadOnly _primeService As Prime.Services.PrimeService

        Public Sub New()
            _primeService = New Prime.Services.PrimeService()
        End Sub


        <Fact>
        Sub IsPrime_InputIs1_ReturnFalse()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

`[Fact]`Atribut deklaruje testovací metodu, která je spuštěna nástrojem Test Runner. Ze složky *PrimeService. Tests* spusťte `dotnet test` . Příkaz [dotnet test](../tools/dotnet-test.md) vytvoří oba projekty a spustí testy. XUnit Test Runner obsahuje vstupní bod programu pro spuštění testů. `dotnet test`spustí Test Runner pomocí projektu testování částí.

Test se nezdařil, protože `IsPrime` nebyl implementován. Pomocí přístupu TDD zapište pouze dostatečný kód, aby tento test prošl. Aktualizujte `IsPrime` pomocí následujícího kódu:

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Not implemented.")
End Function
```

Spusťte `dotnet test`. Test byl úspěšný.

### <a name="add-more-tests"></a>Přidat další testy

Přidejte testy hlavní číslo pro 0 a-1. Předchozí test můžete zkopírovat a změnit následující kód na použití 0 a-1:

```vb
Dim result As Boolean = _primeService.IsPrime(1)

Assert.False(result, "1 should not be prime")
```

Kopírování testovacího kódu, pokud se změní pouze parametr, je výsledkem duplicity kódu a dispozici determinističtější testů. Následující atributy xUnit umožňují zápis sady podobných testů:

- `[Theory]`představuje sadu testů, které spouštějí stejný kód, ale mají různé vstupní argumenty.
- `[InlineData]`atribut určuje hodnoty pro tyto vstupy.

Místo vytváření nových testů použijte předchozí atributy xUnit a vytvořte jednu teorie. Nahraďte následující kód:

```vb
<Fact>
Sub IsPrime_InputIs1_ReturnFalse()
    Dim result As Boolean = _primeService.IsPrime(1)

    Assert.False(result, "1 should not be prime")
End Sub
```

s následujícím kódem:

```vb
<Theory>
<InlineData(-1)>
<InlineData(0)>
<InlineData(1)>
Sub IsPrime_ValuesLessThan2_ReturnFalse(ByVal value As Integer)
    Dim result As Boolean = _primeService.IsPrime(value)

    Assert.False(result, $"{value} should not be prime")
End Sub
```

V předchozím kódu `[Theory]` a `[InlineData]` Povolte testování více hodnot, které jsou menší než dvě. Dva je nejmenší číslo prvočísla.

Spuštění `dotnet test` , dva z testů selžou. Chcete-li provést všechny testy, aktualizujte `IsPrime` metodu následujícím kódem:

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate < 2 Then
        Return False
    End If
    Throw New NotImplementedException("Not fully implemented.")
End Function
```

Po přístupu ke službě TDD přidejte další neúspěšné testy a pak aktualizujte cílový kód. Viz [Dokončená verze testů](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.vb) a [kompletní implementace knihovny](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-dotnet-test/PrimeService/PrimeService.vb).

Metoda Completed `IsPrime` není efektivní algoritmem pro testování primality.

### <a name="additional-resources"></a>Další zdroje

- [Oficiální web xUnit.net](https://xunit.net/)
- [Testování logiky kontroleru v ASP.NET Core](/aspnet/core/mvc/controllers/testing)
- [`dotnet add reference`](../tools/dotnet-add-reference.md)
