---
title: 'Postupy: Čtení textu ze souborů pomocí třídy StreamReader (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- reading files [Visual Basic], text
- text, reading from files
- reading text from files [Visual Basic]
- files [Visual Basic], reading
ms.assetid: 384033c6-18f9-4d59-9610-36371226558f
ms.openlocfilehash: cd6f7b70f2ddabfc5a1476c45ca9813b9a4d949f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-read-text-from-files-with-a-streamreader-visual-basic"></a>Postupy: Čtení textu ze souborů pomocí třídy StreamReader (Visual Basic)
`My.Computer.FileSystem` Objekt poskytuje metody pro otevření <xref:System.IO.TextReader> a <xref:System.IO.TextWriter>. Tyto metody `OpenTextFileWriter` a `OpenTextFileReader`, jsou rozšířené metody, které se v technologii IntelliSense nezobrazí, dokud nevyberte **všechny** kartě.  
  
### <a name="to-read-a-line-from-a-file-with-a-text-reader"></a>Načíst řádek ze souboru s čtečku textu  
  
-   Použití `OpenTextFileReader` metoda otevřete <xref:System.IO.TextReader>, zadání souboru. Tento příklad otevře soubor s názvem `testfile.txt`, přečte řádek z něj a zobrazí řádek v okně se zprávou.  
  
     [!code-vb[VbFileIORead#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-text-from-files-with-a-streamreader_1.vb)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Soubor, který je pro čtení musí být textového souboru.  
  
 Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu. Například soubor Form1.vb nemusí být zdrojový soubor jazyka Visual Basic.  
  
 Před použitím dat ve své aplikaci ověřte všechny vstupy. Soubor nemusí mít obsah, jaký očekáváte, a metody pro čtení z tohoto souboru mohou selhat.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Čtení ze souboru, vaše sestavení vyžaduje úroveň oprávnění udělenou <xref:System.Security.Permissions.FileIOPermission> třídy. Pokud používáte v kontextu částečným vztahem důvěryhodnosti, kód může vyvolat výjimku z důvodu nedostatečných oprávnění. Další informace najdete v tématu [Základy zabezpečení přístupu kódu](../../../../framework/misc/code-access-security-basics.md). Uživatel také potřebuje přístup k souboru. Další informace najdete v tématu [Přehled technologie ACL](http://msdn.microsoft.com/library/06fbf66d-6f02-4378-b863-b2f12e349045).  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:System.Windows.Forms.OpenFileDialog>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A>  
 [Komponenta SaveFileDialog](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md)  
 [Čtení ze souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
