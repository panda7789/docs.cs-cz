---
title: Použití pojmenovaných a volitelných argumentů v programovacím programu sady Office – Průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- named and optional arguments [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
ms.assetid: 65b8a222-bcd8-454c-845f-84adff5a356f
ms.openlocfilehash: 36b5c8b49404606c8240d24953c3677d5612d30e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714879"
---
# <a name="how-to-use-named-and-optional-arguments-in-office-programming-c-programming-guide"></a>Použití pojmenovaných a volitelných argumentů v programování sady Office (Průvodce programováním jazyka C#)

Pojmenované argumenty a volitelné argumenty, zavedené v jazyce C# 4, zvyšují pohodlí, flexibilitu a čitelnost v programování jazyka C#. Kromě toho tyto funkce výrazně usnadňují přístup k rozhraním COM, jako jsou rozhraní API automatizace sady Microsoft Office.

V následujícím příkladu má metoda [ConvertToTable](<xref:Microsoft.Office.Interop.Word.Range.ConvertToTable%2A>) šestnáct parametrů, které představují charakteristiky tabulky, například počet sloupců a řádků, formátování, ohraničení, písma a barvy. Všech šestnáct parametrů je volitelných, protože většinu času nechcete určit konkrétní hodnoty pro všechny z nich. Bez pojmenovaných a volitelných argumentů však musí být pro každý parametr poskytnuta hodnota nebo zástupná hodnota. S pojmenovanými a volitelnými argumenty zadáte hodnoty pouze pro parametry, které jsou požadovány pro váš projekt.

K dokončení těchto postupů je třeba mít v počítači nainstalovanou aplikaci Microsoft Office Word.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-new-console-application"></a>Vytvoření nové konzolové aplikace

1. Spusťte Visual Studio.

2. V nabídce **Soubor** přejděte na **Nový**a potom klepněte na **položku Project**.

3. V podokně **Kategorie šablon** rozbalte **položku Visual C#** a klepněte na tlačítko **Windows**.

4. V horní části podokna **Šablony** se ujistěte, že se rozhraní **.NET Framework 4** zobrazí v poli **Cílová architektura.**

5. V podokně **Šablony** klepněte na položku **Konzolová aplikace**.

6. Do pole **Název** zadejte název projektu.

7. Klikněte na tlačítko **OK**.

     Nový projekt se zobrazí v **Průzkumníku řešení**.

## <a name="to-add-a-reference"></a>Přidání odkazu

1. V **Průzkumníku řešení**klikněte pravým tlačítkem myši na název projektu a potom klikněte na **příkaz Přidat odkaz**. Zobrazí se dialogové okno **Přidat odkaz.**

2. Na stránce **.NET** vyberte v seznamu **Název součásti** **položku Microsoft.Office.Interop.Word.**

3. Klikněte na tlačítko **OK**.

## <a name="to-add-necessary-using-directives"></a>Chcete-li přidat nezbytné pomocí směrnic

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na *soubor Program.cs* a potom klepněte na příkaz Zobrazit **kód**.

2. Do horní `using` části souboru kódu přidejte následující direktivy:

     [!code-csharp[csProgGuideNamedAndOptional#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#4)]

## <a name="to-display-text-in-a-word-document"></a>Zobrazení textu ve wordovém dokumentu

1. Do `Program` třídy v *Program.cs*přidejte následující metodu k vytvoření aplikace Word a dokumentu aplikace Word. Metoda [Add](<xref:Microsoft.Office.Interop.Word.Documents.Add%2A>) má čtyři volitelné parametry. Tento příklad používá jejich výchozí hodnoty. Proto žádné argumenty jsou nezbytné v volání příkazu.

     [!code-csharp[csProgGuideNamedAndOptional#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#6)]

2. Na konec metody přidejte následující kód, který definuje, kde se má v dokumentu zobrazit text a jaký text se má zobrazit:

     [!code-csharp[csProgGuideNamedAndOptional#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#7)]

## <a name="to-run-the-application"></a>Spuštění aplikace

1. Do hlavního příkazu přidejte následující příkaz:

     [!code-csharp[csProgGuideNamedAndOptional#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#8)]

2. Spuštění projektu stisknutím <kbd>klávesy CTRL</kbd>+<kbd>F5.</kbd> Zobrazí se dokument aplikace Word, který obsahuje zadaný text.

## <a name="to-change-the-text-to-a-table"></a>Změna textu na tabulku
  
1. Pomocí `ConvertToTable` metody uzavřete text do tabulky. Metoda má šestnáct volitelných parametrů. Technologie IntelliSense uzavře volitelné parametry do závorek, jak je znázorněno na následujícím obrázku.

     ![Seznam parametrů pro metodu ConvertToTable](./media/how-to-use-named-and-optional-arguments-in-office-programming/convert-table-parameters.png)

     Pojmenované a volitelné argumenty umožňují zadat hodnoty pouze pro parametry, které chcete změnit. Přidejte následující kód na `DisplayInWord` konec metody a vytvořte jednoduchou tabulku. Argument určuje, že čárky v textovém `range` řetězci v samostatné buňky tabulky.

     [!code-csharp[csProgGuideNamedAndOptional#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#9)]

     V dřívějších verzích jazyka C# `ConvertToTable` vyžaduje volání pro každý parametr referenční argument, jak je znázorněno v následujícím kódu:
  
     [!code-csharp[csProgGuideNamedAndOptional#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#14)]

2. Spuštění projektu stisknutím <kbd>klávesy CTRL</kbd>+<kbd>F5.</kbd>

## <a name="to-experiment-with-other-parameters"></a>Experimentovat s dalšími parametry

1. Chcete-li tabulku změnit tak, aby byla mít jeden `DisplayInWord` sloupec a tři řádky, nahraďte poslední řádek v tabulce následujícím příkazem a zadejte <kbd>kombinaci kláves CTRL</kbd>+<kbd>F5</kbd>.  

     [!code-csharp[csProgGuideNamedAndOptional#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#10)]

2. Chcete-li určit předdefinovaný formát tabulky, nahraďte poslední řádek v s `DisplayInWord` následujícím příkazem a zadejte <kbd>kombinaci kláves CTRL</kbd>+<kbd>F5</kbd>. Formát může být libovolná z konstant [WdTableFormat.](<xref:Microsoft.Office.Interop.Word.WdTableFormat>)

     [!code-csharp[csProgGuideNamedAndOptional#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#11)]

## <a name="example"></a>Příklad

Následující kód obsahuje úplný příklad:

 [!code-csharp[csProgGuideNamedAndOptional#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#12)]

## <a name="see-also"></a>Viz také

- [Pojmenované a nepovinné argumenty](./named-and-optional-arguments.md)
