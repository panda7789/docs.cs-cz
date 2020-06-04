---
title: 'Postupy: Zápis textu do souborů pomocí třídy StreamWriter'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic], StreamWriter
ms.assetid: 99762e57-ef46-4dcc-8959-a8f79c22f067
ms.openlocfilehash: 373f3bd07ea61263ddd81037d8cbbb06f789e599
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411574"
---
# <a name="how-to-write-text-to-files-with-a-streamwriter-in-visual-basic"></a>Postupy: Zápis textu do souborů pomocí třídy StreamWriter v jazyce Visual Basic

Tento příklad otevře <xref:System.IO.StreamWriter> objekt s `My.Computer.FileSystem.OpenTextFileWriter` metodou a použije ho k zápisu řetězce do textového souboru s <xref:System.IO.TextWriter.WriteLine%2A> metodou <xref:System.IO.StreamWriter> třídy.  
  
## <a name="example"></a>Příklad  

 [!code-vb[VbFileIOWrite#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#5)]  
  
## <a name="robust-programming"></a>Robustní programování  

 Následující podmínky mohou způsobit výjimku:  
  
- Soubor existuje a je určen jen pro čtení ( <xref:System.IO.IOException> ).  
  
- Disk je plný ( <xref:System.IO.IOException> ).  
  
- Cesta je příliš dlouhá ( <xref:System.IO.PathTooLongException> ).  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  

 Tento příklad vytvoří nový soubor, pokud soubor ještě neexistuje. Pokud aplikace potřebuje vytvořit soubor, tato aplikace potřebuje `Create` ke složce přístup. Pokud soubor již existuje, aplikace potřebuje `Write` přístup pouze k menšímu oprávnění. Je-li to možné, je bezpečnější vytvořit soubor během nasazení a udělit `Read` přístup pouze k jedinému souboru, nikoli ke `Create` složce.  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO.StreamWriter>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>
- [Postupy: čtení z textových souborů](how-to-read-from-text-files.md)
- [Zápis do souborů](writing-to-files.md)
