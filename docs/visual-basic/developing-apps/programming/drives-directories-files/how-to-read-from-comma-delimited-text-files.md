---
title: 'Postup: čtení z textových souborů oddělených čárkami'
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
# <a name="how-to-read-from-comma-delimited-text-files-in-visual-basic"></a>Postup: čtení z textových souborů oddělených čárkami v jazyce Visual Basic

Objekt `TextFieldParser` poskytuje způsob, jak snadno a efektivně analyzovat strukturované textové soubory, jako jsou například protokoly. Vlastnost `TextFieldType` definuje, zda se jedná o soubor s oddělovačem nebo o soubor s poli textu s pevnou šířkou.  
  
### <a name="to-parse-a-comma-delimited-text-file"></a>Analýza textového souboru odděleného čárkami  
  
1. Vytvořte `TextFieldParser`nový . Následující kód vytvoří `TextFieldParser` `MyReader` pojmenovaný a `test.txt`otevře soubor .  
  
     [!code-vb[VbFileIORead#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#15)]  
  
2. Definujte `TextField` typ a oddělovač. Následující kód definuje `TextFieldType` vlastnost `Delimited` jako a oddělovač jako ",".  
  
     [!code-vb[VbFileIORead#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#16)]  
  
3. Smyčka procházet pole v souboru. Pokud jsou některé řádky poškozeny, nahlaste chybu a pokračujte v provádění analýzy. Následující kód prochází souborem, zobrazuje každé pole a hlásí všechna pole, která jsou nesprávně formátována.  
  
     [!code-vb[VbFileIORead#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#17)]  
  
4. Zavřete `While` `Using` bloky `End While` a `End Using`s a .  
  
     [!code-vb[VbFileIORead#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#18)]  
  
## <a name="example"></a>Příklad  

 Tento příklad čte `test.txt`ze souboru .  
  
 [!code-vb[VbFileIORead#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#19)]  
  
## <a name="robust-programming"></a>Robustní programování  

 Následující podmínky mohou způsobit výjimku:  
  
- Řádek nelze analyzovat pomocí zadaného formátu<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>( ). Zpráva o výjimce určuje řádek způsobující <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> výjimku, zatímco vlastnosti je přiřazen text obsažený v řádku.  
  
- Zadaný soubor neexistuje<xref:System.IO.FileNotFoundException>( ).  
  
- Situace částečné důvěryhodnosti, ve které uživatel nemá dostatečná oprávnění pro přístup k souboru. (<xref:System.Security.SecurityException>).  
  
- Cesta je příliš<xref:System.IO.PathTooLongException>dlouhá ( ).  
  
- Uživatel nemá dostatečná oprávnění pro přístup<xref:System.UnauthorizedAccessException>k souboru ( ).  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [Postupy: Čtení z textových souborů s pevnou šířkou](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)
- [Postupy: Čtení z textových souborů ve více formátech](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [Analýza textových souborů pomocí objektu TextFieldParser](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [Návod: Práce se soubory a adresáři v jazyce Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [Řešení potíží: Čtení z textových souborů a zápis do nich](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
