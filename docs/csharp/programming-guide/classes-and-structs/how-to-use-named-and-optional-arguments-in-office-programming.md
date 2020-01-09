---
title: Použití pojmenovaných a nepovinných argumentů v programování C# pro systém Office – Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- named and optional arguments [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
ms.assetid: 65b8a222-bcd8-454c-845f-84adff5a356f
ms.openlocfilehash: 36b5c8b49404606c8240d24953c3677d5612d30e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714879"
---
# <a name="how-to-use-named-and-optional-arguments-in-office-programming-c-programming-guide"></a>Použití pojmenovaných a nepovinných argumentů v programováníC# pro systém Office (Průvodce programováním)

Pojmenované argumenty a volitelné argumenty, představené C# ve 4, zvyšují pohodlí, flexibilitu a čitelnost při C# programování. Kromě toho tyto funkce významně usnadňují přístup k rozhraním COM, jako jsou systém Microsoft Office rozhraní API pro automatizaci.

V následujícím příkladu má metoda [ConvertToTable](<xref:Microsoft.Office.Interop.Word.Range.ConvertToTable%2A>) šestnáct parametrů, které reprezentují vlastnosti tabulky, jako je počet sloupců a řádků, formátování, ohraničení, písma a barvy. Všechny šestnácté parametry jsou volitelné, protože většina času neumožňuje zadat konkrétní hodnoty pro všechny. Bez pojmenovaných a nepovinných argumentů však musí být pro každý parametr zadána hodnota nebo zástupný symbol. U pojmenovaných a nepovinných argumentů zadáte hodnoty pouze pro parametry, které jsou požadovány pro váš projekt.

Aby bylo možné dokončit tyto postupy, je nutné, aby byl v počítači nainstalován systém Microsoft Office Word.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-new-console-application"></a>Vytvoření nové konzolové aplikace

1. Spusťte Visual Studio.

2. V nabídce **soubor** přejděte na příkaz **Nový**a klikněte na **projekt**.

3. V podokně **Kategorie šablon** rozbalte položku **vizuál C#** a potom klikněte na možnost **Windows**.

4. Podívejte se v horní části podokna **šablony** , abyste se ujistili, že se v poli **cílová architektura** zobrazí **.NET Framework 4** .

5. V podokně **šablony** klikněte na **Konzolová aplikace**.

6. Do pole **název** zadejte název projektu.

7. Klikněte na tlačítko **OK**.

     Nový projekt se zobrazí v **Průzkumník řešení**.

## <a name="to-add-a-reference"></a>Přidání odkazu

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na název projektu a pak klikněte na **Přidat odkaz**. Zobrazí se dialogové okno **Přidat odkaz** .

2. Na stránce **.NET** vyberte v seznamu **název součásti** možnost **Microsoft. Office. Interop. Word** .

3. Klikněte na tlačítko **OK**.

## <a name="to-add-necessary-using-directives"></a>Přidání nezbytných direktiv using

1. V **Průzkumník řešení**klikněte pravým tlačítkem na soubor *program.cs* a pak klikněte na **Zobrazit kód**.

2. Do horní části souboru kódu přidejte následující direktivy `using`:

     [!code-csharp[csProgGuideNamedAndOptional#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#4)]

## <a name="to-display-text-in-a-word-document"></a>Zobrazení textu v dokumentu aplikace Word

1. Do třídy `Program` v *program.cs*přidejte následující metodu pro vytvoření aplikace Word a wordového dokumentu. Metoda [Add](<xref:Microsoft.Office.Interop.Word.Documents.Add%2A>) má čtyři volitelné parametry. V tomto příkladu se používají výchozí hodnoty. Proto nejsou v příkazu call nutné žádné argumenty.

     [!code-csharp[csProgGuideNamedAndOptional#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#6)]

2. Na konec metody přidejte následující kód, který definuje, kde se má v dokumentu zobrazovat text, a zobrazený text:

     [!code-csharp[csProgGuideNamedAndOptional#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#7)]

## <a name="to-run-the-application"></a>Spuštění aplikace

1. Přidejte následující příkaz do Main:

     [!code-csharp[csProgGuideNamedAndOptional#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#8)]

2. Stisknutím <kbd>kombinace kláves CTRL</kbd>+<kbd>F5</kbd> spusťte projekt. Zobrazí se dokument aplikace Word obsahující zadaný text.

## <a name="to-change-the-text-to-a-table"></a>Změna textu na tabulku
  
1. K uzavření textu v tabulce použijte metodu `ConvertToTable`. Metoda má 16 nepovinných parametrů. IntelliSense vloží volitelné parametry do závorek, jak je znázorněno na následujícím obrázku.

     ![Seznam parametrů pro metodu ConvertToTable](./media/how-to-use-named-and-optional-arguments-in-office-programming/convert-table-parameters.png)

     Pojmenované a volitelné argumenty umožňují zadat hodnoty pouze pro parametry, které chcete změnit. Přidejte následující kód na konec metody `DisplayInWord` pro vytvoření jednoduché tabulky. Argument určuje, že čárky v textovém řetězci v `range` oddělují buňky tabulky.

     [!code-csharp[csProgGuideNamedAndOptional#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#9)]

     V dřívějších verzích C#nástroje volání `ConvertToTable` vyžaduje argument odkazu pro každý parametr, jak je znázorněno v následujícím kódu:
  
     [!code-csharp[csProgGuideNamedAndOptional#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#14)]

2. Stisknutím <kbd>kombinace kláves CTRL</kbd>+<kbd>F5</kbd> spusťte projekt.

## <a name="to-experiment-with-other-parameters"></a>Experimentování s jinými parametry

1. Chcete-li změnit tabulku tak, aby měla jeden sloupec a tři řádky, nahraďte poslední řádek v `DisplayInWord` následujícím příkazem a potom zadejte <kbd>CTRL</kbd>+<kbd>F5</kbd>.  

     [!code-csharp[csProgGuideNamedAndOptional#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#10)]

2. Chcete-li pro tabulku zadat předdefinovaný formát, nahraďte poslední řádek v `DisplayInWord` následujícím příkazem a zadejte <kbd>CTRL</kbd>+<kbd>F5</kbd>. Formát může být libovolná konstanta [WdTableFormat](<xref:Microsoft.Office.Interop.Word.WdTableFormat>) .

     [!code-csharp[csProgGuideNamedAndOptional#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#11)]

## <a name="example"></a>Příklad

Následující kód obsahuje úplný příklad:

 [!code-csharp[csProgGuideNamedAndOptional#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#12)]

## <a name="see-also"></a>Viz také:

- [Pojmenované a nepovinné argumenty](./named-and-optional-arguments.md)
