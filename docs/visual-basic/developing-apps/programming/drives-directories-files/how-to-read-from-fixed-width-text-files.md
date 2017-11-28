---
title: "Postupy: čtení z souborů s pevnou šířkou v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- fixed-width text file
- reading text files [Visual Basic], fixed-width
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- text files [Visual Basic], reading
ms.assetid: 99be5692-967a-4e85-993e-cd18139a5a69
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a5caa124af1bf4681a4c061f453ce5e09ec2dae7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-from-fixed-width-text-files-in-visual-basic"></a>Postupy: čtení z souborů s pevnou šířkou v jazyce Visual Basic
`TextFieldParser` Objekt poskytuje způsob, jak snadno a efektivně analýza strukturovaných textových souborů, jako jsou protokoly.  
  
 `TextFieldType` Vlastnost určuje, zda soubor Analyzovaná soubor s oddělovači nebo s pevnou šířkou textových polí. Pevná šířka textového souboru může mít na konci pole proměnné šířky. K určení, zda má pole na konci proměnné šířky, zadejte ji tak, aby měl šířka menší než nebo rovna nule.  
  
### <a name="to-parse-a-fixed-width-text-file"></a>Chcete-li analyzovat soubor pevnou šířkou  
  
1.  Vytvořte novou `TextFieldParser`. Následující kód vytvoří `TextFieldParser` s názvem `Reader` a otevře soubor `test.log`.  
  
     [!code-vb[VbFileIORead#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_1.vb)]  
  
2.  Definování `TextFieldType` vlastnost jako `FixedWidth`, nastavte šířku a formátování. Následující kód definuje sloupce textu; První je 5 znaků široký, druhý 10, 11 třetí a čtvrtý je proměnné šířky.  
  
     [!code-vb[VbFileIORead#10](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_2.vb)]  
  
3.  Projděte všechny pole v souboru. Pokud jsou řádky poškozeny, ohlaste chybu a pokračujte v analýze.  
  
     [!code-vb[VbFileIORead#11](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_3.vb)]  
  
4.  Zavřít `While` a `Using` zablokuje s `End While` a `End Using`.  
  
     [!code-vb[VbFileIORead#12](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_4.vb)]  
  
## <a name="example"></a>Příklad  
 Tento příklad čte ze souboru `test.log`.  
  
 [!code-vb[VbFileIORead#13](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_5.vb)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
-   Řádek nelze analyzovat pomocí zadaného formátu (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>). Zpráva o výjimce určuje řádek, který způsobil výjimku a <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> vlastnost je přiřazena k obsažené v řádku textu.  
  
-   Zadaný soubor neexistuje (<xref:System.IO.FileNotFoundException>).  
  
-   Stav částečným vztahem důvěryhodnosti, ve kterém uživatel nemá dostatečná oprávnění k přístupu k souboru. (<xref:System.Security.SecurityException>).  
  
-   Cesta je příliš dlouhá (<xref:System.IO.PathTooLongException>).  
  
-   Uživatel nemá dostatečná oprávnění k přístupu k souboru (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>  
 [Postupy: čtení z oddělených čárkou textových souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)  
 [Postupy: čtení z textových souborů ve více formátech](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)  
 [Analýza textových souborů pomocí objektu TextFieldParser](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)  
 [Návod: Manipulace se soubory a adresáře v jazyce Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)  
 [Řešení potíží: Čtení a zápis do textových souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)  
 
