---
title: Vytvoření knihovny tříd .NET Standard v sadě Visual Studio
description: Zjistěte, jak vytvořit knihovnu tříd .NET Standard napsanou v jazyce C# nebo Visual Basic pomocí sady Visual Studio
ms.date: 12/09/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 748a1499e0c3a4a41613a69b715dbcfbd585bfe3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714009"
---
# <a name="build-a-net-standard-library-in-visual-studio"></a>Vytvoření knihovny .NET Standard v sadě Visual Studio

*Knihovna tříd* definuje typy a metody, které jsou volány aplikací. Knihovna tříd, která cílí na rozhraní .NET Standard 2.0, umožňuje, aby byla vaše knihovna volána libovolnou implementací rozhraní .NET, která tuto verzi rozhraní .NET Standard podporuje. Po dokončení knihovny tříd se můžete rozhodnout, zda ji chcete distribuovat jako komponentu jiného výrobce nebo zda ji chcete zahrnout jako sdruženou komponentu s jednou nebo více aplikacemi.

> [!NOTE]
> Seznam verzí rozhraní .NET Standard a platforem, které podporují, naleznete v tématu [.NET Standard](../../standard/net-standard.md).

V tomto tématu vytvoříte jednoduchou knihovnu nástrojů, která obsahuje jednu metodu zpracování řetězců. Budete implementovat jako [metodu rozšíření,](../../csharp/programming-guide/classes-and-structs/extension-methods.md) takže můžete volat, jako kdyby <xref:System.String> byl členem třídy.

## <a name="create-a-visual-studio-solution"></a>Vytvoření řešení sady Visual Studio

Začněte vytvořením prázdného řešení pro vložení projektu knihovny tříd. Řešení visual studio slouží jako kontejner pro jeden nebo více projektů. Přidáte další související projekty do stejného řešení, pokud budete pokračovat v sérii kurzů.

Chcete-li vytvořit prázdné řešení:

1. Otevřete sadu Visual Studio.

2. V počátečním okně zvolte **Vytvořit nový projekt**.

3. Na stránce **Vytvořit nový projekt** zadejte **řešení** do vyhledávacího pole. Zvolte šablonu **Prázdné řešení** a pak zvolte **Další**.

   ![Prázdná šablona řešení v sadě Visual Studio](media/library-with-visual-studio/blank-solution.png)

4. Na stránce **Konfigurovat nový projekt** zadejte do pole Název **projektu** **projektprojektprojekt.** Potom zvolte **Vytvořit**.

> [!TIP]
> Tento krok můžete také přeskočit a nechat Visual Studio vytvořit řešení pro vás při vytváření projektu v dalším kroku. Na stránce **Konfigurace nového projektu vyhledejte** možnosti řešení.

## <a name="create-a-class-library-project"></a>Vytvoření projektu knihovny tříd

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[C #](#tab/csharp)

1. Přidejte do řešení nový projekt knihovny tříd C#.

   1. Klikněte pravým tlačítkem myši na řešení v **Průzkumníku řešení** a vyberte **Přidat** > **nový projekt**.

   1. Na stránce **Přidat nový projekt** zadejte **knihovnu** do vyhledávacího pole. Ze seznamu Jazyk zvolte **C#** a pak ze seznamu Platforma zvolte **Všechny platformy.** Zvolte **šablonu Knihovna tříd (.NET Standard)** a pak zvolte **Další**.

   1. Na stránce **Konfigurovat nový projekt** zadejte **StringLibrary** do pole **Název projektu.** Potom zvolte **Vytvořit**.

1. Zkontrolujte, zda knihovna cílí na správnou verzi standardu .NET. Klepněte pravým tlačítkem myši na projekt knihovny v **Průzkumníku řešení**a vyberte příkaz **Vlastnosti**. Textové pole **Cílová architektura** ukazuje, že projekt cílí na standard .NET Standard 2.0.

   ![Vlastnosti projektu pro knihovnu tříd](./media/library-with-visual-studio/library-project-properties.png)

1. Nahraďte kód v okně kódu následujícím kódem a uložte soubor:

   [!CODE-csharp[ClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]

   Knihovna tříd `UtilityLibraries.StringLibrary`, obsahuje `StartsWithUpper`metodu s názvem . Tato metoda <xref:System.Boolean> vrátí hodnotu, která označuje, zda aktuální instance řetězce začíná velkým znakem. Standard Unicode rozlišuje velká písmena od malých písmen. Metoda <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> vrátí, `true` pokud znak je velká písmena.

1. Na řádku nabídek vyberte **Build** > **Build Build Solution**.

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

1. Přidejte do řešení nový projekt knihovny tříd visual basic .NET Standard s názvem "StringLibrary".

   1. Klikněte pravým tlačítkem myši na řešení v **Průzkumníku řešení** a vyberte **Přidat** > **nový projekt**.

   1. Na stránce **Přidat nový projekt** zadejte **knihovnu** do vyhledávacího pole. V seznamu Jazyk **zvolte Visual Basic** a pak ze seznamu Platforma zvolte **Všechny platformy.** Zvolte **šablonu Knihovna tříd (.NET Standard)** a pak zvolte **Další**.

   1. Na stránce **Konfigurovat nový projekt** zadejte **StringLibrary** do pole **Název projektu.** Potom zvolte **Vytvořit**.

1. Zkontrolujte, zda knihovna cílí na správnou verzi standardu .NET. Klepněte pravým tlačítkem myši na projekt knihovny v **Průzkumníku řešení**a vyberte příkaz **Vlastnosti**. Textové pole **Cílová architektura** ukazuje, že projekt cílí na standard .NET Standard 2.0.

   ![Vlastnosti projektu pro knihovnu tříd](./media/library-with-visual-studio/vb/library-project-properties.png)

1. V dialogovém okně **Vlastnosti** vymažte text v textovém poli **Kořenový jmenovcí obor.** Pro každý projekt visual basic automaticky vytvoří obor názvů, který odpovídá názvu projektu. V tomto kurzu definujete obor názvů nejvyšší [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) úrovně pomocí klíčového slova v souboru kódu.

1. Nahraďte kód v okně kódu následujícím kódem a uložte soubor:

   [!CODE-vb[ClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   Knihovna tříd `UtilityLibraries.StringLibrary`, obsahuje `StartsWithUpper`metodu s názvem . Tato metoda <xref:System.Boolean> vrátí hodnotu, která označuje, zda aktuální instance řetězce začíná velkým znakem. Standard Unicode rozlišuje velká písmena od malých písmen. Metoda <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> vrátí, `true` pokud znak je velká písmena.

1. Na řádku nabídek vyberte **Build** > **Build Build Solution**.

---

   Projekt by měl zkompilovat bez chyby.

## <a name="next-steps"></a>Další kroky

Úspěšně jste vytvořili knihovnu. Protože jste nevolali žádnou z jeho metod, nevíte, zda funguje podle očekávání. Dalším krokem při vývoji knihovny je otestovat.

> [!div class="nextstepaction"]
> [Vytvoření projektu pro testování částí](testing-library-with-visual-studio.md)
