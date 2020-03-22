---
title: 'Postupy: Čtení z binárních souborů'
ms.date: 07/20/2015
helpviewer_keywords:
- binary files [Visual Basic], reading from
- I/O [Visual Basic], reading from binary files
- ReadAllBytes method [Visual Basic], reading from binary files
- My.Computer.FileSystem object, reading from binary files
ms.assetid: d2b1269e-24b6-42e0-9414-ae708db282d8
ms.openlocfilehash: c33bc72a5c79901e3715ed6a587ffdb8e3565e48
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74335298"
---
# <a name="how-to-read-from-binary-files-in-visual-basic"></a>Postupy: Čtení z binárních souborů v jazyce Visual Basic

Objekt `My.Computer.FileSystem` poskytuje `ReadAllBytes` metodu pro čtení z binárních souborů.  
  
### <a name="to-read-from-a-binary-file"></a>Čtení z binárního souboru  
  
- Použijte `ReadAllBytes` metodu, která vrací obsah souboru jako bajtové pole. Tento příklad čte `C:/Documents and Settings/selfportrait.jpg`ze souboru .  
  
     [!code-vb[VbVbcnMyFileSystem#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#78)]  
  
- U velkých binárních souborů <xref:System.IO.FileStream.Read%2A> můžete použít <xref:System.IO.FileStream> metodu objektu ke čtení ze souboru pouze zadanou částku najednou. Potom můžete omezit, kolik souboru je načten do paměti pro každou operaci čtení. Následující příklad kódu zkopíruje soubor a umožňuje volajícímu určit, kolik souboru se čte do paměti na operaci čtení.  
  
     [!code-vb[VbVbcnMyFileSystem#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#91)]  
  
## <a name="robust-programming"></a>Robustní programování  

 Následující podmínky mohou způsobit, že bude vyvolána výjimka:  
  
- Cesta není platná z jednoho z následujících důvodů: jedná se o řetězec nulové délky, obsahuje pouze prázdné<xref:System.ArgumentException>znaky, obsahuje neplatné znaky nebo se jedná o cestu zařízení ( ).  
  
- Cesta není platná, protože `Nothing` <xref:System.ArgumentNullException>je ( ).  
  
- Soubor neexistuje (<xref:System.IO.FileNotFoundException>).  
  
- Soubor je používán jiným procesem nebo dojde k chybě<xref:System.IO.IOException>vstupně-out ( ).  
  
- Cesta překračuje maximální délku definovanou<xref:System.IO.PathTooLongException>systémem ( ).  
  
- Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).  
  
- Není dostatek paměti pro zápis řetězce<xref:System.OutOfMemoryException>do vyrovnávací paměti ( ).  
  
- Uživatel nemá potřebná oprávnění k<xref:System.Security.SecurityException>zobrazení cesty ( ).  
  
 Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu. Například soubor Form1.vb nemusí být zdrojový soubor jazyka Visual Basic.  
  
 Před použitím dat ve své aplikaci ověřte všechny vstupy. Soubor nemusí mít obsah, jaký očekáváte, a metody pro čtení z tohoto souboru mohou selhat.  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [Čtení ze souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [Postupy: Čtení z textových souborů ve více formátech](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [Ukládání dat do schránky a čtení ze schránky](../../../../visual-basic/developing-apps/programming/computer-resources/storing-data-to-and-reading-from-the-clipboard.md)
