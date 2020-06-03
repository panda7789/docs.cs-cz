---
title: Organizování a testování projektů pomocí .NET Core CLI
description: V tomto kurzu se dozvíte, jak organizovat a testovat projekty .NET Core z příkazového řádku.
author: cartermp
ms.date: 09/10/2018
ms.openlocfilehash: 58c78c0f11ab1b275e4e4d05bf1da32562333c91
ms.sourcegitcommit: 0a798a7e9680e2d0a5a81a3eaa203870ea782883
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/03/2020
ms.locfileid: "84325942"
---
# <a name="organizing-and-testing-projects-with-the-net-core-cli"></a>Organizování a testování projektů pomocí .NET Core CLI

Tento kurz následuje [kurz: Vytvoření konzolové aplikace pomocí .NET Core s využitím Visual Studio Code](with-visual-studio-code.md), který vám přesáhne vytvoření jednoduché konzolové aplikace pro vývoj aplikací pro pokročilé a dobře uspořádané aplikace. Po zobrazení, jak používat složky k uspořádání kódu, se v tomto kurzu dozvíte, jak roztáhnout konzolovou aplikaci pomocí testovacího rozhraní [xUnit](https://xunit.github.io/) .

## <a name="using-folders-to-organize-code"></a>Použití složek k uspořádání kódu

Pokud chcete zavést nové typy do konzolové aplikace, můžete to udělat tak, že přidáte soubory, které obsahují typy do aplikace. Například pokud přidáte soubory obsahující `AccountInformation` a `MonthlyReportRecords` typy do projektu, struktura souboru projektu je plochá a Snadná navigace:

```
/MyProject
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

To však funguje i v případě, že velikost projektu je poměrně malá. Můžete si představit, co se stane, když do projektu přidáte 20 typů? Projekt nebude možné snadno procházet a udržovat s tím, že mnoho souborů zachovává kořenový adresář projektu.

Chcete-li uspořádat projekt, vytvořte novou složku a pojmenujte *modely* IT tak, aby obsahovaly soubory typu. Do složky *modely* umístěte soubory typu:

```
/MyProject
|__/Models
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

Projekty, které logicky seskupují soubory do složek, lze snadno procházet a udržovat. V další části vytvoříte složitější vzorek pomocí složek a testování částí.

## <a name="organizing-and-testing-using-the-newtypes-pets-sample"></a>Uspořádání a testování pomocí ukázky NewTypes pro domácí zvířata

### <a name="building-the-sample"></a>Vytvoření ukázky

V následujících krocích můžete postupovat podle toho, jak se používá [Ukázka NewTypes pro domácí](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild) prostředí, nebo můžete vytvořit vlastní soubory a složky. Typy jsou logicky uspořádány do struktury složek, která umožňuje přidání dalších typů později a testy jsou také logicky umístěny do složky umožňující přidání dalších testů později.

Ukázka obsahuje dva typy a a `Dog` `Cat` má k implementaci společné rozhraní `IPet` . Pro `NewTypes` projekt je vaším cílem organizovat do *domácí složky domácí* typy, které souvisejí s PET. Pokud se později přidá další sada typů, *WildAnimals* se například umístí do složky *NewTypes* vedle složky *domácí* . Složka *WildAnimals* může obsahovat typy pro zvířata, která nejsou domácí, například `Squirrel` a `Rabbit` typy. Tímto způsobem, že se přidávají typy, projekt zůstane dobře uspořádaný.

Vytvořte následující strukturu složek se zvýrazněným obsahem souboru:

```
/NewTypes
|__/src
   |__/NewTypes
      |__/Pets
         |__Dog.cs
         |__Cat.cs
         |__IPet.cs
      |__Program.cs
      |__NewTypes.csproj
```

*IPet.cs*:

[!code-csharp[IPet interface](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/IPet.cs)]

*Dog.cs*:

[!code-csharp[Dog class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/Dog.cs)]

*Cat.cs*:

[!code-csharp[Cat class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Pets/Cat.cs)]

*Program.cs*:

[!code-csharp[Main](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/Program.cs)]

*NewTypes. csproj*:

[!code-xml[NewTypes csproj](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/src/NewTypes/NewTypes.csproj)]

Spusťte následující příkaz:

```dotnetcli
dotnet run
```

Získejte následující výstup:

```console
Woof!
Meow!
```

Volitelné cvičení: rozšířením tohoto projektu můžete přidat nový typ PET, například `Bird` ,. Nastavit metodu ptáku `TalkToOwner` jako `Tweet!` vlastníka. Spusťte aplikaci znovu. Výstup bude obsahovat`Tweet!`

### <a name="testing-the-sample"></a>Testování ukázky

`NewTypes`Projekt je na místě a organizujete ho tím, že ve složce zachováte typy související s dalšími místy. Dále vytvořte testovací projekt a začněte psát testy pomocí testovacího rozhraní [xUnit](https://xunit.github.io/) . Testování částí vám umožní automaticky kontrolovat chování typů PET a ověřit tak, že fungují správně.

Přejděte zpět do složky *Src* a vytvořte *testovací* složku se složkou *NewTypesTests* v ní. Na příkazovém řádku ze složky *NewTypesTests* spusťte `dotnet new xunit` . Tím se vytvoří dva soubory: *NewTypesTests. csproj* a *UnitTest1.cs*.

Testovací projekt aktuálně nemůže testovat typy v `NewTypes` a vyžaduje odkaz na projekt `NewTypes` . Chcete-li přidat odkaz na projekt, použijte [`dotnet add reference`](../tools/dotnet-add-reference.md) příkaz:

```dotnetcli
dotnet add reference ../../src/NewTypes/NewTypes.csproj
```

Nebo máte také možnost ručně přidat odkaz na projekt přidáním `<ItemGroup>` uzlu do souboru *NewTypesTests. csproj* :

```xml
<ItemGroup>
  <ProjectReference Include="../../src/NewTypes/NewTypes.csproj" />
</ItemGroup>
```

*NewTypesTests. csproj*:

[!code-xml[NewTypesTests csproj](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/test/NewTypesTests/NewTypesTests.csproj)]

Soubor *NewTypesTests. csproj* obsahuje následující:

* Odkaz na balíček `Microsoft.NET.Test.Sdk` , na který je infrastruktura testování .NET
* Odkaz na balíček `xunit` , na rozhraní xUnit Testing
* Odkaz na balíček `xunit.runner.visualstudio` , na, Test Runner
* Odkaz na projekt na `NewTypes` , kód k otestování

Změňte název *UnitTest1.cs* na *PetTests.cs* a nahraďte kód v souboru následujícím kódem:

```csharp
using System;
using Xunit;
using Pets;

public class PetTests
{
    [Fact]
    public void DogTalkToOwnerReturnsWoof()
    {
        string expected = "Woof!";
        string actual = new Dog().TalkToOwner();

        Assert.NotEqual(expected, actual);
    }

    [Fact]
    public void CatTalkToOwnerReturnsMeow()
    {
        string expected = "Meow!";
        string actual = new Cat().TalkToOwner();

        Assert.NotEqual(expected, actual);
    }
}
```

Volitelné cvičení: Pokud jste přidali `Bird` typ dříve, který `Tweet!` vydává vlastníkovi, přidejte testovací metodu do souboru *PetTests.cs* , `BirdTalkToOwnerReturnsTweet` abyste zkontrolovali, že `TalkToOwner` metoda pro daný typ funguje správně `Bird` .

> [!NOTE]
> I když očekáváte, `expected` že `actual` hodnoty a jsou stejné, počáteční kontrolní výraz s `Assert.NotEqual` touto kontrolou určí, že tyto hodnoty nejsou *stejné*. Před prvním vytvořením testu, který se nezdařil, je zkontrolovat logiku testu. Po potvrzení, že se test nezdařil, upravte kontrolní výraz, aby bylo možné test předat.

Následuje ukázka kompletní struktury projektu:

```
/NewTypes
|__/src
   |__/NewTypes
      |__/Pets
         |__Dog.cs
         |__Cat.cs
         |__IPet.cs
      |__Program.cs
      |__NewTypes.csproj
|__/test
   |__NewTypesTests
      |__PetTests.cs
      |__NewTypesTests.csproj
```

Začněte v adresáři *test/NewTypesTests* . Obnovte testovací projekt pomocí [`dotnet restore`](../tools/dotnet-restore.md) příkazu. Spusťte testy pomocí [`dotnet test`](../tools/dotnet-test.md) příkazu. Tento příkaz spustí Test Runner zadaný v souboru projektu.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Jak bylo očekáváno, testování se nezdařilo a konzola zobrazí následující výstup:

```output
Test run for c:\Users\ronpet\repos\samples\core\console-apps\NewTypesMsBuild\test\NewTypesTests\bin\Debug\netcoreapp2.1\NewTypesTests.dll(.NETCoreApp,Version=v2.1)
Microsoft (R) Test Execution Command Line Tool Version 15.8.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
[xUnit.net 00:00:00.77]     PetTests.DogTalkToOwnerReturnsWoof [FAIL]
[xUnit.net 00:00:00.78]     PetTests.CatTalkToOwnerReturnsMeow [FAIL]
Failed   PetTests.DogTalkToOwnerReturnsWoof
Error Message:
 Assert.NotEqual() Failure
Expected: Not "Woof!"
Actual:   "Woof!"
Stack Trace:
   at PetTests.DogTalkToOwnerReturnsWoof() in c:\Users\ronpet\repos\samples\core\console-apps\NewTypesMsBuild\test\NewTypesTests\PetTests.cs:line 13
Failed   PetTests.CatTalkToOwnerReturnsMeow
Error Message:
 Assert.NotEqual() Failure
Expected: Not "Meow!"
Actual:   "Meow!"
Stack Trace:
   at PetTests.CatTalkToOwnerReturnsMeow() in c:\Users\ronpet\repos\samples\core\console-apps\NewTypesMsBuild\test\NewTypesTests\PetTests.cs:line 22

Total tests: 2. Passed: 0. Failed: 2. Skipped: 0.
Test Run Failed.
Test execution time: 1.7000 Seconds
```

Změňte kontrolní výrazy testů z `Assert.NotEqual` na `Assert.Equal` :

[!code-csharp[PetTests class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/test/NewTypesTests/PetTests.cs)]

Znovu spusťte testy pomocí `dotnet test` příkazu a získejte následující výstup:

```output
Test run for c:\Users\ronpet\repos\samples\core\console-apps\NewTypesMsBuild\test\NewTypesTests\bin\Debug\netcoreapp2.1\NewTypesTests.dll(.NETCoreApp,Version=v2.1)
Microsoft (R) Test Execution Command Line Tool Version 15.8.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...

Total tests: 2. Passed: 2. Failed: 0. Skipped: 0.
Test Run Successful.
Test execution time: 1.6029 Seconds
```

Testy proběhly úspěšně. Metody typu PET vrací správné hodnoty při komunikaci s vlastníkem.

Naučili jste se techniky pro organizování a testování projektů pomocí xUnit. Pokud je chcete použít ve svých vlastních projektech, přečtěte si tyto postupy. *Šťastné kódování!*
