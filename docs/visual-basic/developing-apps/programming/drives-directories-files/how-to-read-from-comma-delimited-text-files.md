---
title: 'Postupy: čtení z oddělených čárkou textových souborů v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- reading text files [Visual Basic], comma-delimited
- text files [Visual Basic], reading
ms.assetid: a8413fe4-0dba-49c8-8692-44fb67a9ec4f
ms.openlocfilehash: 8b9faaad2abaa0d551304ff03f8212bd535eda58
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623206"
---
# <a name="how-to-read-from-comma-delimited-text-files-in-visual-basic"></a>Postupy: čtení z oddělených čárkou textových souborů v jazyce Visual Basic
`TextFieldParser` Objekt poskytuje způsob, jak snadno a efektivně analýza strukturovaných textových souborů, jako jsou protokoly. `TextFieldType` Vlastnost definuje, zda je soubor s oddělovači nebo s pevnou šířkou textových polí.  
  
### <a name="to-parse-a-comma-delimited-text-file"></a>Analyzovat čárku textový soubor s oddělovači  
  
1. Vytvořte nový `TextFieldParser`. Následující kód vytvoří `TextFieldParser` s názvem `MyReader` a otevře soubor `test.txt`.  
  
     [!code-vb[VbFileIORead#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#15)]  
  
2. Definovat `TextField` typu a oddělovač. Následující kód definuje `TextFieldType` vlastnost jako `Delimited` a oddělovač jako ",".  
  
     [!code-vb[VbFileIORead#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#16)]  
  
3. Projít polí v souboru. Pokud jsou řádky poškozený, ohlaste chybu a mohlo pokračovat s analýzou. Následující kód prochází soubor, pak zobrazení jednotlivých polí a vytváření sestav všechna pole, která jsou v nesprávném formátu.  
  
     [!code-vb[VbFileIORead#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#17)]  
  
4. Zavřít `While` a `Using` blokuje s `End While` a `End Using`.  
  
     [!code-vb[VbFileIORead#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#18)]  
  
## <a name="example"></a>Příklad  
 V tomto příkladu načteme soubor `test.txt`.  
  
 [!code-vb[VbFileIORead#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#19)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
- Řádek nelze analyzovat pomocí určeného formátu (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>). Zpráva o výjimce určuje řádek, který způsobil výjimku, a <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> vlastnost je přiřazena obsažené v řádku textu.  
  
- Zadaný soubor neexistuje (<xref:System.IO.FileNotFoundException>).  
  
- Stav částečným vztahem důvěryhodnosti, ve kterém uživatel nemá dostatečná oprávnění pro přístup k souboru. (<xref:System.Security.SecurityException>).  
  
- Cesta je příliš dlouhá (<xref:System.IO.PathTooLongException>).  
  
- Uživatel nemá dostatečná oprávnění pro přístup k souboru (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [Postupy: Čtení z souborů s pevnou šířkou](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)
- [Postupy: Čtení z textových souborů ve více formátech](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [Analýza textových souborů pomocí objektu TextFieldParser](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [Návod: Práce se soubory a adresáře v jazyce Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [Odstraňování potíží: Čtení a zápis do textových souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
