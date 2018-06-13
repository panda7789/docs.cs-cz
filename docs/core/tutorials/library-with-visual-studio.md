---
title: Sestavení .NET standardní knihovny tříd s C# a .NET Core v Visual Studio 2017
description: Naučte se vytvářet napsané v C# s použitím Visual Studio 2017 .NET standardní knihovny tříd.
author: BillWagner
ms.author: wiwagn
ms.date: 08/07/2017
ms.openlocfilehash: fa265dc5e1101c54ae8d65ad9a3232cd6bd4e52a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33211986"
---
# <a name="building-a-class-library-with-c-and-net-core-in-visual-studio-2017"></a>Vytvoření knihovny tříd s C# a .NET Core v Visual Studio 2017

A *knihovny tříd* definuje typy a metody, které se nazývají jiná aplikace. Knihovny tříd zacílený standardní rozhraní .NET 2.0 umožňuje své knihovny a volat žádnou implementaci rozhraní .NET, která podporuje tuto verzi .NET Standard. Po dokončení knihovny tříd, můžete se rozhodnout, zda chcete distribuovat jako součást jiného výrobce nebo jestli chcete zahrnout jako součást připojené pomocí jedné nebo více aplikací.

> [!NOTE]
> Seznam .NET Standard verze a platformy podporují, naleznete v části [.NET Standard](../../standard/net-standard.md).

V tomto tématu vytvoříte jednoduchého nástroje knihovny, která obsahuje jednu metodu zpracování řetězce. Budete implementovat jej jako [metoda rozšíření](../../csharp/programming-guide/classes-and-structs/extension-methods.md) tak, aby můžete volat, jako by šlo členem <xref:System.String> třídy.

## <a name="creating-a-class-library-solution"></a>Vytváření řešení knihovna – třída

Začněte vytvořením řešení pro váš projekt knihovny tříd a jeho souvisejících projekty. Řešení sady Visual Studio právě slouží jako kontejner pro jeden nebo více projektů. Pokud chcete vytvořit řešení:

1. Na panelu nabídek Visual Studio zvolte **soubor** > **nový** > **projektu**.

1. V **nový projekt** dialogové okno, rozbalte **jiné typy projektů** uzel a vyberte možnost **řešení sady Visual Studio**. Název řešení "ClassLibraryProjects" a vyberte **OK** tlačítko.

   ![Dialogové okno Nový projekt](./media/library-with-visual-studio/newproject.png)

## <a name="creating-the-class-library-project"></a>Vytvoření projektu knihovny tříd

Vytvoření projektu knihovny tříd:

1. V **Průzkumníku řešení**, klikněte pravým tlačítkem na **ClassLibraryProjects** řešení souboru a v místní nabídce vyberte **přidat** > **nový Projekt**.

1. V **přidat nový projekt** dialogové okno, rozbalte **Visual C#** uzlu, pak vyberte **.NET Standard** následuje uzlu **(.NET Standard)–Knihovnatříd** šablona projektu. V **název** textové pole, jako název projektu zadejte "StringLibrary". Vyberte **OK** k vytvoření projektu knihovny tříd.

   ![Přidat dialogové okno Nový projekt](./media/library-with-visual-studio/libproject.png)

   V okně Kód pak otevře ve vývojovém prostředí sady Visual Studio.

   ![Visual Studio okna aplikace zobrazuje kód výchozí třídy knihovny šablony](./media/library-with-visual-studio/stringlibrary.png)

1. Zkontrolujte, že naše knihovna cílem správnou verzi .NET Standard. Klikněte pravým tlačítkem na projekt knihovny v **Průzkumníku řešení** windows, potom vyberte **vlastnosti**. **Cílové rozhraní** textového pole ukazuje, že jsme se cílení na rozhraní .NET 2.0 standardní.

   ![Vlastnosti projektu pro knihovny tříd](./media/library-with-visual-studio/properties.png)

1. Nahraďte kód v okně kód následující kód a soubor uložte:

   [!CODE-csharp[ClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]

   Knihovna tříd `UtilityLibraries.StringLibrary`, obsahuje metodu s názvem `StartsWithUpper`, která vrátí <xref:System.Boolean> hodnotu, která určuje, zda aktuální instance řetězec začíná velké písmeno. Standardu Unicode rozlišuje velká písmena z malých písmen. <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> Metoda vrátí `true` Pokud znak je velké písmeno.

1. Na panelu nabídek vyberte **sestavení** > **sestavit řešení**. Projekt by měl kompilovat bez chyby.

   ![V podokně výstupu zobrazující, že bylo úspěšně dokončeno sestavení](./media/library-with-visual-studio/buildsucceeds.png)

## <a name="next-step"></a>Další krok

Úspěšně jste vytvořili knihovny. Vzhledem k tomu, že nebyly volá všechny její metody, nevíte, zda vše funguje podle očekávání. Dalším krokem při vývoji vaše knihovna je otestovat pomocí [projektu testování částí](testing-library-with-visual-studio.md).