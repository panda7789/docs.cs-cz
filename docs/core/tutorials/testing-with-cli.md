---
title: Uspořádání a testování projektů pomocí příkazového řádku .NET Core
description: Tento kurz vysvětluje, jak uspořádat a testování .NET Core projekty z příkazového řádku.
author: cartermp
ms.author: mairaw
ms.date: 05/16/2017
ms.openlocfilehash: a49eb1d398ab80a4ece703b7889083ea967df862
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33217640"
---
# <a name="organizing-and-testing-projects-with-the-net-core-command-line"></a>Uspořádání a testování projektů pomocí příkazového řádku .NET Core

V tomto kurzu následuje [Začínáme s .NET Core v systému Windows nebo Linux/macOS pomocí příkazového řádku](using-with-xplat-cli.md), přesměrujeme vás nad rámec vytvoření jednoduché konzolové aplikace pro vývoj aplikací pokročilé a dobře uspořádány. Po ukazuje, jak používat složky organizace kódu, tento kurz ukazuje, jak rozšířit konzolovou aplikaci pomocí [xUnit](https://xunit.github.io/) testování framework.

## <a name="using-folders-to-organize-code"></a>Použití složek k uspořádání kódu

Pokud chcete zavést nové typy do konzoly aplikace, můžete tak učinit přidáním soubory obsahující typy, které mají aplikace. Například pokud přidáte soubory obsahující `AccountInformation` a `MonthlyReportRecords` typy do projektu strukturu souborů projektu je plochý a usnadňují přejděte:

```
/MyProject
|__AccountInformation.cs
|__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

Však to jenom funguje i při velikost vašeho projektu je poměrně malý. Můžete si, co se stane Pokud přidáte do projektu 20 typy? Projekt výborný nebude snadno přejděte a udržovat s třídou mnoho soubory littering kořenového adresáře projektu.

K uspořádání projektu, vytvořte novou složku a pojmenujte ji *modely* pro soubory typu. Pro soubory typu do *modely* složky:

```
/MyProject
|__/Models
   |__AccountInformation.cs
   |__MonthlyReportRecords.cs
|__MyProject.csproj
|__Program.cs
```

Projekty, které logicky skupiny souborů do složek, které se dají snadno přejděte a údržbu. V další části je vytvořit složitější ukázku se složkami a testování částí.

## <a name="organizing-and-testing-using-the-newtypes-pets-sample"></a>Uspořádání a testování pomocí ukázkových mazlíčků NewTypes

### <a name="building-the-sample"></a>Vytváření vzorku

Následující postup, můžete buď absolvovat pomocí [NewTypes mazlíčků ukázkové](https://github.com/dotnet/samples/tree/master/core/console-apps/NewTypesMsBuild) nebo vytvořit vlastní soubory a složky. Typy jsou logicky uspořádány do strukturu složek, která umožňuje přidání další typy později a testy jsou také logicky umístit do složky umožňující přidání další testy později.

Ukázka obsahuje dva typy `Dog` a `Cat`a je implementovat společné rozhraní a má `IPet`. Pro `NewTypes` projektu vaším cílem je uspořádat typy související s pet do *mazlíčků* složky. Pokud později, přidáte další sadu typy *WildAnimals* například se umístit do *NewTypes* složky spolu s *mazlíčků* složky. *WildAnimals* složka může obsahovat typy pro zvířat, které nejsou mazlíčků, jako například `Squirrel` a `Rabbit` typy. Tímto způsobem jako typy jsou přidány, projekt zůstává i uspořádány. 

Vytvořte následující strukturu složek s uvedené obsah souboru:

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

*Program.cs*:

[!code-csharp[Main](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/Program.cs)]

*NewTypes.csproj*:

[!code-xml[NewTypes csproj](../../../samples/core/console-apps/NewTypesMsBuild/src/NewTypes/NewTypes.csproj)]

Spuštěním následujících příkazů:

```console
dotnet run
```

Získejte následující výstup:

```console
Woof!
Meow!
```

Volitelné cvičení: můžete přidat nové domácí typu, například `Bird`, tím, že rozšíří tento projekt. Ujistěte se, ptačí perspektivy na `TalkToOwner` metoda udělení `Tweet!` vlastníkovi. Spusťte aplikaci znovu. Výstup bude obsahovat `Tweet!`

### <a name="testing-the-sample"></a>Testování vzorku

`NewTypes` Projektu je na místě a uspořádán udržováním typy související s mazlíčků ve složce. V dalším kroku vytvořte projekt testu a zahájit zápis testování pomocí [xUnit](https://xunit.github.io/) test framework. Testování částí umožňuje automaticky zkontrolujte bevahior vaše domácí typů potvrďte, že jste operační správně.

Vytvoření *testování* složku s *NewTypesTests* v její složce. Na příkazovém řádku z *NewTypesTests* složky, provést `dotnet new xunit`. Tímto se vytvoří dva soubory: *NewTypesTests.csproj* a *UnitTest1.cs*.

K testovacímu projektu nemůže otestovat aktuálně typy v `NewTypes` a vyžaduje odkaz na projekt `NewTypes` projektu. Chcete-li přidat odkaz na projekt, použijte [ `dotnet add reference` ](../tools/dotnet-add-reference.md) příkaz:

```
dotnet add reference ../../src/NewTypes/NewTypes.csproj
```

Máte také možnost ručně přidejte odkaz na projekt tak, že přidáte `<ItemGroup>` uzlu *NewTypesTests.csproj* souboru:

```xml
<ItemGroup>
  <ProjectReference Include="../../src/NewTypes/NewTypes.csproj" />
</ItemGroup>
```

*NewTypesTests.csproj*:

[!code-xml[NewTypesTests csproj](../../../samples/core/console-apps/NewTypesMsBuild/test/NewTypesTests/NewTypesTests.csproj)]

*NewTypesTests.csproj* soubor obsahuje následující:

* Odkaz na balíček `Microsoft.NET.Test.Sdk`, .NET testování infrastruktury
* Odkaz na balíček `xunit`, xUnit testování framework
* Odkaz na balíček `xunit.runner.visualstudio`, nástroj test runner
* Odkaz na projekt `NewTypes`, kód pro testování

Změna názvu *UnitTest1.cs* k *PetTests.cs* a nahraďte kód v souboru následující:

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

Volitelné cvičení: Pokud jste přidali `Bird` dříve typ, který poskytne `Tweet!` vlastníkovi, přidejte metodu testu do *PetTests.cs* souboru, `BirdTalkToOwnerReturnsTweet`, zkontroluje, jestli `TalkToOwner` metoda funguje správně pro `Bird` typu.

> [!NOTE]
> I když můžete očekávat, který `expected` a `actual` jsou hodnoty stejné, počáteční kontrolní výrazy s `Assert.NotEqual` kontroly určit, že jsou *nerovná*. Vždy nejprve vytvořte testy selhání jednou pro ověření logiku testů. Toto je důležitým krokem při metodika návrhu řízeného testováním (TDD). Jakmile potvrdíte, že testy nezdaří, můžete upravit kontrolní výrazy a povolení jejich předávání.

Na obrázku je dokončený projekt strukturu:

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

Spusťte v *test/NewTypesTests* adresáře. Obnovit k testovacímu projektu s [ `dotnet restore` ](../tools/dotnet-restore.md) příkaz. Spouštění testů pomocí [ `dotnet test` ](../tools/dotnet-test.md) příkaz. Tento příkaz spustí nástroj test runner zadaný v souboru projektu.

 [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

 
Podle očekávání, testování selže a konzole zobrazí následující výstup:
 
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

Změnit tvrzení testů z `Assert.NotEqual` k `Assert.Equal`:

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

Testování předává. Domácí typy metody vrací správné hodnoty při posuzování vlastníkovi.

Když jste se naučili techniky k uspořádání a testování projektů pomocí xUnit. Pokračovat v těchto postupů je použití ve vašich vlastních projektů. *Kódování radostí!*

