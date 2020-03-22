---
title: 'Postupy: Zápis textu do souborů pomocí třídy StreamWriter'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic], StreamWriter
ms.assetid: 99762e57-ef46-4dcc-8959-a8f79c22f067
ms.openlocfilehash: 869e29263abcdd8525b2c372c7bb466e3e21fc65
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334499"
---
# <a name="how-to-write-text-to-files-with-a-streamwriter-in-visual-basic"></a>Postupy: Zápis textu do souborů pomocí třídy StreamWriter v jazyce Visual Basic

Tento příklad <xref:System.IO.StreamWriter> otevře objekt `My.Computer.FileSystem.OpenTextFileWriter` s metodou a používá jej k zápisu řetězce do textového souboru s <xref:System.IO.TextWriter.WriteLine%2A> metodou <xref:System.IO.StreamWriter> třídy.  
  
## <a name="example"></a>Příklad  

 [!code-vb[VbFileIOWrite#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#5)]  
  
## <a name="robust-programming"></a>Robustní programování  

 Následující podmínky mohou způsobit výjimku:  
  
- Soubor existuje a je jen<xref:System.IO.IOException>pro čtení ( ).  
  
- Disk je plný<xref:System.IO.IOException>( ).  
  
- Název cesty je příliš<xref:System.IO.PathTooLongException>dlouhý ( ).  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  

 Tento příklad vytvoří nový soubor, pokud soubor ještě neexistuje. Pokud aplikace potřebuje vytvořit soubor, tato `Create` aplikace potřebuje přístup pro složku. Pokud soubor již existuje, aplikace `Write` potřebuje pouze přístup, menší oprávnění. Pokud je to možné, je bezpečnější vytvořit soubor `Read` během nasazení a udělit `Create` přístup pouze k jednomu souboru, nikoli přístup u složky.  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO.StreamWriter>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>
- [Postup: Čtení z textových souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)
- [Zápis do souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
