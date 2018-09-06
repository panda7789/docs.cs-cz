---
title: Uspořádání a testování projektů pomocí příkazového řádku .NET Core
description: Tento kurz vysvětluje, jak uspořádat a Testovací projekty .NET Core z příkazového řádku.
author: cartermp
ms.author: mairaw
ms.date: 05/16/2017
ms.openlocfilehash: 5fdbdc115ea5cd6da54f7c43bec2aa6f82e71310
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43738350"
---
# <a name="organizing-and-testing-projects-with-the-net-core-command-line"></a>Uspořádání a testování projektů pomocí příkazového řádku .NET Core

V tomto kurzu následuje [Začínáme s .NET Core ve Windows, Linux nebo macOS pomocí příkazového řádku](using-with-xplat-cli.md), přechod nad rámec vytváření jednoduchou konzolovou aplikaci pro vývoj pokročilých a dobře organizovaný aplikací. Po ukazuje, jak na složky slouží k uspořádání kódu, tento kurz ukazuje, jak rozšířit aplikaci konzoly pomocí [xUnit](https://xunit.github.io/) testování.

## <a name="using-folders-to-organize-code"></a>Použití složek k uspořádání kódu

Pokud chcete zavést nové typy do konzolové aplikace, provedete to tak, že přidáte soubory, které obsahují typy pro aplikace. Například pokud přidáte soubory, které obsahují `AccountInformation` a `MonthlyReportRecords` typy do projektu, je struktura souboru projektu bez stromové struktury a usnadňuje přechod:

```
/MyProject
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

Ale toto funguje, pouze i když je poměrně malá velikost vašeho projektu. Můžete si představit, co se stane, pokud je 20 typy přidat do projektu? Projekt jednoznačně by se snadno procházet a udržovat s, který mnoho souborů littering kořenový adresář projektu.

K uspořádání projekt, vytvořte novou složku s názvem *modely* pro uložení souborů typů. Umístěte soubory typu do *modely* složky:

```
/MyProject
|__/Models
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

Projekty, které logicky skupiny soubory do složek, které jsou snadno procházet a udržovat. V další části vytvořit složitější vzorek se složkami a testování částí.

## <a name="organizing-and-testing-using-the-newtypes-pets-sample"></a>Uspořádání a testování s využitím ukázkové NewTypes mazlíčků

### <a name="building-the-sample"></a>Vytváření vzorku

Následující postup, můžete buď absolvovat pomocí [NewTypes domácí zvířata ukázka](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild) nebo vytvořit vlastní soubory a složky. Typy jsou logicky uspořádány do struktury složek, který umožňuje přidání dalších typů později, a testy jsou také logicky umístěny ve složkách umožňující přidání další testy později.

Ukázka obsahuje dva typy `Dog` a `Cat`a je jim implementovat obecné rozhraní `IPet`. Pro `NewTypes` projektu, vaším cílem je uspořádat domácí mazlíček souvisejících typů do *Mazlíčci* složky. Pokud se později přidá jinou sadu typů *WildAnimals* například přejdou na *NewTypes* složce společně s *Mazlíčci* složky. *WildAnimals* složka může obsahovat typy pro zvířata, které nejsou mazlíčků, jako například `Squirrel` a `Rabbit` typy. Tímto způsobem přidávání typů projektu zůstane dobře uspořádané. 

Vytvořte následující strukturu složek s obsahem souboru uvedené:

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

[!code-csharp[IPet interface](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/IPet.cs)]

*Dog.cs*:

[!code-csharp[Dog class](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/Dog.cs)]

*Cat.cs*:

[!code-csharp[Cat class](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Pets/Cat.cs)]

*Soubor program.cs*:

[!code-csharp[Main](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Program.cs)]

*NewTypes.csproj*:

[!code-xml[NewTypes csproj](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/NewTypes.csproj)]

Spusťte následující příkazy:

```console
dotnet run
```

Získáte následující výstup:

```console
Woof!
Meow!
```

Volitelné cvičení: můžete přidat nový domácí mazlíčky typ, například `Bird`, rozšířením tento projekt. Ujistěte se, zobrazení z ptačí perspektivy `TalkToOwner` Poskytněte metodu `Tweet!` na vlastníka. Znovu spusťte aplikaci. Výstup bude zahrnovat `Tweet!`

### <a name="testing-the-sample"></a>Testování ukázky

`NewTypes` Projekt je na místě a uspořádán udržováním mazlíčci související typy ve složce. V dalším kroku vytvoření testovacího projektu a začít psát testy s [xUnit](https://xunit.github.io/) rozhraní pro testování. Testování částí umožňuje automaticky zjišťovat bevahior domácí mazlíčky typů potvrďte, že funguje správně.

Vytvoření *testování* složka s *NewTypesTests* složky v něm. Na příkazovém řádku z *NewTypesTests* složce spusťte `dotnet new xunit`. Tímto se vytvoří dva soubory: *NewTypesTests.csproj* a *UnitTest1.cs*.

Projekt testů nelze aktuálně typy v testu `NewTypes` a vyžaduje odkaz na projekt `NewTypes` projektu. Chcete-li přidat odkaz na projekt, použijte [ `dotnet add reference` ](../tools/dotnet-add-reference.md) příkaz:

```
dotnet add reference ../../src/NewTypes/NewTypes.csproj
```

Máte také možnost ručně přidáte odkaz na projekt tak, že přidáte `<ItemGroup>` uzlu *NewTypesTests.csproj* souboru:

```xml
<ItemGroup>
  <ProjectReference Include="../../src/NewTypes/NewTypes.csproj" />
</ItemGroup>
```

*NewTypesTests.csproj*:

[!code-xml[NewTypesTests csproj](../../../samples/core/console-apps/NewTypesMsBuild/test/NewTypesTests/NewTypesTests.csproj)]

*NewTypesTests.csproj* soubor obsahuje následující:

* Odkaz na balíček `Microsoft.NET.Test.Sdk`, .NET testování infrastruktury
* Odkaz na balíček `xunit`, xUnit testování
* Odkaz na balíček `xunit.runner.visualstudio`, nástroj test runner
* Odkaz na projekt `NewTypes`, kód pro testování

Změňte název *UnitTest1.cs* k *PetTests.cs* a nahraďte kód v souboru následujícím kódem:

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

Volitelné cvičení: Pokud jste přidali `Bird` dříve typ, který provede `Tweet!` vlastníkovi, přidejte testovací metody pro *PetTests.cs* souboru, `BirdTalkToOwnerReturnsTweet`, zkontroluje, jestli `TalkToOwner` metoda se dá použít správně `Bird` typu.

> [!NOTE]
> I když můžete očekávat, že `expected` a `actual` jsou hodnoty stejné, počáteční kontrolní výraz se `Assert.NotEqual` kontroly Určuje, že tyto hodnoty jsou *nerovná*. Vždy nejprve vytvořte test selhání za účelem ověření logiky testu. Jakmile potvrdíte, že se test nezdaří, upravte kontrolní výraz, aby test proběhl úspěšně.

Následuje ukázka struktury dokončený projekt:

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

Spustit v *test/NewTypesTests* adresáře. Obnovit testovací projekt s [ `dotnet restore` ](../tools/dotnet-restore.md) příkazu. Spustit testy pomocí [ `dotnet test` ](../tools/dotnet-test.md) příkazu. Tento příkaz spustí nástroj test runner zadané v souboru projektu.

 [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

 
Podle očekávání, testování selže a konzoly se zobrazí následující výstup:
 
```
Test run for C:\NewTypesMsBuild\test\NewTypesTests\bin\Debug\netcoreapp1.1\NewTypesTests.dll(.NETCoreApp,Version=v1.1)
Microsoft (R) Test Execution Command Line Tool Version 15.0.0.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
[xUnit.net 00:00:00.7271827]   Discovering: NewTypesTests
[xUnit.net 00:00:00.8258687]   Discovered:  NewTypesTests
[xUnit.net 00:00:00.8663545]   Starting:    NewTypesTests
[xUnit.net 00:00:01.0109236]     PetTests.CatTalkToOwnerReturnsMeow [FAIL]
[xUnit.net 00:00:01.0119107]       Assert.NotEqual() Failure
[xUnit.net 00:00:01.0120278]       Expected: Not "Meow!"
[xUnit.net 00:00:01.0120968]       Actual:   "Meow!"
[xUnit.net 00:00:01.0130500]       Stack Trace:
[xUnit.net 00:00:01.0141240]         C:\NewTypesMsBuild\test\NewTypesTests\PetTests.cs(22,0): at PetTests.CatTalkToOwnerReturnsMeow()
[xUnit.net 00:00:01.0272364]     PetTests.DogTalkToOwnerReturnsWoof [FAIL]
[xUnit.net 00:00:01.0273649]       Assert.NotEqual() Failure
[xUnit.net 00:00:01.0274166]       Expected: Not "Woof!"
[xUnit.net 00:00:01.0274690]       Actual:   "Woof!"
[xUnit.net 00:00:01.0275264]       Stack Trace:
[xUnit.net 00:00:01.0275960]         C:\NewTypesMsBuild\test\NewTypesTests\PetTests.cs(13,0): at PetTests.DogTalkToOwnerReturnsWoof()
[xUnit.net 00:00:01.0294509]   Finished:    NewTypesTests
Failed   PetTests.CatTalkToOwnerReturnsMeow
Error Message:
 Assert.NotEqual() Failure
Expected: Not "Meow!"
Actual:   "Meow!"
Stack Trace:
   at PetTests.CatTalkToOwnerReturnsMeow() in C:\NewTypesMsBuild\test\NewTypesTests\PetTests.cs:line 22
Failed   PetTests.DogTalkToOwnerReturnsWoof
Error Message:
 Assert.NotEqual() Failure
Expected: Not "Woof!"
Actual:   "Woof!"
Stack Trace:
   at PetTests.DogTalkToOwnerReturnsWoof() in C:\NewTypesMsBuild\test\NewTypesTests\PetTests.cs:line 13

Total tests: 2. Passed: 0. Failed: 2. Skipped: 0.
Test Run Failed.
Test execution time: 2.1371 Seconds
```

Změnit kontrolní výrazy testy z `Assert.NotEqual` k `Assert.Equal`:

[!code-csharp[PetTests class](../../../samples/core/console-apps/NewTypesMsBuild/test/NewTypesTests/PetTests.cs)]

Znovu spusťte testy s `dotnet test` příkazů a získat následující výstup:

```
Microsoft (R) Test Execution Command Line Tool Version 15.0.0.0
Copyright (c) Microsoft Corporation.  All rights reserved.

Starting test execution, please wait...
[xUnit.net 00:00:01.3882374]   Discovering: NewTypesTests
[xUnit.net 00:00:01.4767970]   Discovered:  NewTypesTests
[xUnit.net 00:00:01.5157667]   Starting:    NewTypesTests
[xUnit.net 00:00:01.6408870]   Finished:    NewTypesTests

Total tests: 2. Passed: 2. Failed: 0. Skipped: 0.
Test Run Successful.
Test execution time: 1.6634 Seconds
```

Testuje se předá. Domácí mazlíčky typy metody vrací správné hodnoty, když mluvíme vlastníkovi.

Když jste se naučili techniky k uspořádání a testování projektů s použitím xUnit. Pomocí následujících postupů jejich použití ve vašich vlastních projektů přejdete vpřed. *Šťastné kódování!*

