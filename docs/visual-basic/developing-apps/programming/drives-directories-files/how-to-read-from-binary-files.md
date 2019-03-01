---
title: 'Postupy: Čtení z binárních souborů v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- binary files [Visual Basic], reading from
- I/O [Visual Basic], reading from binary files
- ReadAllBytes method [Visual Basic], reading from binary files
- My.Computer.FileSystem object, reading from binary files
ms.assetid: d2b1269e-24b6-42e0-9414-ae708db282d8
ms.openlocfilehash: e9b30d119a404396e2bf37aa445a420f7823c57b
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980383"
---
# <a name="how-to-read-from-binary-files-in-visual-basic"></a>Postupy: Čtení z binárních souborů v jazyce Visual Basic
`My.Computer.FileSystem` Objekt, který poskytuje `ReadAllBytes` metody pro čtení z binárních souborů.  
  
### <a name="to-read-from-a-binary-file"></a>Čtení z binárního souboru  
  
-   Použití `ReadAllBytes` metoda, která vrátí obsah souboru jako bajtové pole. V tomto příkladu načteme soubor `C:/Documents and Settings/selfportrait.jpg`.  
  
     [!code-vb[VbVbcnMyFileSystem#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#78)]  
  
-   Pro velké binární soubory, můžete použít <xref:System.IO.FileStream.Read%2A> metodu <xref:System.IO.FileStream> objektu určeného ke čtení ze souboru určenou dobu po jednom. Můžete omezit, jak velká část souboru je načten do paměti pro každou operaci čtení. Následující příklad kódu se zkopíruje soubor a umožňuje volajícímu zadat, jak velká část souboru je načíst do paměti za operace čtení.  
  
     [!code-vb[VbVbcnMyFileSystem#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#91)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku, která je vyvolána:  
  
-   Cesta není platná pro jednu z následujících důvodů: Jedná se o řetězec nulové délky, obsahuje pouze mezeru, obsahuje neplatné znaky nebo je cesta zařízení (<xref:System.ArgumentException>).  
  
-   Cesta není platná, protože se jedná `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Soubor neexistuje (<xref:System.IO.FileNotFoundException>).  
  
-   Soubor je používán jiným procesem nebo dojde k chybě vstupně-výstupních operací (<xref:System.IO.IOException>).  
  
-   Cesta přesahuje maximální délka definovaná systémem (<xref:System.IO.PathTooLongException>).  
  
-   Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).  
  
-   Není dostatek paměti k zápisu řetězce do vyrovnávací paměti (<xref:System.OutOfMemoryException>).  
  
-   Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).  
  
 Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu. Například soubor Form1.vb nemusí být zdrojový soubor jazyka Visual Basic.  
  
 Před použitím dat ve své aplikaci ověřte všechny vstupy. Soubor nemusí mít obsah, jaký očekáváte, a metody pro čtení z tohoto souboru mohou selhat.  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [Čtení ze souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [Postupy: Čtení z textových souborů ve více formátech](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [Ukládání dat do schránky a čtení ze schránky](../../../../visual-basic/developing-apps/programming/computer-resources/storing-data-to-and-reading-from-the-clipboard.md)
