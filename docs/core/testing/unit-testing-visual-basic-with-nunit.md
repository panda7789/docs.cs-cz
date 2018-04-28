---
title: Testování jazyka Visual Basic v .NET Core pomocí testovacích dotnet a NUnit částí
description: Další koncepty test jednotky v .NET Core prostřednictvím interaktivní prostředí vytváření ukázkové řešení Visual Basic podrobné pomocí NUnit.
author: rprouse
ms.date: 12/01/2017
ms.topic: conceptual
dev_langs:
- vb
ms.prod: dotnet-core
ms.workload:
- dotnetcore
ms.openlocfilehash: b275d1da2c46b1ba8376bf0a77b4dcb8d6f76445
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="unit-testing-visual-basic-net-core-libraries-using-dotnet-test-and-nunit"></a>Knihovny jazyka Visual Basic .NET Core pomocí testovacích dotnet a NUnit testování částí

Tento kurz vás provede interaktivní prostředí vytváření ukázkové řešení podrobné další koncepty testování částí. Pokud chcete postupovat v kurzu pomocí předdefinovaných řešení, [zobrazení nebo stažení ukázkového kódu](https://github.com/dotnet/samples/tree/master/core/getting-started/unit-testing-vb-nunit/) před zahájením. Pokyny ke stažení najdete v tématu [ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="creating-the-source-project"></a>Vytvoření projektu zdroje

Otevřete okno prostředí. Vytvořte adresář s názvem *jednotky – testování vb-nunit* pro uložení řešení. Uvnitř tohoto nového adresáře, spusťte [ `dotnet new sln` ](../tools/dotnet-new.md) k vytvoření nové řešení. Tento postup je snazší správa knihovny tříd a projektu testování částí. V adresáři řešení vytvořit *PrimeService* adresáře. Proto pokud máte následující strukturu adresáře a souboru:

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
```

Ujistěte se, *PrimeService* aktuální adresář a spusťte [ `dotnet new classlib -lang VB` ](../tools/dotnet-new.md) a vytvořte tak projekt zdroje. Přejmenování *Class1.VB* k *PrimeService.VB*. Použití vývoje řízeného testováním (TDD), vytvořte na selhání implementace `PrimeService` třídy:

```vb
Imports System

Namespace Prime.Services
    Public Class PrimeService
        Public Function IsPrime(candidate As Integer) As Boolean
            Throw New NotImplementedException("Please create a test first")
        End Function
    End Class
End Namespace
```

Změna adresáře zpět do *jednotky – testování vb – pomocí stest* adresáře. Spustit [ `dotnet sln add .\PrimeService\PrimeService.vbproj` ](../tools/dotnet-sln.md) přidání projektu knihovny tříd do řešení.

## <a name="install-the-nunit-project-template"></a>Šablona projektu NUnit instalace

NUnit testování projektu, který je potřeba nainstalovat před vytvořením testovacího projektu šablony. To jenom je nutné provést jednou na každém počítači vývojáře, kde vytvoříte nové projekty NUnit. Spustit [ `dotnet new -i NUnit3.DotNetNew.Template` ](../tools/dotnet-new.md) instalovat NUnit šablony.

 ```
 dotnet new -i NUnit3.DotNetNew.Template
 ```

## <a name="creating-the-test-project"></a>Vytvoření projektu testů

Dále vytvořte *PrimeService.Tests* adresáře. Zobrazí následující osnova adresářovou strukturu:

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
```

Ujistěte se, *PrimeService.Tests* adresář aktuální adresář a vytvoření nového projektu pomocí [ `dotnet new nunit -lang VB` ](../tools/dotnet-new.md). Tento příkaz vytvoří testovací projekt, který používá NUnit jako knihovně testu. Nástroj test runner v nakonfiguruje vygenerované šablony *PrimeServiceTests.vbproj*:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.5.0" />
  <PackageReference Include="NUnit" Version="3.9.0" />
  <PackageReference Include="NUnit3TestAdapter" Version="3.9.0" />
</ItemGroup>
```

K testovacímu projektu vyžaduje další balíčky k vytváření a spouštění testování částí. `dotnet new` v předchozím kroku přidat že nunit a NUnit testovací adaptéru. Nyní přidejte `PrimeService` knihovny tříd jako další závislosti do projektu. Použití [ `dotnet add reference` ](../tools/dotnet-add-reference.md) příkaz:

```
dotnet add reference ../PrimeService/PrimeService.vbproj
```

Zobrazí celý soubor v [ukázky úložiště](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService.Tests.vbproj) na Githubu.

Máte následující rozložení konečné řešení:

```
/unit-testing-vb-nunit
    unit-testing-vb-nunit.sln
    /PrimeService
        Source Files
        PrimeService.vbproj
    /PrimeService.Tests
        Test Source Files
        PrimeServiceTests.vbproj
```

Spuštění [ `dotnet sln add .\PrimeService.Tests\PrimeService.Tests.vbproj` ](../tools/dotnet-sln.md) v *jednotky – testování vb-nunit* adresáře.

## <a name="creating-the-first-test"></a>Vytvoření prvního testu

Volá TDD přístup pro zápis jeden selhání test, což předat a zopakováním postupu. Odebrat *UnitTest1.vb* z *PrimeService.Tests* adresáře a vytvořte nový soubor jazyka Visual Basic s názvem *PrimeService_IsPrimeShould.VB*. Přidejte následující kód:

```vb
Imports NUnit.Framework

Namespace PrimeService.Tests
    <TestFixture>
    Public Class PrimeService_IsPrimeShould
        Private _primeService As Prime.Services.PrimeService = New Prime.Services.PrimeService()

        <Test>
        Sub ReturnFalseGivenValueOf1()
            Dim result As Boolean = _primeService.IsPrime(1)

            Assert.False(result, "1 should not be prime")
        End Sub

    End Class
End Namespace
```

`<TestFixture>` Atribut určuje třídu, která obsahuje testy. `<Test>` Atribut označuje metodu, která spustí nástroj test runner. Z *jednotky – testování vb-nunit*, provést [ `dotnet test` ](../tools/dotnet-test.md) vytvářet testy a knihovny tříd a poté spusťte testy. Nástroj test runner NUnit obsahuje vstupní bod programu ke spuštění testů. `dotnet test` Spustí nástroj test runner pomocí projektu testů jednotek, které jste vytvořili.

Test se nezdaří. Nevytvořili jste ještě implementace. Psaní kódu nejjednodušší v, aby tento test `PrimeService` třídu, která funguje:

```vb
Public Function IsPrime(candidate As Integer) As Boolean
    If candidate = 1 Then
        Return False
    End If
    Throw New NotImplementedException("Please create a test first")
End Function
```

V *jednotky – testování vb-nunit* spusťte `dotnet test` znovu. `dotnet test` Příkaz spustí sestavení pro `PrimeService` projektu a pak `PrimeService.Tests` projektu. Po sestavení obou projektů, spustí se tento jeden test. Pak předá.

## <a name="adding-more-features"></a>Přidání další funkce

Teď, když jste udělali jeden testovací předání, je čas zapsat informace. Existuje několik dalších jednoduchý případů pro prvočísel: 0, -1. Můžete přidat jako nový testování pomocí těchto případech `<Test>` atribut, ale které rychle stane zdlouhavé. Existují další xUnit atributy, které vám umožní zápisu sada testů, podobně jako.  A `<TestCase>` atribut představuje sada testů, které provést stejný kód, ale mají jinou vstupní argumenty. Můžete použít `<TestCase>` atribut zadat hodnoty pro tyto vstupy.

Místo vytváření nové testů, platí tyto dva atributy vytvoření řady testů, které testovací několik hodnoty menší než dva, což je s nejnižším číslem prime:

[!code-vb[Sample_TestCode](../../../samples/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb?name=Sample_TestCode)]

Spustit `dotnet test`, a dvě z nich testy nezdaří. Chcete-li všechny testy průchodu, změnit `if` klauzule na začátku metody:

```vb
if candidate < 2
```

Pokračujte k iteraci v přidáním další testy, další teorií a další kód v knihovně hlavní. Máte [dokončení verzi testy](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService.Tests/PrimeService_IsPrimeShould.vb) a [dokončení implementace knihovny](https://github.com/dotnet/samples/blob/master/core/getting-started/unit-testing-vb-nunit/PrimeService/PrimeService.vb).

Když jste sestavili malé knihovny a sadu testů jednotek pro danou knihovnu. Řešení si strukturovaná, tak, aby přidání nové balíčky a testy je součástí normálním pracovním postupu. Jste soustředí většinu čas a úsilí na řešení cílů aplikace.
