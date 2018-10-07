---
title: Vytvoření kompletního řešení .NET Core ve Windows pomocí sady Visual Studio 2017
description: Zjistěte, jak k vytvoření kompletního řešení .NET Core v sadě Visual Studio 2017 na Windows.
author: bleroy
ms.author: mairaw
ms.date: 11/16/2016
ms.custom: vs-dotnet
ms.openlocfilehash: c21c257b55c4389ea4a60fca55eb83cff60ff3b5
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/06/2018
ms.locfileid: "48840937"
---
# <a name="building-a-complete-net-core-solution-on-windows-using-visual-studio-2017"></a>Vytvoření kompletního řešení .NET Core ve Windows pomocí sady Visual Studio 2017

Visual Studio 2017 poskytuje plnohodnotné vývojové prostředí pro vývoj aplikací .NET Core. Postupy v tomto dokumentu popisují kroky potřebné k začlenění typické řešení .NET Core, který obsahuje opakovaně použitelné knihovny, testování a přes knihovny třetích stran. 

## <a name="prerequisites"></a>Požadavky

Postupujte podle pokynů [naší stránce s požadavky](../windows-prerequisites.md) k aktualizaci vašeho prostředí.

## <a name="a-solution-using-only-net-core-projects"></a>Řešení, které využívá jenom projekty .NET Core

### <a name="writing-the-library"></a>Zápis knihovny

1. V sadě Visual Studio, zvolte **souboru**, **nový**, **projektu**. V **nový projekt** dialogového okna, rozbalte **Visual C#** uzlu a zvolte **.NET Standard** uzel a klikněte na tlačítko **knihovna tříd (.NET Standard)**. Tím se vytvoří knihovny .NET Standard, který cílí na .NET Core stejně jako jiné implementace .NET, která podporuje verzi 2.0 [.Net Standard](https://docs.microsoft.com/en-us/dotnet/standard/net-standard)

2. Název projektu "Library" a "Golden" řešení. Ponechte **vytvořit adresář pro řešení** zaškrtnuto. Klikněte na tlačítko **OK**.

3. V Průzkumníku řešení otevřete kontextovou nabídku **závislosti** uzlu a zvolte **spravovat balíčky NuGet**.

4. Zvolte možnost "nuget.org" jako **zdroj balíčku**a zvolte **Procházet** kartu. Vyhledat **Newtonsoft.Json**. Klikněte na tlačítko **nainstalovat**a přijměte licenční smlouvu. Balíček by se měl zobrazit v části **závislosti/NuGet** a se automaticky obnoví.

5. Přejmenovat `Class1.cs` soubor `Thing.cs`. Přijměte přejmenování třídy. Přidejte metodu: `public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`

7. Na **sestavení** nabídce zvolte **sestavit řešení**.

   Má řešení sestavit bez chyb.

### <a name="writing-the-test-project"></a>Zápis testovacího projektu

1. V Průzkumníku řešení otevřete kontextovou nabídku **řešení** uzlu a zvolte **přidat**, **nový projekt**. V **nový projekt** dialogového okna, v části **Visual C# / .NET Core**, zvolte **projekt testu jednotek (.NET Core)**. Pojmenujte ji "TestLibrary" a klikněte na tlačítko OK. 

2. V **TestLibrary** projektu, otevřete kontextovou nabídku **závislosti** uzlu a zvolte **přidat odkaz**. Klikněte na tlačítko **projekty**, zkontrolujte projekt knihovny a klikněte na tlačítko OK. To přidá odkaz na knihovnu z testovacího projektu.

3. Přejmenovat `UnitTest1.cs` do souboru `LibraryTests.cs` a přijměte přejmenování třídy. Přidat `using Library;` na začátek souboru a nahraďte `TestMethod1` metodu s následujícím kódem:
    ```csharp
    [TestMethod]
    public void ThingGetsObjectValFromNumber()
    {
        Assert.AreEqual(42, new Thing().Get(42));
    }
    ```

   Teď by měl být možné sestavit řešení. 
   
4. Na **testování** nabídce zvolte **Windows**, **Průzkumníka testů** zajistí okna Průzkumníka testů do pracovního prostoru. Po několika sekundách `ThingGetsObjectValFromNumber` test by se měla zobrazit v Průzkumníku testů. Zvolte **spustit všechny**.
   
   Test by měl úspěšný.

### <a name="writing-the-console-app"></a>Zápis aplikace konzoly

1. V Průzkumníku řešení otevřete kontextovou nabídku řešení a přidejte nový **Konzolová aplikace (.NET Core)** projektu. Název "Aplikace".

2. V **aplikace** projektu, otevřete kontextovou nabídku **závislosti** uzlu a zvolte **přidat**, **odkaz**. 

3. V **správce odkazů** dialogové okno Kontrola **knihovny** pod **projekty**, **řešení** uzlu a pak klikněte na tlačítko **OK**

6. Otevřete místní nabídku pro **aplikace** uzlu a zvolte **nastavit jako spouštěný projekt**. Tím se zajistí, že stisknutí F5 nebo CTRL + F5 se spustí aplikace konzoly.

7. Otevřít `Program.cs` přidejte `using Library;` na začátek souboru a pak přidejte `Console.WriteLine($"The answer is {new Thing().Get(42)}.");` k `Main` – metoda.

8. Nastavte zarážku po řádek, který jste právě přidali.

9. Stisknutím klávesy F5 spusťte aplikaci...

   Aplikace má sestavit bez chyb a by měl zarážce. Musíte mít také možnost zkontrolovat, že aplikace výstupu "odpověď je 42.".
