---
title: 'Postupy: Čtení textu ze souborů pomocí třídy StreamReader (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- reading files [Visual Basic], text
- text, reading from files
- reading text from files [Visual Basic]
- files [Visual Basic], reading
ms.assetid: 384033c6-18f9-4d59-9610-36371226558f
ms.openlocfilehash: 5631b402743a7be19428d15f55fbaa78b5b90668
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623366"
---
# <a name="how-to-read-text-from-files-with-a-streamreader-visual-basic"></a>Postupy: Čtení textu ze souborů pomocí třídy StreamReader (Visual Basic)
`My.Computer.FileSystem` Objekt, který poskytuje metody pro otevření <xref:System.IO.TextReader> a <xref:System.IO.TextWriter>. Tyto metody `OpenTextFileWriter` a `OpenTextFileReader`, pokročilé metody, které se nezobrazují v technologii IntelliSense, pokud jste vybrali **všechny** kartu.  
  
### <a name="to-read-a-line-from-a-file-with-a-text-reader"></a>Čtení řádku ze souboru pomocí čtečky textu  
  
- Použití `OpenTextFileReader` metoda otevřete <xref:System.IO.TextReader>, zadání souboru. Tento příklad otevře soubor s názvem `testfile.txt`, přečte řádek z něj a zobrazuje řádek v okně se zprávou.  
  
     [!code-vb[VbFileIORead#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#1)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Soubor, který je pro čtení musí být textový soubor.  
  
 Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu. Například soubor Form1.vb nemusí být zdrojový soubor jazyka Visual Basic.  
  
 Před použitím dat ve své aplikaci ověřte všechny vstupy. Soubor nemusí mít obsah, jaký očekáváte, a metody pro čtení z tohoto souboru mohou selhat.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Čtení ze souboru sestavení vyžaduje úroveň oprávnění udělenou <xref:System.Security.Permissions.FileIOPermission> třídy. Pokud používáte v kontextu částečným vztahem důvěryhodnosti, kód může vyvolat výjimku, protože nedostatečná oprávnění. Další informace najdete v tématu [Základy zabezpečení přístupu kódu](../../../../framework/misc/code-access-security-basics.md). Uživatel potřebuje také přístup k souboru. Další informace najdete v tématu [Přehled technologie ACL](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100)).  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:System.Windows.Forms.OpenFileDialog>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A>
- [Komponenta SaveFileDialog](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md)
- [Čtení ze souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
