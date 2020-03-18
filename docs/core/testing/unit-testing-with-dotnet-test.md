---
title: Testování částí kódu Jazyka C# v rozhraní .NET Core pomocí dotnet test a xUnit
description: Naučte koncepty testování částí v C# a .NET Core prostřednictvím interaktivního prostředí, které buduje ukázkové řešení krok za krokem pomocí dotnet test a xUnit.
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: c9e3d63a2cf4f560591459833340b729ffec1b95
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240893"
---
# <a name="unit-testing-c-in-net-core-using-dotnet-test-and-xunit"></a>Testování částí C# v .NET Core pomocí dotnet test a xUnit

Tento kurz ukazuje, jak vytvořit řešení obsahující projekt testování částí a projekt zdrojového kódu. Chcete-li postupovat podle kurzu pomocí předem sestaveného řešení, [zobrazte nebo stáhněte ukázkový kód](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-using-dotnet-test/). Pokyny ke stažení naleznete v [tématu Ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="create-the-solution"></a>Vytvoření řešení

V této části je vytvořeno řešení, které obsahuje zdroj ové a testovací projekty. Dokončené řešení má následující adresářovou strukturu:

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

Následující pokyny poskytují kroky k vytvoření testovacího řešení. Pokyny k vytvoření testovacího řešení v jednom kroku naleznete v [tématu Příkazy k vytvoření testovacího řešení.](#create-test-cmd)

* Otevřete okno prostředí.
* Spusťte následující příkaz:

  ```dotnetcli
  dotnet new sln -o unit-testing-using-dotnet-test
  ```

  Příkaz [`dotnet new sln`](../tools/dotnet-new.md) vytvoří nové řešení v adresáři *testování jednotky using-dotnet-test.*
* Změňte adresář na složku *testování jednotky pomocí dotnet-test.*
* Spusťte následující příkaz:

  ```dotnetcli
  dotnet new classlib -o PrimeService
  ```

   Příkaz [`dotnet new classlib`](../tools/dotnet-new.md) vytvoří nový projekt knihovny tříd ve složce *PrimeService.* Nová knihovna tříd bude obsahovat kód, který má být testován.
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
  * Vyvolá <xref:System.NotImplementedException> se zprávou označující, že není implementována.
  * Je aktualizován později v kurzu.

<!-- preceding code shows an english bias. Message makes no sense outside english -->

* V adresáři *testování jednotky using-dotnet-test* přidejte do řešení následující příkaz:

  ```dotnetcli
  dotnet sln add ./PrimeService/PrimeService.csproj
  ```

* Vytvořte projekt *PrimeService.Tests* spuštěním následujícího příkazu:

  ```dotnetcli
  dotnet new xunit -o PrimeService.Tests
  ```

* Předchozí příkaz:
  * Vytvoří projekt *PrimeService.Tests* v adresáři *PrimeService.Tests.* Testovací projekt používá [xUnit](https://xunit.github.io/) jako testovací knihovnu.
  * Nakonfiguruje testovacího `<PackageReference />`běžce přidáním následujících prvků do souboru projektu:
    * "Microsoft.NET.Test.Sdk"
    * "xunit"
    * "xunit.runner.visualstudio"

* Přidejte testovací projekt do souboru řešení spuštěním následujícího příkazu:

  ```dotnetcli
  dotnet sln add ./PrimeService.Tests/PrimeService.Tests.csproj
  ```

* Přidejte `PrimeService` knihovnu tříd jako závislost do projektu *PrimeService.Tests:*

  ```dotnetcli
  dotnet add ./PrimeService.Tests/PrimeService.Tests.csproj reference ./PrimeService/PrimeService.csproj  
  ```

<a name="create-test-cmd"></a>

### <a name="commands-to-create-the-solution"></a>Příkazy k vytvoření řešení

Tato část shrnuje všechny příkazy v předchozí části. Pokud jste dokončili kroky v předchozí části, tuto část přeskočte.

Následující příkazy vytvořit testovací řešení v počítači se systémem Windows. V případě macOS a `ren` Unixu aktualizujte `ren` příkaz na verzi operačního systému a přejmenujte soubor:

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

Postupujte podle pokynů pro "Nahradit kód v *PrimeService.cs* s následujícím kódem" v předchozí části.

## <a name="create-a-test"></a>Vytvoření testu

Populární přístup ve vývoji řízený testováním (TDD) je napsat test před implementací cílového kódu. Tento kurz používá přístup TDD. Metoda `IsPrime` je volatelná, ale není implementována. Testovací volání `IsPrime` se nezdaří. S TDD je napsán test, o kterých je známo, že se nezdaří. Cílový kód je aktualizován tak, aby test projít. Budete pokračovat v opakování tohoto přístupu, psaní selhání testu a pak aktualizace cílového kódu předat.

Aktualizace projektu *PrimeService.Tests:*

* Odstranit *PrimeService.Tests/UnitTest1.cs*.
* Vytvořte soubor *PrimeService.Tests/PrimeService_IsPrimeShould.cs.*
* Nahraďte kód v *PrimeService_IsPrimeShould.cs* následujícím kódem:

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

Atribut `[Fact]` deklaruje testovací metodu, která je spuštěna testovacím běžcem. Ze složky *PrimeService.Tests* spusťte `dotnet test`. [Dotnet test](../tools/dotnet-test.md) příkaz vytvoří oba projekty a spustí testy. XUnit test runner obsahuje vstupní bod programu ke spuštění testů. `dotnet test`spustí testovací běh pomocí projektu testování částí.

Test se `IsPrime` nezdaří, protože nebyl implementován. Pomocí přístupu TDD, napište pouze dostatek kódu, aby tento test projde. Aktualizace `IsPrime` s následujícím kódem:

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

Spusťte `dotnet test`. Test projde.

### <a name="add-more-tests"></a>Přidání dalších testů

Přidejte testy prvočísel pro 0 a -1. Můžete zkopírovat předchozí test a změnit následující kód pro použití 0 a -1:

```csharp
var result = _primeService.IsPrime(1);

Assert.False(result, "1 should not be prime");
```

Kopírování testovacího kódu při změně pouze parametru má za následek duplikaci kódu a testovací nadýmání. Následující atributy xUnit umožňují zápis sady podobných testů:

- `[Theory]`představuje sadu testů, které spouštějí stejný kód, ale mají různé vstupní argumenty.

- `[InlineData]`atribut určuje hodnoty pro tyto vstupy.

Spíše než vytvářet nové testy, použijte předchozí xUnit atributy k vytvoření jedné teorie. Nahraďte následující kód:

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

V předchozím kódu `[Theory]` a `[InlineData]` povolit testování několik hodnot menší než dvě. Dvojka je nejmenší prvočíslo.

Spuštění `dotnet test`, dva testy se nezdaří. Chcete-li provést všechny testy `IsPrime` projít, aktualizujte metodu s následujícím kódem:

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

Podle přístupu TDD přidejte další testy selhání a aktualizujte cílový kód. Podívejte se na [hotovou verzi testů](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService.Tests/PrimeService_IsPrimeShould.cs) a [kompletní implementaci knihovny](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-using-dotnet-test/PrimeService/PrimeService.cs).

Dokončená `IsPrime` metoda není efektivní algoritmus pro testování primality.

### <a name="additional-resources"></a>Další zdroje

- [xUnit.net oficiální stránky](https://xunit.github.io)
- [Logika testovacího řadiče v ASP.NET core](/aspnet/core/mvc/controllers/testing)
- [`dotnet add reference`](../tools/dotnet-add-reference.md)
