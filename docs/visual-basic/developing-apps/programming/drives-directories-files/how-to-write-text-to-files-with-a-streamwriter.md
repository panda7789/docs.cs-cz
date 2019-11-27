---
title: 'Postupy: Zápis textu do souborů pomocí třídy StreamWriter'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic], StreamWriter
ms.assetid: 99762e57-ef46-4dcc-8959-a8f79c22f067
ms.openlocfilehash: 869e29263abcdd8525b2c372c7bb466e3e21fc65
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74334499"
---
# <a name="how-to-write-text-to-files-with-a-streamwriter-in-visual-basic"></a>Postupy: Zápis textu do souborů pomocí třídy StreamWriter v jazyce Visual Basic

Tento příklad otevře objekt <xref:System.IO.StreamWriter> s metodou `My.Computer.FileSystem.OpenTextFileWriter` a použije ho k zápisu řetězce do textového souboru s metodou <xref:System.IO.TextWriter.WriteLine%2A> třídy <xref:System.IO.StreamWriter>.  
  
## <a name="example"></a>Příklad  

 [!code-vb[VbFileIOWrite#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#5)]  
  
## <a name="robust-programming"></a>Robustní programování  

 Následující podmínky mohou způsobit výjimku:  
  
- Soubor existuje a je určen jen pro čtení (<xref:System.IO.IOException>).  
  
- Disk je plný (<xref:System.IO.IOException>).  
  
- Cesta je příliš dlouhá (<xref:System.IO.PathTooLongException>).  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  

 Tento příklad vytvoří nový soubor, pokud soubor ještě neexistuje. Pokud aplikace potřebuje vytvořit soubor, musí tato aplikace `Create` přístup ke složce. Pokud soubor již existuje, aplikace potřebuje pouze `Write` přístup, což je méně oprávnění. Pokud je to možné, je bezpečnější vytvořit soubor během nasazení a udělit `Read` přístup pouze k jednomu souboru místo `Create` přístupu pro složku.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO.StreamWriter>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>
- [Postupy: čtení z textových souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)
- [Zápis do souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
