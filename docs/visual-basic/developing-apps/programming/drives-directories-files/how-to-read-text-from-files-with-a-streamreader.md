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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74334565"
---
# <a name="how-to-read-text-from-files-with-a-streamreader-visual-basic"></a>Postupy: Čtení textu ze souborů pomocí třídy StreamReader (Visual Basic)

Objekt `My.Computer.FileSystem` poskytuje metody pro otevření <xref:System.IO.TextReader> a <xref:System.IO.TextWriter>. Tyto metody, `OpenTextFileWriter` a `OpenTextFileReader`, jsou pokročilé metody, které se nezobrazují v IntelliSense, pokud nevyberete kartu **vše** .  
  
### <a name="to-read-a-line-from-a-file-with-a-text-reader"></a>Načtení řádku ze souboru pomocí čtecího modulu textu  
  
- Pomocí metody `OpenTextFileReader` otevřete <xref:System.IO.TextReader>a zadejte soubor. Tento příklad otevře soubor s názvem `testfile.txt`, přečte z něj řádek a zobrazí řádek v okně se zprávou.  
  
     [!code-vb[VbFileIORead#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#1)]  
  
## <a name="robust-programming"></a>Robustní programování  

 Soubor, který je čten, musí být textový soubor.  
  
 Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu. Například soubor Form1. vb nemusí být Visual Basic zdrojový soubor.  
  
 Před použitím dat ve své aplikaci ověřte všechny vstupy. Soubor nemusí mít obsah, jaký očekáváte, a metody pro čtení z tohoto souboru mohou selhat.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  

 Aby bylo možné číst ze souboru, vaše sestavení vyžaduje úroveň oprávnění udělené třídou <xref:System.Security.Permissions.FileIOPermission>. Pokud používáte v kontextu s částečným vztahem důvěryhodnosti, může kód vyvolat výjimku z důvodu nedostatečných oprávnění. Další informace najdete v tématu [Základy zabezpečení přístupu ke kódu](../../../../framework/misc/code-access-security-basics.md). Uživatel také potřebuje přístup k souboru. Další informace najdete v tématu [Přehled technologie ACL](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100)).  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:System.Windows.Forms.OpenFileDialog>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A>
- [Komponenta SaveFileDialog](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md)
- [Čtení ze souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
