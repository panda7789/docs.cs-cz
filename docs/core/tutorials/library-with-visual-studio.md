---
title: Sestavení knihovny tříd .NET Standard v aplikaci Visual Studio
description: Naučte se vytvářet .NET Standard knihovny tříd napsané v C# nebo Visual Basic pomocí sady Visual Studio.
ms.date: 12/09/2019
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 160993a4dd40356cde541616a1f15f87712e8ae2
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75343118"
---
# <a name="build-a-net-standard-library-in-visual-studio"></a>Sestavení knihovny .NET Standard v aplikaci Visual Studio

*Knihovna tříd* definuje typy a metody, které jsou volány aplikací. Knihovna tříd, která cílí na .NET Standard 2,0, umožňuje, aby byla vaše knihovna volána jakoukoli implementací .NET, která podporuje tuto verzi .NET Standard. Po dokončení knihovny tříd se můžete rozhodnout, zda je chcete distribuovat jako součást třetí strany, nebo zda ji chcete zahrnout jako součást sady s jednou nebo více aplikacemi.

> [!NOTE]
> Seznam verzí .NET Standard a platforem, které podporují, najdete v tématu [.NET Standard](../../standard/net-standard.md).

V tomto tématu vytvoříte jednoduchou knihovnu nástrojů, která obsahuje jedinou metodu pro zpracování řetězců. Implementujete ho jako [metodu rozšíření](../../csharp/programming-guide/classes-and-structs/extension-methods.md) , takže ji můžete zavolat, jako kdyby byla členem třídy <xref:System.String>.

## <a name="create-a-visual-studio-solution"></a>Vytvoření řešení pro Visual Studio

Začněte vytvořením prázdného řešení pro vložení projektu knihovny tříd do. Řešení sady Visual Studio slouží jako kontejner pro jeden nebo více projektů. Další související projekty přidáte do stejného řešení, pokud budete pokračovat s řadou kurzů.

Vytvoření prázdného řešení:

1. Otevřít Visual Studio.

2. V okně Start vyberte možnost **vytvořit nový projekt**.

3. Na stránce **vytvořit nový projekt** zadejte do vyhledávacího pole **řešení** . Zvolte šablonu **prázdného řešení** a klikněte na tlačítko **Další**.

   ![Šablonu prázdného řešení v sadě Visual Studio](media/library-with-visual-studio/blank-solution.png)

4. Na stránce **Konfigurovat nový projekt** zadejte do pole **název projektu** **ClassLibraryProjects** . Pak zvolte **vytvořit**.

> [!TIP]
> Tento krok můžete také přeskočit a nechat si Visual Studio vytvořit řešení při vytváření projektu v dalším kroku. Vyhledejte možnosti řešení na stránce **Konfigurovat nový projekt** .

## <a name="create-a-class-library-project"></a>Vytvořit projekt knihovny tříd

<!-- markdownlint-disable MD025 -->

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. Přidejte do řešení C# nový projekt knihovny tříd .NET Standard s názvem "StringLibrary".

   1. V **Průzkumník řešení** klikněte pravým tlačítkem na řešení a vyberte **Přidat** > **Nový projekt**.

   1. Na stránce **Přidat nový projekt** zadejte do vyhledávacího pole **Library** . Vyberte **C#** ze seznamu jazyk a v seznamu platforma zvolte možnost **všechny platformy** . Zvolte šablonu **Knihovna tříd (.NET Standard)** a klikněte na tlačítko **Další**.

   1. Na stránce **Konfigurovat nový projekt** zadejte do pole **název projektu** **StringLibrary** . Pak zvolte **vytvořit**.

1. Zkontrolujte, zda je knihovna cílena na správnou verzi .NET Standard. V **Průzkumník řešení**klikněte pravým tlačítkem na projekt knihovny a pak vyberte **vlastnosti**. Textové pole **cílové rozhraní** uvádí, že cíle projektu .NET Standard 2,0.

   ![Vlastnosti projektu pro knihovnu tříd](./media/library-with-visual-studio/library-project-properties.png)

1. Kód v okně kód nahraďte následujícím kódem a uložte soubor:

   [!CODE-csharp[ClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]

   Knihovna tříd, `UtilityLibraries.StringLibrary`, obsahuje metodu s názvem `StartsWithUpper`. Tato metoda vrací hodnotu <xref:System.Boolean>, která označuje, zda aktuální instance řetězce začíná velkým znakem. Standard Unicode rozlišuje velká písmena od malých písmen. Metoda <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> vrátí `true`, pokud je znak velkými písmeny.

1. Na panelu nabídek vyberte **sestavení** **řešení**Build > .

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. Přidejte do řešení nový projekt knihovny tříd Visual Basic .NET Standard s názvem "StringLibrary".

   1. V **Průzkumník řešení** klikněte pravým tlačítkem na řešení a vyberte **Přidat** > **Nový projekt**.

   1. Na stránce **Přidat nový projekt** zadejte do vyhledávacího pole **Library** . V seznamu jazyk vyberte možnost **Visual Basic** a v seznamu platforma zvolte možnost **všechny platformy** . Zvolte šablonu **Knihovna tříd (.NET Standard)** a klikněte na tlačítko **Další**.

   1. Na stránce **Konfigurovat nový projekt** zadejte do pole **název projektu** **StringLibrary** . Pak zvolte **vytvořit**.

1. Zkontrolujte, zda je knihovna cílena na správnou verzi .NET Standard. V **Průzkumník řešení**klikněte pravým tlačítkem na projekt knihovny a pak vyberte **vlastnosti**. Textové pole **cílové rozhraní** uvádí, že cíle projektu .NET Standard 2,0.

   ![Vlastnosti projektu pro knihovnu tříd](./media/library-with-visual-studio/vb/library-project-properties.png)

1. V dialogovém okně **vlastnosti** vymažte text v textovém poli **kořenový obor názvů** . Pro každý projekt Visual Basic automaticky vytvoří obor názvů, který odpovídá názvu projektu. V tomto kurzu definujete obor názvů nejvyšší úrovně pomocí klíčového slova [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) v souboru kódu.

1. Kód v okně kód nahraďte následujícím kódem a uložte soubor:

   [!CODE-vb[ClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   Knihovna tříd, `UtilityLibraries.StringLibrary`, obsahuje metodu s názvem `StartsWithUpper`. Tato metoda vrací hodnotu <xref:System.Boolean>, která označuje, zda aktuální instance řetězce začíná velkým znakem. Standard Unicode rozlišuje velká písmena od malých písmen. Metoda <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> vrátí `true`, pokud je znak velkými písmeny.

1. Na panelu nabídek vyberte **sestavení** **řešení**Build > .

---

   Projekt by měl být zkompilován bez chyby.

## <a name="next-steps"></a>Další kroky

Úspěšně jste vytvořili knihovnu. Vzhledem k tomu, že jste nevolali žádnou z jeho metod, nevíte, zda funguje podle očekávání. Dalším krokem při vývoji knihovny je testování.

> [!div class="nextstepaction"]
> [Vytvoření projektu pro testování částí](testing-library-with-visual-studio.md)
