---
title: 'Postupy: Čtení textu ze souborů pomocí třídy StreamReader'
ms.date: 07/20/2015
helpviewer_keywords:
- reading files [Visual Basic], text
- text, reading from files
- reading text from files [Visual Basic]
- files [Visual Basic], reading
ms.assetid: 384033c6-18f9-4d59-9610-36371226558f
ms.openlocfilehash: 572463d1f03d768fb133f2dac59b012051f053bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334565"
---
# <a name="how-to-read-text-from-files-with-a-streamreader-visual-basic"></a>Postupy: Čtení textu ze souborů pomocí třídy StreamReader (Visual Basic)

Objekt `My.Computer.FileSystem` poskytuje metody pro <xref:System.IO.TextReader> otevření <xref:System.IO.TextWriter>a a . Tyto metody `OpenTextFileWriter` `OpenTextFileReader`a , jsou pokročilé metody, které se nezobrazují v intelliSense, pokud nevyberete kartu **Vše.**  
  
### <a name="to-read-a-line-from-a-file-with-a-text-reader"></a>Čtení řádku ze souboru pomocí čtečky textu  
  
- Pomocí `OpenTextFileReader` metody otevřete <xref:System.IO.TextReader>soubor , který určuje soubor. Tento příklad otevře `testfile.txt`soubor s názvem , přečte řádek z něj a zobrazí řádek v poli se zprávou.  
  
     [!code-vb[VbFileIORead#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#1)]  
  
## <a name="robust-programming"></a>Robustní programování  

 Přečtený soubor musí být textový soubor.  
  
 Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu. Například soubor Form1.vb nemusí být zdrojový soubor jazyka Visual Basic.  
  
 Před použitím dat ve své aplikaci ověřte všechny vstupy. Soubor nemusí mít obsah, jaký očekáváte, a metody pro čtení z tohoto souboru mohou selhat.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  

 Ke čtení ze souboru vyžaduje sestavení úroveň <xref:System.Security.Permissions.FileIOPermission> oprávnění udělenou třídou. Pokud jsou spuštěny v kontextu částečné důvěryhodnosti, kód může vyvolat výjimku z důvodu nedostatečných oprávnění. Další informace naleznete v [tématu Základy zabezpečení přístupu kódu](../../../../framework/misc/code-access-security-basics.md). Uživatel také potřebuje přístup k souboru. Další informace naleznete v tématu [Přehled technologie ACL](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100)).  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:System.Windows.Forms.OpenFileDialog>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A>
- [Komponenta SaveFileDialog](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md)
- [Čtení ze souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
