---
title: "Vytvoření kompletního řešení .NET Core do systému Windows, pomocí Visual Studio 2017"
description: "Zjistěte, jak sestavit kompletní .NET Core řešení ve Visual Studio 2017 v systému Windows."
keywords: "Rozhraní .NET, .NET core"
author: bleroy
ms.author: mairaw
ms.date: 11/16/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: ba7e082c-a7c8-431e-a342-f67734b660f6
ms.workload: dotnetcore
ms.openlocfilehash: e922a2c91fab5c513f5c560920d37d77da2d6f84
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="building-a-complete-net-core-solution-on-windows-using-visual-studio-2017"></a>Vytvoření kompletního řešení .NET Core do systému Windows, pomocí Visual Studio 2017

Visual Studio 2017 poskytuje plnohodnotné vývojové prostředí pro vývoj aplikací .NET Core. Postupy v tomto dokumentu popisují kroky potřebné k vytvoření typické .NET Core řešení, které obsahuje opakovaně použitelné knihovny, testování a používání knihoven třetích stran. 

## <a name="prerequisites"></a>Požadavky

Postupujte podle pokynů [naší stránce s požadavky](../windows-prerequisites.md) aktualizovat vaše prostředí.

## <a name="a-solution-using-only-net-core-projects"></a>Řešení pomocí jenom .NET Core projekty

### <a name="writing-the-library"></a>Zápis knihovny

1. V sadě Visual Studio, vyberte **soubor**, **nový**, **projektu**. V **nový projekt** dialogové okno, rozbalte **Visual C#** uzlu a zvolte **.NET Standard** uzel a potom vyberte **(.NET Standard)–Knihovnatříd**. 

2. Název projektu "Library" a "Golden" řešení. Nechte **vytvořit adresář pro řešení** zaškrtnutí. Click **OK**.

3. V Průzkumníku řešení otevřete kontextovou nabídku **závislosti** uzel a zvolte **spravovat balíčky NuGet**.

4. Vyberte "nuget.org" jako **zdroj balíčku**a vyberte **Procházet** kartě. Vyhledejte **Newtonsoft.Json**. Klikněte na tlačítko **nainstalovat**a přijměte licenční smlouvu. Balíček by se měla zobrazit v části **závislosti nebo NuGet** a automaticky obnovit.

5. Přejmenujte `Class1.cs` do souboru `Thing.cs`. Přijměte přejmenování třídy. Přidání metody:`public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`

7. Na **sestavení** nabídce zvolte **sestavit řešení**.

   Řešení má sestavit bez chyby.

### <a name="writing-the-test-project"></a>Zápis k testovacímu projektu

1. V Průzkumníku řešení otevřete kontextovou nabídku **řešení** uzel a zvolte **přidat**, **nový projekt**. V **nový projekt** dialogové okno, v části **Visual C# nebo .NET Core**, zvolte **projektu testování částí (.NET Core)**. Název "TestLibrary" a klikněte na tlačítko OK. 

2. V **TestLibrary** projektu, otevřete kontextovou nabídku **závislosti** uzel a zvolte **přidat odkaz na**. Klikněte na tlačítko **projekty**, zkontrolujte projektu knihovny a klikněte na tlačítko OK. Tento postup přidá odkaz na knihovnu z testovacího projektu.

3. Přejmenujte `UnitTest1.cs` do souboru `LibraryTests.cs` a přijměte tříd přejmenujte. Přidat `using Library;` na začátek souboru a nahradit `TestMethod1` metoda následujícím kódem:
    ```csharp
    [TestMethod]
    public void ThingGetsObjectValFromNumber()
    {
        Assert.AreEqual(42, new Thing().Get(42));
    }
    ```

   Teď by měla být možné sestavit řešení. 
   
4. Na **testování** nabídce zvolte **Windows**, **testování Explorer** mohli okno Průzkumníka testů do pracovního prostoru. Za několik sekund `ThingGetsObjectValFromNumber` test by se měla objevit v Průzkumníka testů. Zvolte **spustit všechny**.
   
   Test by měla předávat.

### <a name="writing-the-console-app"></a>Zápis konzolové aplikace

1. V Průzkumníku řešení otevřete kontextu nabídku pro řešení a přidejte nový **konzolové aplikace (.NET Core)** projektu. Název "Aplikace".

2. V **aplikace** projektu, otevřete kontextovou nabídku **závislosti** uzel a zvolte **přidat**, **odkaz**. 

3. V **správce odkazů** dialogové okno, zkontrolujte **knihovny** pod **projekty**, **řešení** uzel a pak klikněte na tlačítko **OK**

6. Otevřete kontextovou nabídku **aplikace** uzel a zvolte **nastavit jako spouštěný projekt**. Tím se zajistí, že stále mačkat F5 nebo CTRL + F5 spustí konzolovou aplikaci.

7. Otevřete `Program.cs` soubor, přidejte `using Library;` direktivy do horní části souboru a poté přidejte `Console.WriteLine($"The answer is {new Thing().Get(42)}.");` k `Main` metoda.

8. Nastavení boru přerušení po řádek, který jste právě přidali.

9. Stisknutím klávesy F5 spusťte aplikaci...

   Aplikace má sestavit bez chyby a měli průchodu zarážkou. Musíte mít také možnost zkontrolovat, že aplikace výstup "odpověď je 42.".
