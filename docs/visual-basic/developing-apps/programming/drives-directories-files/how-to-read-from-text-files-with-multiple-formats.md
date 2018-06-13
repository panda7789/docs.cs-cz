---
title: 'Postupy: Čtení z textových souborů ve více formátech v jazyce Visual Basic'
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
ms.openlocfilehash: 2c67e358e418ed8cbfddd9a8e7b03a60e46d6356
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33584869"
---
# <a name="how-to-read-from-text-files-with-multiple-formats-in-visual-basic"></a>Postupy: Čtení z textových souborů ve více formátech v jazyce Visual Basic
<xref:Microsoft.VisualBasic.FileIO.TextFieldParser> Objekt poskytuje způsob, jak snadno a efektivně analýza strukturovaných textových souborů, jako jsou protokoly. Soubor s více formátů může zpracovat pomocí `PeekChars` metoda k určení formátu každého řádku procházení souboru.  
  
### <a name="to-parse-a-text-file-with-multiple-formats"></a>Analyzovat textový soubor s více formátů  
  
1.  Přidejte textový soubor s názvem testfile.txt do projektu. Do textového souboru přidejte následující obsah.  
  
    ```  
    Err  1001 Cannot access resource.  
    Err  2014 Resource not found.  
    Acc  10/03/2009User1      Administrator.  
    Err  0323 Warning: Invalid access attempt.  
    Acc  10/03/2009User2      Standard user.  
    Acc  10/04/2009User2      Standard user.  
    ```  
  
2.  Definují očekávaný formát a formát použitý při hlášení chyby. Poslední položky v každé pole je -1, proto pole poslední předpokládá se, že proměnné šířky. K tomu dochází, pokud poslední položky v poli je menší než nebo rovna 0.  
  
     [!code-vb[VbFileIORead#4](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_1.vb)]  
  
3.  Vytvořte novou <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> objekt, definování šířky a formátu.  
  
     [!code-vb[VbFileIORead#5](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_2.vb)]  
  
4.  Projděte řádky, testování formát před čtením.  
  
     [!code-vb[VbFileIORead#6](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_3.vb)]  
  
5.  Chyby zápisu do konzoly.  
  
     [!code-vb[VbFileIORead#7](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_4.vb)]  
  
## <a name="example"></a>Příklad  
 Toto je kompletní příklad, který čte ze souboru `testfile.txt`.  
  
 [!code-vb[VbFileIORead#8](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_5.vb)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
-   Řádek nelze analyzovat pomocí zadaného formátu (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>). Zpráva o výjimce určuje řádek, který způsobil výjimku a <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> vlastnost je přiřazena k obsažené v řádku textu.  
  
-   Zadaný soubor neexistuje (<xref:System.IO.FileNotFoundException>).  
  
-   Stav částečným vztahem důvěryhodnosti, ve kterém uživatel nemá dostatečná oprávnění k přístupu k souboru. (<xref:System.Security.SecurityException>).  
  
-   Cesta je příliš dlouhá (<xref:System.IO.PathTooLongException>).  
  
-   Uživatel nemá dostatečná oprávnění k přístupu k souboru (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.PeekChars%2A>  
 <xref:Microsoft.VisualBasic.FileIO.MalformedLineException>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.EndOfData%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TextFieldType%2A>  
 [Postupy: Čtení z textových souborů s oddělovačem čárkou](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)  
 [Postupy: Čtení z textových souborů s pevnou šířkou](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)  
 [Analýza textových souborů pomocí objektu TextFieldParser](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
