---
title: Uspořádání a testování projektů pomocí rozhraní CLI jádra .NET
description: Tento kurz vysvětluje, jak uspořádat a otestovat projekty .NET Core z příkazového řádku.
author: cartermp
ms.date: 09/10/2018
ms.openlocfilehash: 0d61e0fc004cfcb6d78c49475c7b7f0f523aad2c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78239908"
---
# <a name="organizing-and-testing-projects-with-the-net-core-cli"></a>Uspořádání a testování projektů pomocí rozhraní CLI jádra .NET

Tento kurz následuje [Začínáme s rozhraním .NET Core ve Windows/Linux/macOS pomocí příkazového řádku](cli-create-console-app.md), který vás přenese nad rámec vytvoření jednoduché konzolové aplikace pro vývoj pokročilých a dobře organizovaných aplikací. Poté, co ukazuje, jak používat složky k uspořádání kódu, tento kurz ukazuje, jak rozšířit konzolové aplikace s [xUnit](https://xunit.github.io/) testování rámce.

## <a name="using-folders-to-organize-code"></a>Uspořádání kódu pomocí složek

Pokud chcete do konzolové aplikace zavést nové typy, můžete tak učinit přidáním souborů obsahujících typy do aplikace. Pokud například přidáte do `AccountInformation` `MonthlyReportRecords` projektu soubory obsahující a typy, struktura souborů projektu je plochá a snadno se naviguje:

```
/MyProject
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

To však funguje dobře pouze v případě, že velikost projektu je relativně malá. Dokážete si představit, co se stane, když do projektu přidáte 20 typů? Projekt rozhodně nebude snadné se orientovat a udržovat s tím, že mnoho souborů odhazování kořenového adresáře projektu.

Chcete-li projekt uspořádat, vytvořte novou složku a pojmenujte ji *Modely* pro uložení textových souborů. Umístěte textové soubory do složky *Modely:*

```
/MyProject
|__/Models
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

Projekty, které logicky seskupují soubory do složek, lze snadno procházet a udržovat. V další části vytvoříte složitější ukázku se složkami a testováním částí.

## <a name="organizing-and-testing-using-the-newtypes-pets-sample"></a>Uspořádání a testování pomocí newtypes domácí chránič ukázky

### <a name="building-the-sample"></a>Vytvoření vzorku

Následující kroky můžete sledovat pomocí [NewTypes Pets Ukázka](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild) nebo vytvořit vlastní soubory a složky. Typy jsou logicky uspořádány do struktury složek, která umožňuje přidání více typů později a testy jsou také logicky umístěny do složek, které umožňují přidání dalších testů později.

Ukázka obsahuje dva `Dog` `Cat`typy a , a má `IPet`je implementovat společné rozhraní , . Pro `NewTypes` projekt, vaším cílem je uspořádat pet-související typy do složky *Domácí zvířata.* Pokud další sadu typů je přidán později, *WildAnimals* například, jsou umístěny ve složce *NewTypes* vedle *pets* složky. Složka *WildAnimals* může obsahovat typy pro zvířata, `Squirrel` `Rabbit` která nejsou domácími mazlíčky, například a typy. Tímto způsobem, jak jsou přidány typy, projekt zůstává dobře organizovaný.

Vytvořte následující strukturu složek s indikovaným obsahem souboru:

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

*NewTypes.csproj*:

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

Volitelné cvičení: Rozšířením tohoto projektu můžete `Bird`přidat nový typ domácího mazlíčka, například . Aby ptačí `TalkToOwner` metoda dát `Tweet!` majiteli. Spusťte aplikaci znovu. Výstup bude zahrnovat`Tweet!`

### <a name="testing-the-sample"></a>Testování vzorku

Projekt `NewTypes` je na svém místě a vy jste ho uspořádali tak, že jste ve složce uchovávali typy související s domácími zvířaty. Dále vytvořte testovací projekt a začněte psát testy pomocí rozhraní [xUnit](https://xunit.github.io/) test. Testování částí umožňuje automaticky zkontrolovat chování vašeho domácího mazlíčka, abyste potvrdili, že fungují správně.

Přejděte zpět do složky *src* a vytvořte *testovací* složku se složkou *NewTypesTests* v ní. Na příkazovém řádku ze složky `dotnet new xunit` *NewTypesTests* spusťte . Tím se vytvoří dva soubory: *NewTypesTests.csproj* a *UnitTest1.cs*.

Testovací projekt nemůže aktuálně otestovat `NewTypes` typy v aplikaci `NewTypes` a vyžaduje odkaz na projekt. Chcete-li přidat odkaz [`dotnet add reference`](../tools/dotnet-add-reference.md) na projekt, použijte příkaz:

```dotnetcli
dotnet add reference ../../src/NewTypes/NewTypes.csproj
```

Nebo máte také možnost ručně přidat odkaz na projekt `<ItemGroup>` přidáním uzlu do souboru *NewTypesTests.csproj:*

```xml
<ItemGroup>
  <ProjectReference Include="../../src/NewTypes/NewTypes.csproj" />
</ItemGroup>
```

*NewTypesTests.csproj*:

[!code-xml[NewTypesTests csproj](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/test/NewTypesTests/NewTypesTests.csproj)]

Soubor *NewTypesTests.csproj* obsahuje následující:

* Odkaz na `Microsoft.NET.Test.Sdk`balíček , testovací infrastrukturu .NET
* Odkaz na `xunit`balíček , rozhraní xUnit testing framework
* Odkaz na `xunit.runner.visualstudio`balíček , zkušební běžec
* Odkaz na `NewTypes`projekt , kód k testování

Změňte název *UnitTest1.cs,* *chcete-li PetTests.cs* a nahraďte kód v souboru následujícím:

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

Volitelné cvičení: Pokud `Bird` jste přidali typ `Tweet!` dříve, který dává a vlastníkovi, `BirdTalkToOwnerReturnsTweet`přidejte testovací `TalkToOwner` metodu do `Bird` souboru *PetTests.cs* , zkontrolujte, zda metoda funguje správně pro daný typ.

> [!NOTE]
> I když `expected` očekáváte, že hodnoty a `actual` jsou `Assert.NotEqual` stejné, počáteční kontrolní výraz s kontrolou určuje, že tyto hodnoty *nejsou stejné*. Vždy zpočátku vytvořit test nezdaří, aby bylo možné zkontrolovat logiku testu. Po potvrzení, že test se nezdaří, upravte kontrolní výraz povolit test předat.

Následující ukazuje kompletní strukturu projektu:

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

Začněte v adresáři *test/NewTypesTests.* Obnovte testovací projekt [`dotnet restore`](../tools/dotnet-restore.md) pomocí příkazu. Spusťte testy [`dotnet test`](../tools/dotnet-test.md) pomocí příkazu. Tento příkaz spustí testovací běh zadaný v souboru projektu.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Podle očekávání se testování nezdaří a konzola zobrazí následující výstup:

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

Změna kontrolních výrazů `Assert.NotEqual` testů `Assert.Equal`z do :

[!code-csharp[PetTests class](../../../samples/snippets/core/tutorials/testing-with-cli/csharp/test/NewTypesTests/PetTests.cs)]

Znovu spusťte testy `dotnet test` pomocí příkazu a získejte následující výstup:

```output
Test run for c:\Users\ronpet\repos\samples\core\console-apps\NewTypesMsBuild\test\NewTypesTests\bin\Debug\netcoreapp2.1\NewTypesTests.dll(.NETCoreApp,Version=v2.1)
Microsoft (R) Test Execution Command Line Tool Version 15.8.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...

Total tests: 2. Passed: 2. Failed: 0. Skipped: 0.
Test Run Successful.
Test execution time: 1.6029 Seconds
```

Testování projde. Metody typů zvířat vrátí správné hodnoty při rozhovoru s majitelem.

Naučili jste se techniky pro organizaci a testování projektů pomocí xUnit. Pokračujte s těmito technikami jejich použití ve svých vlastních projektech. *Happy kódování!*
