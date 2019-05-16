---
title: Sestavení C# knihovny .NET Standard sady Visual Studio 2017
description: Zjistěte, jak vytvořit knihovnu tříd .NET Standard napsané v jazyce C# pomocí sady Visual Studio 2017.
author: BillWagner
ms.author: wiwagn
ms.date: 08/07/2017
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 440ef2ed398b22262923422efd7f1259e3ee9b74
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633695"
---
# <a name="build-a-net-standard-library-with-c-and-the-net-core-sdk-in-visual-studio-2017"></a>Sestavení knihovny .NET Standard s C# a .NET Core SDK v sadě Visual Studio 2017

A *knihovny tříd* definuje typy a metody, které jsou volány aplikací. Knihovna tříd, který cílí na .NET Standard 2.0 umožňuje knihovny, které jsou volány žádné implementace .NET, která podporuje danou verzi .NET Standard. Po dokončení knihovnu tříd, můžete se rozhodnout, zda chcete distribuovat jako součást jiného výrobce nebo určuje, zda chcete zahrnout jako součást připojené pomocí jedné nebo více aplikací.

> [!NOTE]
> Seznam verzí rozhraní .NET Standard a platformy, které podporují, najdete v tématu [.NET Standard](../../standard/net-standard.md).

V tomto tématu vytvoříte knihovnu jednoduchý nástroj, který obsahuje jedinou metodu zpracování řetězců. Budete implementovat jako [– metoda rozšíření](../../csharp/programming-guide/classes-and-structs/extension-methods.md) tak, že můžete volat, jakoby byly členem <xref:System.String> třídy.

## <a name="creating-a-class-library-solution"></a>Vytvoření řešení knihovny tříd

Začněte vytvořením řešení pro váš projekt knihovny tříd a její související projekty. Řešení sady Visual Studio slouží pouze jako kontejner pro jeden nebo více projektů. Vytvoření řešení:

1. Na řádku nabídek sady Visual Studio, zvolte **souboru** > **nový** > **projektu**.

1. V **nový projekt** dialogového okna, rozbalte **ostatní typy projektů** uzel a vyberte možnost **řešení sady Visual Studio**. Název řešení "ClassLibraryProjects" a vyberte **OK** tlačítko.

   ![Dialogové okno Nový projekt se zvýrazněným nové prázdné řešení](./media/library-with-visual-studio/new-project-dialog.png)

## <a name="creating-the-class-library-project"></a>Vytvoření projektu knihovny tříd

Vytvoření projektu knihovny třídy:

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na **ClassLibraryProjects** řešení a v místní nabídce vyberte možnost **přidat** > **nový Projekt**.

1. V **přidat nový projekt** dialogového okna, rozbalte **Visual C#** uzlu, vyberte **.NET Standard** uzel, za nímž následuje **knihovna tříd (.NET Standard)** šablony projektu. V **název** textové pole, zadejte "StringLibrary" jako název projektu. Vyberte **OK** vytvořte projekt knihovny tříd.

   ![Přidat dialogové okno Nový projekt knihovny](./media/library-with-visual-studio/add-new-library-project.png)

   Potom otevře se okno kódu ve vývojovém prostředí sady Visual Studio.

   ![Visual Studio okno aplikace zobrazuje kód výchozí knihovny třídy šablony](./media/library-with-visual-studio/string-library-project.png)

1. Zkontrolujte, že naše knihovny, zaměřuje správná verze modulu .NET Standard. Klikněte pravým tlačítkem na projekt knihovny v **Průzkumníka řešení** windows, vyberte **vlastnosti**. **Cílová architektura** textovém poli se zobrazí, že jsme cílíte .NET Standard 2.0.

   ![Vlastnosti projektu pro knihovny tříd](./media/library-with-visual-studio/library-project-properties.png)

1. Nahraďte kód v okně kód následujícím kódem a soubor uložte:

   [!CODE-csharp[ClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]

   Knihovna tříd `UtilityLibraries.StringLibrary`, obsahuje metodu s názvem `StartsWithUpper`, který vrátí hodnotu <xref:System.Boolean> hodnotu, která určuje, zda aktuální instance řetězec začíná velkým písmenem. Unicode standard rozlišuje velká písmena z malých písmen. <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> Vrátí metoda `true` Pokud znak je velké písmeno.

1. Na panelu nabídek vyberte **sestavení** > **sestavit řešení**. Projekt by měl zkompiluje bez chyb.

   ![Podokno výstup zobrazuje, že sestavení bylo úspěšné](./media/library-with-visual-studio/output-pane-successful-build.png)

## <a name="next-step"></a>Další krok

Úspěšně jste vytvořili knihovnu. Protože nejsou volány kterékoliv z jeho metod, zatím nevíte, jestli funguje podle očekávání. Dalším krokem při vývoji vaší knihovny je testovat pomocí [projekt testů jednotek](testing-library-with-visual-studio.md).
