---
title: Sestavení .NET Standard knihovny tříd Visual Basic v aplikaci Visual Studio 2017
description: Naučte se vytvářet .NET Standard knihovny tříd napsané v Visual Basic pomocí sady Visual Studio 2017
ms.date: 08/07/2017
dev_langs:
- vb
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 1daab377abe3b6b89f73ed48eafadeae4d7eee77
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73100870"
---
# <a name="build-a-net-standard-library-with-visual-basic-and-the-net-core-sdk-in-visual-studio-2017"></a>Sestavení knihovny .NET Standard s Visual Basic a .NET Core SDK v aplikaci Visual Studio 2017

*Knihovna tříd* definuje typy a metody, které jsou volány aplikací. Knihovna tříd, která cílí na .NET Standard 2,0, umožňuje, aby byla vaše knihovna volána jakoukoli implementací .NET, která podporuje tuto verzi .NET Standard. Po dokončení knihovny tříd se můžete rozhodnout, zda je chcete distribuovat jako součást třetí strany, nebo zda ji chcete zahrnout jako součást sady s jednou nebo více aplikacemi.

> [!NOTE]
> Seznam verzí .NET Standard a platforem, které podporují, najdete v tématu [.NET Standard](../../standard/net-standard.md).

V tomto tématu vytvoříte jednoduchou knihovnu nástrojů, která obsahuje jedinou metodu pro zpracování řetězců. Implementujete ho jako [metodu rozšíření](../../visual-basic/programming-guide/language-features/procedures/extension-methods.md) , takže ji můžete zavolat, jako kdyby byla členem třídy <xref:System.String>.

## <a name="creating-a-class-library-solution"></a>Vytvoření řešení knihovny tříd

Začněte vytvořením řešení pro projekt knihovny tříd a souvisejících projektů. Řešení sady Visual Studio slouží pouze jako kontejner pro jeden nebo více projektů. Postup vytvoření řešení:

1. Na panelu nabídek aplikace Visual Studio vyberte **soubor** > **Nový** > **projekt**.

1. V dialogovém okně **Nový projekt** rozbalte uzel **ostatní typy projektů** a vyberte **řešení sady Visual Studio**. Pojmenujte řešení "ClassLibraryProjects" a vyberte tlačítko **OK** .

   ![Dialog pro vytvoření nového testovacího projektu v aplikaci Visual Studio](./media/library-with-visual-studio/new-project-dialog.png)

## <a name="creating-the-class-library-project"></a>Vytvoření projektu knihovny tříd

Vytvořte projekt knihovny tříd:

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na soubor řešení **ClassLibraryProjects** a z místní nabídky vyberte **Přidat** > **Nový projekt**.

1. V dialogovém okně **Přidat nový projekt** rozbalte uzel **Visual Basic** a pak vyberte **.NET Standard** uzel následovaný šablonou projektu **Knihovna tříd (.NET Standard)** . Do textového pole **název** zadejte "StringLibrary" jako název projektu. Vyberte **OK** a vytvořte projekt knihovny tříd.

   ![Dialogové okno Přidat nový projekt knihovny pro Visual Studio](./media/vb-library-with-visual-studio/create-new-library-project.png)

   Okno Code (kód) se pak otevře ve vývojovém prostředí sady Visual Studio. 
 
   ![Okno aplikace sady Visual Studio zobrazující výchozí kód šablony knihovny tříd](./media/vb-library-with-visual-studio/visual-studio-library.png)

1. Zkontrolujte, zda je knihovna cílena na správnou verzi .NET Standard. V **Průzkumník řešení** oknech klikněte pravým tlačítkem na projekt knihovny a pak vyberte **vlastnosti**. Textové pole **cílové rozhraní** uvádí, že cílíme na .NET Standard 2,0.

   ![Vlastnosti projektu pro knihovnu tříd](./media/library-with-visual-studio/library-project-properties.png)

1. V dialogovém okně **vlastnosti** také vymažte text v textovém poli **kořenový obor názvů** . Pro každý projekt Visual Basic automaticky vytvoří obor názvů, který odpovídá názvu projektu, a všechny obory názvů definované v souborech zdrojového kódu jsou rodičem tohoto oboru názvů. Chceme definovat obor názvů nejvyšší úrovně pomocí klíčového slova [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) .
  
1. Kód v okně kód nahraďte následujícím kódem a uložte soubor:

  [!CODE-vb[ClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   Knihovna tříd, `UtilityLibraries.StringLibrary`, obsahuje metodu s názvem `StartsWithUpper`, která vrací <xref:System.Boolean> hodnotu, která označuje, zda aktuální instance řetězce začíná velkým znakem. Standard Unicode rozlišuje velká písmena od malých písmen. Metoda <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> vrátí `true`, pokud je znak velkými písmeny.

1. Na panelu nabídek vyberte **sestavení** **řešení**Build > . Projekt by měl být zkompilován bez chyby.

   ![Podokno výstup ukazující, že sestavení bylo úspěšné](./media/library-with-visual-studio/output-pane-successful-build.png)

## <a name="next-step"></a>Další krok

Úspěšně jste vytvořili knihovnu. Vzhledem k tomu, že jste nevolali žádnou z jeho metod, nevíte, zda funguje podle očekávání. Dalším krokem při vývoji knihovny je testování pomocí [projektu testování částí](testing-library-with-visual-studio.md).
