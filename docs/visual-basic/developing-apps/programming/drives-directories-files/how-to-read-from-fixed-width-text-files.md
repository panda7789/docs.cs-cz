---
title: 'Postup: čtení z textu s pevnou šířkou Soubory'
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
# <a name="how-to-read-from-fixed-width-text-files-in-visual-basic"></a>Postup: čtení z textových souborů s pevnou šířkou v jazyce Visual Basic

Objekt `TextFieldParser` poskytuje způsob, jak snadno a efektivně analyzovat strukturované textové soubory, jako jsou například protokoly.  
  
 Vlastnost `TextFieldType` definuje, zda je analyzovaný soubor soubor s oddělovačem nebo soubor, který má pole s pevnou šířkou textu. V textovém souboru s pevnou šířkou může mít pole na konci proměnnou šířku. Chcete-li určit, že pole na konci má proměnnou šířku, definujte ji tak, aby měla šířku menší nebo rovnou nule.  
  
### <a name="to-parse-a-fixed-width-text-file"></a>Analýza textového souboru s pevnou šířkou  
  
1. Vytvořte `TextFieldParser`nový . Následující kód vytvoří `TextFieldParser` `Reader` pojmenovaný a `test.log`otevře soubor .  
  
     [!code-vb[VbFileIORead#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#9)]  
  
2. Definujte `TextFieldType` vlastnost `FixedWidth`jako , definování šířky a formátu. Následující kód definuje sloupce textu; první je 5 znaků široký, druhý 10, třetí 11 a čtvrtý má proměnnou šířku.  
  
     [!code-vb[VbFileIORead#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#10)]  
  
3. Smyčka procházet pole v souboru. Pokud jsou některé řádky poškozeny, oznamte chybu a pokračujte v provádění analýzy.  
  
     [!code-vb[VbFileIORead#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#11)]  
  
4. Zavřete `While` `Using` bloky `End While` a `End Using`s a .  
  
     [!code-vb[VbFileIORead#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#12)]  
  
## <a name="example"></a>Příklad  

 Tento příklad čte `test.log`ze souboru .  
  
 [!code-vb[VbFileIORead#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#13)]  
  
## <a name="robust-programming"></a>Robustní programování  

 Následující podmínky mohou způsobit výjimku:  
  
- Řádek nelze analyzovat pomocí zadaného formátu<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>( ). Zpráva o výjimce určuje řádek způsobující <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> výjimku, zatímco vlastnost je přiřazena k textu obsaženému v řádku.  
  
- Zadaný soubor neexistuje<xref:System.IO.FileNotFoundException>( ).  
  
- Situace částečné důvěryhodnosti, ve které uživatel nemá dostatečná oprávnění pro přístup k souboru. (<xref:System.Security.SecurityException>).  
  
- Cesta je příliš<xref:System.IO.PathTooLongException>dlouhá ( ).  
  
- Uživatel nemá dostatečná oprávnění pro přístup<xref:System.UnauthorizedAccessException>k souboru ( ).  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [Postupy: Čtení z textových souborů s oddělovači](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [Postupy: Čtení z textových souborů ve více formátech](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [Analýza textových souborů pomocí objektu TextFieldParser](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [Návod: Práce se soubory a adresáři v jazyce Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [Řešení potíží: Čtení z textových souborů a zápis do nich](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
