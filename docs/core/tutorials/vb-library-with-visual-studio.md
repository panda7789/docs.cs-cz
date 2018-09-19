---
title: Vytvoření knihovny tříd pomocí jazyka Visual Basic a .NET Core v sadě Visual Studio 2017
description: Další informace o vytváření knihovny tříd napsané v jazyce Visual Basic pomocí sady Visual Studio 2017
author: rpetrusha
ms.author: ronpet
ms.date: 08/07/2017
dev_langs:
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 52bbae330afe4a9ea376c6388a06941f74f6606a
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46006883"
---
# <a name="building-a-class-library-with-visual-basic-and-net-core-in-visual-studio-2017"></a>Vytvoření knihovny tříd pomocí jazyka Visual Basic a .NET Core v sadě Visual Studio 2017

A *knihovny tříd* definuje typy a metody, které jsou volány aplikací. Knihovna tříd, který cílí na .NET Standard 2.0 umožňuje knihovny, které jsou volány žádné implementace .NET, která podporuje danou verzi .NET Standard. Po dokončení knihovnu tříd, můžete se rozhodnout, zda chcete distribuovat jako součást jiného výrobce nebo určuje, zda chcete zahrnout jako součást připojené pomocí jedné nebo více aplikací.

> [!NOTE]
> Seznam verzí rozhraní .NET Standard a platformy, které podporují, najdete v tématu [.NET Standard](../../standard/net-standard.md).

V tomto tématu vytvoříte knihovnu jednoduchý nástroj, který obsahuje jedinou metodu zpracování řetězců. Budete implementovat jako [– metoda rozšíření](../../visual-basic/programming-guide/language-features/procedures/extension-methods.md) tak, že můžete volat, jakoby byly členem <xref:System.String> třídy.

## <a name="creating-a-class-library-solution"></a>Vytvoření řešení knihovny tříd

Začněte vytvořením řešení pro váš projekt knihovny tříd a její související projekty. Řešení sady Visual Studio slouží pouze jako kontejner pro jeden nebo více projektů. Vytvoření řešení:

1. Na řádku nabídek sady Visual Studio, zvolte **souboru** > **nový** > **projektu**.

1. V **nový projekt** dialogového okna, rozbalte **ostatní typy projektů** uzel a vyberte možnost **řešení sady Visual Studio**. Název řešení "ClassLibraryProjects" a vyberte **OK** tlačítko.

   ![Dialogové okno nového projektu](./media/library-with-visual-studio/newproject.png)

## <a name="creating-the-class-library-project"></a>Vytvoření projektu knihovny tříd

Vytvoření projektu knihovny třídy:

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na **ClassLibraryProjects** řešení a v místní nabídce vyberte možnost **přidat** > **nový Projekt**.

1. V **přidat nový projekt** dialogového okna, rozbalte **jazyka Visual Basic** uzlu, vyberte **.NET Standard** uzel, za nímž následuje **knihovna tříd (.NET Standard)**  šablony projektu. V **název** textové pole, zadejte "StringLibrary" jako název projektu. Vyberte **OK** vytvořte projekt knihovny tříd.

   ![Přidání dialogového okna Nový projekt](./media/vb-library-with-visual-studio/libproject.png)

   Potom otevře se okno kódu ve vývojovém prostředí sady Visual Studio. 
 
   ![Visual Studio okno aplikace zobrazuje kód výchozí knihovny třídy šablony](./media/vb-library-with-visual-studio/stringlibrary.png)

1. Zkontrolujte, že knihovny, zaměřuje na správnou verzi .NET Standard. Klikněte pravým tlačítkem na projekt knihovny v **Průzkumníka řešení** windows, vyberte **vlastnosti**. **Cílová architektura** textovém poli se zobrazí, že jsme cílíte .NET Standard 2.0.

   ![Vlastnosti projektu pro knihovny tříd](./media/library-with-visual-studio/properties.png)

1. Také v **vlastnosti** dialogového okna, odstraňte text v **kořenový obor názvů** textového pole. Pro každý projekt jazyka Visual Basic automaticky vytvoří obor názvů, který odpovídá názvu projektu a jsou nadřazené položky tohoto oboru názvů všech oborů názvů definovaných v souborech zdrojového kódu. Chceme, aby k definování oboru nejvyšší úrovně s použitím [ `namespace` ](../../visual-basic/language-reference/statements/namespace-statement.md) – klíčové slovo.
  
1. Nahraďte kód v okně kód následujícím kódem a soubor uložte:

  [!CODE-vb[ClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   Knihovna tříd `UtilityLibraries.StringLibrary`, obsahuje metodu s názvem `StartsWithUpper`, který vrátí hodnotu <xref:System.Boolean> hodnotu, která určuje, zda aktuální instance řetězec začíná velkým písmenem. Unicode standard rozlišuje velká písmena z malých písmen. <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> Vrátí metoda `true` Pokud znak je velké písmeno.

1. Na panelu nabídek vyberte **sestavení** > **sestavit řešení**. Projekt by měl zkompiluje bez chyb.

   ![Podokno výstup zobrazuje, že sestavení bylo úspěšné](./media/library-with-visual-studio/buildsucceeds.png)



## <a name="next-step"></a>Další krok

Úspěšně jste vytvořili knihovnu. Protože nejsou volány kterékoliv z jeho metod, zatím nevíte, jestli funguje podle očekávání. Dalším krokem při vývoji vaší knihovny je testovat pomocí [projekt testů jednotek](testing-library-with-visual-studio.md).
