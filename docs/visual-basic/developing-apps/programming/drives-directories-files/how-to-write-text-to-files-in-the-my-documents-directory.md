---
title: "Postupy: Zápis textu do souborů v adresáři MyDocuments v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- examples [Visual Basic], text files
- writing to files [Visual Basic], in My Documents
ms.assetid: 1c726124-781d-4976-9baa-ed46814ff3fe
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 81eba9a71d90c79f72ccadfa65431754dfb0164e
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-write-text-to-files-in-the-my-documents-directory-in-visual-basic"></a>Postupy: Zápis textu do souborů v adresáři MyDocuments v jazyce Visual Basic
`My.Computer.FileSystem.SpecialDirectories` Objekt umožňuje přístupu speciální adresářů, jako **MyDocuments** adresáře.  
  
## <a name="procedure"></a>Postup  
  
#### <a name="to-write-new-text-files-in-the-my-documents-directory"></a>Zápis nové textové soubory v adresáři dokumenty  
  
1.  Použití `My.Computer.FileSystem.SpecialDirectories.MyDocuments` vlastnost zadat cestu.  
  
     [!code-vb[VbFileIOWrite#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_1.vb)]  
  
2.  Použití `WriteAllText` metodu pro zápis textu do zadaného souboru.  
  
     [!code-vb[VbVbcnMyFileSystem#14](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_2.vb)]  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbFileIOWrite#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_3.vb)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Nahraďte `test.txt` s názvem chcete zapisovat do souboru.  
  
## <a name="robust-programming"></a>Robustní programování  
 Tento kód znovu vyvolá všechny výjimky, které mohou nastat při zápis textu do souboru. Můžete snížit pravděpodobnost výjimky pomocí Windows Forms – ovládací prvky, jako [OpenFileDialog](../../../../framework/winforms/controls/openfiledialog-component-windows-forms.md) a [SaveFileDialog](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md) součásti, které omezují volbu uživatele na platných názvů. Pomocí těchto ovládacích prvků není spolehlivá, ale. Systém souborů můžete změnit si uživatel vybere soubor čas a čas, který spouští kód. Zpracovávání výjimek v jazyce je proto téměř vždy potřebné při práci se soubory.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Pokud používáte v kontextu částečným vztahem důvěryhodnosti, kód může vyvolat výjimku z důvodu nedostatečných oprávnění. Další informace najdete v tématu [Základy zabezpečení přístupu kódu](../../../../framework/misc/code-access-security-basics.md).  
  
 Tento příklad vytvoří nový soubor. Pokud aplikace potřebuje k vytvoření souboru, tato aplikace potřebuje vytvořit oprávnění pro složku. Jsou oprávnění nastavena pomocí seznamů řízení přístupu. Pokud soubor již existuje, aplikace musí jenom oprávnění, a menší oprávnění k zápisu. Pokud je to možné, je bezpečnější, k vytvoření tohoto souboru během nasazení a udělit pouze oprávnění ke čtení pro jeden soubor, místo udělení oprávnění vytvořit pro složku. Je také k zapisování dat do uživatelské složky než do kořenové složky bezpečnější nebo **Program Files** složky. Další informace najdete v tématu [Přehled technologie ACL](http://msdn.microsoft.com/en-us/06fbf66d-6f02-4378-b863-b2f12e349045).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IO.Path.Combine%2A?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Devices.Computer>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>  
 <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
