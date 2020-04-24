---
title: 'Postupy: čtení z textových souborů s pevnou šířkou'
ms.date: 07/20/2015
helpviewer_keywords:
- fixed-width text file
- reading text files [Visual Basic], fixed-width
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- text files [Visual Basic], reading
ms.assetid: 99be5692-967a-4e85-993e-cd18139a5a69
ms.openlocfilehash: 3cea9bfe2388f0ca510b15cb020f899b81c4603c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334628"
---
# <a name="how-to-read-from-fixed-width-text-files-in-visual-basic"></a>Postupy: čtení z textových souborů s pevnou šířkou v Visual Basic

`TextFieldParser` Objekt poskytuje způsob, jak snadno a efektivně analyzovat strukturované textové soubory, jako jsou protokoly.  
  
 `TextFieldType` Vlastnost definuje, zda je analyzovaný soubor soubor s oddělovači nebo který má pole s pevnou šířkou textu. V textovém souboru s pevnou šířkou může mít pole na konci proměnlivou šířku. Chcete-li určit, že pole na konci má proměnnou Width, definujte ji tak, aby měla šířku menší nebo rovna nule.  
  
### <a name="to-parse-a-fixed-width-text-file"></a>Chcete-li analyzovat textový soubor s pevnou šířkou  
  
1. Vytvořte nový `TextFieldParser`. Následující kód vytvoří `TextFieldParser` pojmenované `Reader` a otevře soubor. `test.log`  
  
     [!code-vb[VbFileIORead#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#9)]  
  
2. Definujte `TextFieldType` vlastnost jako `FixedWidth`a definujte šířku a formát. Následující kód definuje sloupce textu; první je 5 znaků široké, druhý 10, třetí 11 a čtvrtá je proměnná Width.  
  
     [!code-vb[VbFileIORead#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#10)]  
  
3. Projděte pole v souboru. Pokud jsou některé řádky poškozené, nahlaste chybu a pokračujte v analýze.  
  
     [!code-vb[VbFileIORead#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#11)]  
  
4. Zavřete bloky `While` a `Using` v nástroji `End While` a `End Using`.  
  
     [!code-vb[VbFileIORead#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#12)]  
  
## <a name="example"></a>Příklad  

 Tento příklad čte ze souboru `test.log`.  
  
 [!code-vb[VbFileIORead#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#13)]  
  
## <a name="robust-programming"></a>Robustní programování  

 Následující podmínky mohou způsobit výjimku:  
  
- Řádek nelze analyzovat pomocí zadaného formátu (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>). Zpráva o výjimce Určuje řádek, který způsobil výjimku, zatímco <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> vlastnost je přiřazena k textu obsaženému na řádku.  
  
- Zadaný soubor neexistuje (<xref:System.IO.FileNotFoundException>).  
  
- Částečně důvěryhodná situace, kdy uživatel nemá dostatečná oprávnění pro přístup k souboru. (<xref:System.Security.SecurityException>).  
  
- Cesta je příliš dlouhá (<xref:System.IO.PathTooLongException>).  
  
- Uživatel nemá dostatečná oprávnění pro přístup k souboru (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [Postupy: Čtení z textových souborů s oddělovači](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [Postupy: Čtení z textových souborů ve více formátech](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [Analýza textových souborů pomocí objektu TextFieldParser](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [Návod: Práce se soubory a adresáři v jazyce Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [Řešení potíží: Čtení z textových souborů a zápis do nich](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
