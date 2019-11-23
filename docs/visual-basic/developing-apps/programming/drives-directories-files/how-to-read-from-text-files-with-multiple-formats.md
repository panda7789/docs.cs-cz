---
title: 'Postupy: čtení z textových souborů s více formáty v Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- TextFieldParser object, reading from a file
- TextFieldType enumeration
- My.Computer.FileSystem.WriteAllText method, parsing structured text files
- WriteAllText method [Visual Basic], parsing structured text files
- PeekChars method [Visual Basic], determining format of text
- reading text files [Visual Basic], multiple formats
- I/O [Visual Basic], reading text files
- text files [Visual Basic], reading
ms.assetid: 8d185eb2-79ca-42cd-95a7-d3ff44a5a0f8
ms.openlocfilehash: dc726f7648c1c0a564594331023f03d20569d766
ms.sourcegitcommit: 878ca7550b653114c3968ef8906da2b3e60e3c7a
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736826"
---
# <a name="how-to-read-from-fext-files-with-multiple-formats-in-visual-basic"></a>Postupy: čtení ze souborů Fext s více formáty v Visual Basic

Objekt <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> poskytuje způsob, jak snadno a efektivně analyzovat strukturované textové soubory, jako jsou protokoly. Můžete zpracovat soubor s více formáty pomocí metody `PeekChars` k určení formátu každého řádku při analýze souboru.
  
### <a name="to-parse-a-text-file-with-multiple-formats"></a>Postup analýzy textového souboru s více formáty

1. Do projektu přidejte textový soubor s názvem *Testfile. txt* . Do textového souboru přidejte následující obsah:

    ```text
    Err  1001 Cannot access resource.
    Err  2014 Resource not found.
    Acc  10/03/2009User1      Administrator.
    Err  0323 Warning: Invalid access attempt.
    Acc  10/03/2009User2      Standard user.
    Acc  10/04/2009User2      Standard user.
    ```

2. Definujte očekávaný formát a formát použitý při hlášení chyby. Poslední položka v každém poli je-1, proto se předpokládá, že poslední pole má proměnlivou šířku. K tomu dochází, když je poslední položka v poli menší nebo rovna 0.

     [!code-vb[VbFileIORead#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#4)]

3. Vytvořte nový objekt <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> a definujte šířku a formát.

     [!code-vb[VbFileIORead#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#5)]

4. Procházejte řádky smyčkou a před čtením proveďte testování formátu.

     [!code-vb[VbFileIORead#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#6)]

5. Zapište do konzoly chyby.

     [!code-vb[VbFileIORead#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#7)]

## <a name="example"></a>Příklad

Následuje kompletní příklad, který čte ze souboru `testfile.txt`:

 [!code-vb[VbFileIORead#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#8)]

## <a name="robust-programming"></a>Robustní programování

Následující podmínky mohou způsobit výjimku:  
  
- Řádek nelze analyzovat pomocí zadaného formátu (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>). Zpráva výjimky Určuje řádek, který způsobil výjimku, zatímco vlastnost <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> je přiřazena k textu obsaženému na řádku.
- Zadaný soubor neexistuje (<xref:System.IO.FileNotFoundException>).
- Částečně důvěryhodná situace, kdy uživatel nemá dostatečná oprávnění pro přístup k souboru. (<xref:System.Security.SecurityException>).
- Cesta je příliš dlouhá (<xref:System.IO.PathTooLongException>).
- Uživatel nemá dostatečná oprávnění pro přístup k souboru (<xref:System.UnauthorizedAccessException>).

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.PeekChars%2A>
- <xref:Microsoft.VisualBasic.FileIO.MalformedLineException>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.EndOfData%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TextFieldType%2A>
- [Postupy: Čtení z textových souborů s oddělovačem čárkou](how-to-read-from-comma-delimited-text-files.md)
- [Postupy: Čtení z textových souborů s pevnou šířkou](how-to-read-from-fixed-width-text-files.md)
- [Analýza textových souborů pomocí objektu TextFieldParser](parsing-text-files-with-the-textfieldparser-object.md)
