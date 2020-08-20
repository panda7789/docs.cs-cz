---
title: Testování částí kódu v jazyce C# v rozhraní .NET Core pomocí příkazu dotnet test a xUnit
description: Seznamte se s koncepty testování částí v jazycích C# a .NET Core pomocí interaktivního prostředí, které vytváří ukázkové řešení pomocí příkazu dotnet test a xUnit.
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: feff4cabbd10064ef4acca12d4f960f2a40a2b12
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656381"
---
# <a name="unit-testing-c-in-net-core-using-dotnet-test-and-xunit"></a>Testování částí C# v .NET Core pomocí příkazu dotnet test a xUnit

V tomto kurzu se dozvíte, jak vytvořit řešení obsahující projekt testování částí a projekt zdrojového kódu. Pokud chcete postupovat podle kurzu s použitím předem připraveného řešení, [Zobrazte si ukázkový kód nebo si ho stáhněte](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/). Pokyny ke stažení najdete v tématu [ukázky a kurzy](../../samples-and-tutorials/index.md#view-and-download-samples).

## <a name="create-the-solution"></a>Vytvoření řešení

V této části se vytvoří řešení, které obsahuje zdrojové a testovací projekty. Dokončené řešení má následující adresářovou strukturu:

```
/unit-testing-using-dotnet-test
    unit-testing-using-dotnet-test.sln
    /PrimeService
        PrimeService.cs
        PrimeService.csproj
    /PrimeService.Tests
        PrimeService_IsPrimeShould.cs
        PrimeServiceTests.csproj
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
  dotnet new classlib -o PrimeService
  ```

   [`dotnet new classlib`](../tools/dotnet-new.md)Příkaz vytvoří nový projekt knihovny tříd ve složce *PrimeService* . Nová knihovna tříd bude obsahovat kód, který chcete testovat.
* Přejmenujte *Class1.cs* na *PrimeService.cs*.
* Nahraďte kód v *PrimeService.cs* následujícím kódem:
  
  ```csharp
  using System;

  namespace Prime.Services
  {
      public class PrimeService
      {
          public bool IsPrime(int candidate)
          {
              throw new NotImplementedException("Not implemented.");
          }
      }
  }
  ```

* Předcházející kód:
  * Vyvolá <xref:System.NotImplementedException> zprávu oznamující, že není implementována.
  * Se aktualizuje později v tomto kurzu.

<!-- preceding code shows an english bias. Message makes no sense outside english -->

* V adresáři *testování částí-using-dotnet-test* spusťte následující příkaz pro přidání projektu knihovny tříd do řešení:

  ```dotnetcli
  dotnet sln add ./PrimeService/PrimeService.csproj
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
  dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
  ```

* Přidejte `PrimeService` knihovnu tříd jako závislost do projektu *PrimeService. Tests* :

  ```dotnetcli
  dotnet add ./PrimeService.Tests/PrimeService.Tests.csproj reference ./PrimeService/PrimeService.csproj  
  ```

<a name="create-test-cmd"></a>

### <a name="commands-to-create-the-solution"></a>Příkazy k vytvoření řešení

Tato část shrnuje všechny příkazy v předchozí části. Pokud jste dokončili kroky v předchozí části, přeskočte tuto část.

Následující příkazy vytvoří testovací řešení na počítači s Windows. Pro macOS a UNIX aktualizujte `ren` příkaz na verzi operačního systému `ren` pro přejmenování souboru:

```dotnetcli
dotnet new sln -o unit-testing-using-dotnet-test
cd unit-testing-using-dotnet-test
dotnet new classlib -o PrimeService
ren .\PrimeService\Class1.cs PrimeService.cs
dotnet sln add ./PrimeService/PrimeService.csproj
dotnet new xunit -o PrimeService.Tests
dotnet add ./PrimeService.Tests/PrimeService.Tests.csproj reference ./PrimeService/PrimeService.csproj
dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
```

Podle pokynů v části "nahraďte kód v *PrimeService.cs* pomocí následujícího kódu" v předchozí části.

## <a name="create-a-test"></a>Vytvořit test

Oblíbeným přístupem v rámci vývoje řízených testů (TDD) je napsat test před implementací cílového kódu. V tomto kurzu se používá přístup TDD. `IsPrime`Metoda je volat, ale není implementovaná. Testovací volání se `IsPrime` nezdařilo. Pomocí TDD je napsán test, u kterého se říká selhání. Cílový kód je aktualizován, aby provedl test Pass. Tento přístup se opakuje, napíše se neúspěšný test a pak se aktualizuje cílový kód, který se má předat.

Aktualizujte projekt *PrimeService. Tests* :

* Odstraňte *PrimeService. Tests/UnitTest1. cs*.
* Vytvořte soubor *PrimeService. Tests/PrimeService_IsPrimeShould. cs*  .
* Nahraďte kód v *PrimeService_IsPrimeShould. cs* následujícím kódem:

```csharp
using Xunit;
using Prime.Services;

namespace Prime.UnitTests.Services
{
    public class PrimeService_IsPrimeShould
    {
        private readonly PrimeService _primeService;

        public PrimeService_IsPrimeShould()
        {
            _primeService = new PrimeService();
        }

        [Fact]
        public void IsPrime_InputIs1_ReturnFalse()
        {
            var result = _primeService.IsPrime(1);

            Assert.False(result, "1 should not be prime");
        }
    }
}
```

`[Fact]`Atribut deklaruje testovací metodu, která je spuštěna nástrojem Test Runner. Ze složky *PrimeService. Tests* spusťte `dotnet test` . Příkaz [dotnet test](../tools/dotnet-test.md) vytvoří oba projekty a spustí testy. XUnit Test Runner obsahuje vstupní bod programu pro spuštění testů. `dotnet test` spustí Test Runner pomocí projektu testování částí.

Test se nezdařil, protože `IsPrime` nebyl implementován. Pomocí přístupu TDD zapište pouze dostatečný kód, aby tento test prošl. Aktualizujte `IsPrime` pomocí následujícího kódu:

```csharp
public bool IsPrime(int candidate)
{
    if (candidate == 1)
    {
        return false;
    }
    throw new NotImplementedException("Not fully implemented.");
}
```

Spusťte `dotnet test`. Test byl úspěšný.

### <a name="add-more-tests"></a>Přidat další testy

Přidejte testy hlavní číslo pro 0 a-1. Předchozí test můžete zkopírovat a změnit následující kód na použití 0 a-1:

```csharp
var result = _primeService.IsPrime(1);

Assert.False(result, "1 should not be prime");
```

Kopírování testovacího kódu, pokud se změní pouze parametr, je výsledkem duplicity kódu a dispozici determinističtější testů. Následující atributy xUnit umožňují zápis sady podobných testů:

- `[Theory]` představuje sadu testů, které spouštějí stejný kód, ale mají různé vstupní argumenty.
- `[InlineData]` atribut určuje hodnoty pro tyto vstupy.

Místo vytváření nových testů použijte předchozí atributy xUnit a vytvořte jednu teorie. Nahraďte následující kód:

```csharp
[Fact]
public void IsPrime_InputIs1_ReturnFalse()
{
    var result = _primeService.IsPrime(1);

    Assert.False(result, "1 should not be prime");
}
```

s následujícím kódem:

[!code-csharp[Sample_TestCode](../../../samples/snippets/core/testing/unit-testing-using-dotnet-test/csharp/PrimeService.Tests/PrimeService_IsPrimeShould.cs?name=Sample_TestCode)]

V předchozím kódu `[Theory]` a `[InlineData]` Povolte testování více hodnot, které jsou menší než dvě. Dva je nejmenší číslo prvočísla.

Spuštění `dotnet test` , dva z testů selžou. Chcete-li provést všechny testy, aktualizujte `IsPrime` metodu následujícím kódem:

```csharp
public bool IsPrime(int candidate)
{
    if (candidate < 2)
    {
        return false;
    }
    throw new NotImplementedException("Not fully implemented.");
}
```

Po přístupu ke službě TDD přidejte další neúspěšné testy a pak aktualizujte cílový kód. Viz [Dokončená verze testů](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) a [kompletní implementace knihovny](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).

Metoda Completed `IsPrime` není efektivní algoritmem pro testování primality.

### <a name="additional-resources"></a>Další zdroje

- [Oficiální web xUnit.net](https://xunit.net)
- [Testování logiky kontroleru v ASP.NET Core](/aspnet/core/mvc/controllers/testing)
- [`dotnet add reference`](../tools/dotnet-add-reference.md)
