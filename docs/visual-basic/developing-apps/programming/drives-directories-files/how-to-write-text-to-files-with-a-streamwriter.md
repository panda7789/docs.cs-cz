---
title: 'Postupy: Zápis textu do souborů pomocí třídy StreamWriter v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic], StreamWriter
ms.assetid: 99762e57-ef46-4dcc-8959-a8f79c22f067
ms.openlocfilehash: 1ee4e7ba2953d15c63739f0e9c2c46e6be17133c
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965007"
---
# <a name="how-to-write-text-to-files-with-a-streamwriter-in-visual-basic"></a>Postupy: Zápis textu do souborů pomocí třídy StreamWriter v jazyce Visual Basic
Tento příklad otevře <xref:System.IO.StreamWriter> objekt s `My.Computer.FileSystem.OpenTextFileWriter` metody a použije ho k zápisu řetězce do textového souboru s <xref:System.IO.TextWriter.WriteLine%2A> metodu <xref:System.IO.StreamWriter> třídy.  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbFileIOWrite#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#5)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
-   Soubor existuje a je jen pro čtení (<xref:System.IO.IOException>).  
  
-   Disk je plný (<xref:System.IO.IOException>).  
  
-   Cesta je moc dlouhý (<xref:System.IO.PathTooLongException>).  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Tento příklad vytvoří nový soubor, pokud soubor již neexistuje. Pokud aplikace potřebuje vytvořit soubor, pak tato aplikace potřebuje `Create` přístup ke složce. Pokud soubor již existuje, aplikace potřebuje pouze `Write` přístup, a menší oprávnění. Kde je to možné, je bezpečnější vytvořit soubor při nasazení a udělit pouze `Read` přístup do jednoho souboru, spíše než `Create` přístup ke složce.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.IO.StreamWriter>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>
- [Postupy: Čtení z textových souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)
- [Zápis do souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
