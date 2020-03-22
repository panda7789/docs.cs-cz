---
title: 'Postup: Čtení z textových souborů s více formáty'
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
ms.openlocfilehash: b36c781d5f8333749d346bb8f19540f0d1bd1692
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334575"
---
# <a name="how-to-read-from-fext-files-with-multiple-formats-in-visual-basic"></a>Postup: Čtení ze souborů fext s více formáty v jazyce Visual Basic

Objekt <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> poskytuje způsob, jak snadno a efektivně analyzovat strukturované textové soubory, jako jsou například protokoly. Soubor s více formáty můžete zpracovat pomocí `PeekChars` metody k určení formátu každého řádku při analýzě souboru.
  
### <a name="to-parse-a-text-file-with-multiple-formats"></a>Analýza textového souboru s více formáty

1. Přidejte do projektu textový soubor s názvem *testfile.txt.* Do textového souboru přidejte následující obsah:

    ```text
    Err  1001 Cannot access resource.
    Err  2014 Resource not found.
    Acc  10/03/2009User1      Administrator.
    Err  0323 Warning: Invalid access attempt.
    Acc  10/03/2009User2      Standard user.
    Acc  10/04/2009User2      Standard user.
    ```

2. Definujte očekávaný formát a formát použitý při nakazení chyby. Poslední položka v každém poli je -1, proto se předpokládá, že poslední pole má proměnnou šířku. K tomu dochází, když poslední položka v poli je menší nebo rovna 0.

     [!code-vb[VbFileIORead#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#4)]

3. Vytvořte <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> nový objekt, který definuje šířku a formát.

     [!code-vb[VbFileIORead#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#5)]

4. Smyčka přes řádky, testování formátu před čtením.

     [!code-vb[VbFileIORead#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#6)]

5. Zápis chyb do konzoly.

     [!code-vb[VbFileIORead#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#7)]

## <a name="example"></a>Příklad

Následuje úplný příklad, který čte `testfile.txt`ze souboru :

 [!code-vb[VbFileIORead#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#8)]

## <a name="robust-programming"></a>Robustní programování

Následující podmínky mohou způsobit výjimku:  
  
- Řádek nelze analyzovat pomocí zadaného formátu<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>( ). Zpráva o výjimce určuje řádek způsobující <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> výjimku, zatímco vlastnost je přiřazena k textu obsaženému v řádku.
- Zadaný soubor neexistuje<xref:System.IO.FileNotFoundException>( ).
- Situace částečné důvěryhodnosti, ve které uživatel nemá dostatečná oprávnění pro přístup k souboru. (<xref:System.Security.SecurityException>).
- Cesta je příliš<xref:System.IO.PathTooLongException>dlouhá ( ).
- Uživatel nemá dostatečná oprávnění pro přístup<xref:System.UnauthorizedAccessException>k souboru ( ).

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.PeekChars%2A>
- <xref:Microsoft.VisualBasic.FileIO.MalformedLineException>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.EndOfData%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TextFieldType%2A>
- [Postupy: Čtení z textových souborů s oddělovači](how-to-read-from-comma-delimited-text-files.md)
- [Postupy: Čtení z textových souborů s pevnou šířkou](how-to-read-from-fixed-width-text-files.md)
- [Analýza textových souborů pomocí objektu TextFieldParser](parsing-text-files-with-the-textfieldparser-object.md)
