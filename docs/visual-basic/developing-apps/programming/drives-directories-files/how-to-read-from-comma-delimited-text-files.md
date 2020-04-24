---
title: 'Postupy: čtení z textových souborů s hodnotami oddělenými čárkou'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- reading text files [Visual Basic], comma-delimited
- text files [Visual Basic], reading
ms.assetid: a8413fe4-0dba-49c8-8692-44fb67a9ec4f
ms.openlocfilehash: 9b93893e2221b156b65ce8e945089269ea28c989
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74335065"
---
# <a name="how-to-read-from-comma-delimited-text-files-in-visual-basic"></a>Postupy: čtení z textových souborů s oddělovači ve formátu čárky v Visual Basic

`TextFieldParser` Objekt poskytuje způsob, jak snadno a efektivně analyzovat strukturované textové soubory, jako jsou protokoly. `TextFieldType` Vlastnost určuje, zda se jedná o soubor s oddělovači, nebo o pole s pevnou šířkou textu.  
  
### <a name="to-parse-a-comma-delimited-text-file"></a>Jak analyzovat textový soubor s oddělovači  
  
1. Vytvořte nový `TextFieldParser`. Následující kód vytvoří `TextFieldParser` pojmenované `MyReader` a otevře soubor. `test.txt`  
  
     [!code-vb[VbFileIORead#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#15)]  
  
2. Definujte `TextField` typ a oddělovač. Následující kód definuje `TextFieldType` vlastnost jako `Delimited` a oddělovač jako ",".  
  
     [!code-vb[VbFileIORead#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#16)]  
  
3. Projděte pole v souboru. Pokud jsou některé řádky poškozené, nahlaste chybu a pokračujte v analýze. Následující kód prochází souborem, zobrazením jednotlivých polí a vytvářením sestav pro všechna pole, která jsou formátována nesprávně.  
  
     [!code-vb[VbFileIORead#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#17)]  
  
4. Zavřete bloky `While` a `Using` v nástroji `End While` a `End Using`.  
  
     [!code-vb[VbFileIORead#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#18)]  
  
## <a name="example"></a>Příklad  

 Tento příklad čte ze souboru `test.txt`.  
  
 [!code-vb[VbFileIORead#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#19)]  
  
## <a name="robust-programming"></a>Robustní programování  

 Následující podmínky mohou způsobit výjimku:  
  
- Řádek nelze analyzovat pomocí zadaného formátu (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>). Zpráva o výjimce Určuje řádek, který způsobil výjimku, zatímco <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> vlastnost je přiřazena k textu obsaženému na řádku.  
  
- Zadaný soubor neexistuje (<xref:System.IO.FileNotFoundException>).  
  
- Částečně důvěryhodná situace, kdy uživatel nemá dostatečná oprávnění pro přístup k souboru. (<xref:System.Security.SecurityException>).  
  
- Cesta je příliš dlouhá (<xref:System.IO.PathTooLongException>).  
  
- Uživatel nemá dostatečná oprávnění pro přístup k souboru (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [Postupy: Čtení z textových souborů s pevnou šířkou](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)
- [Postupy: Čtení z textových souborů ve více formátech](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [Analýza textových souborů pomocí objektu TextFieldParser](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [Návod: Práce se soubory a adresáři v jazyce Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [Řešení potíží: Čtení z textových souborů a zápis do nich](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
