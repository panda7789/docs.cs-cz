---
title: 'Postupy: Čtení z binárních souborů'
ms.date: 07/20/2015
helpviewer_keywords:
- binary files [Visual Basic], reading from
- I/O [Visual Basic], reading from binary files
- ReadAllBytes method [Visual Basic], reading from binary files
- My.Computer.FileSystem object, reading from binary files
ms.assetid: d2b1269e-24b6-42e0-9414-ae708db282d8
ms.openlocfilehash: 3b4108034b86d99143fff6943e68ca0077ebd21b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359926"
---
# <a name="how-to-read-from-binary-files-in-visual-basic"></a>Postupy: Čtení z binárních souborů v jazyce Visual Basic

`My.Computer.FileSystem`Objekt poskytuje `ReadAllBytes` metodu pro čtení z binárních souborů.  
  
### <a name="to-read-from-a-binary-file"></a>Čtení z binárního souboru  
  
- Použijte `ReadAllBytes` metodu, která vrátí obsah souboru jako bajtové pole. Tento příklad čte ze souboru `C:/Documents and Settings/selfportrait.jpg` .  
  
     [!code-vb[VbVbcnMyFileSystem#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#78)]  
  
- U velkých binárních souborů lze použít <xref:System.IO.FileStream.Read%2A> metodu <xref:System.IO.FileStream> objektu pro čtení ze souboru pouze v zadané velikosti. Pak můžete omezit, kolik souborů je načteno do paměti pro každou operaci čtení. Následující příklad kódu zkopíruje soubor a umožňuje volajícímu určit, jak velká část souboru je načtena do paměti na operaci čtení.  
  
     [!code-vb[VbVbcnMyFileSystem#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#91)]  
  
## <a name="robust-programming"></a>Robustní programování  

 Následující podmínky mohou způsobit vyvolání výjimky:  
  
- Cesta není platná z některého z následujících důvodů: Jedná se o řetězec o nulové délce, obsahuje pouze prázdné znaky, obsahuje neplatné znaky nebo se jedná o cestu k zařízení ( <xref:System.ArgumentException> ).  
  
- Cesta není platná, protože je `Nothing` ( <xref:System.ArgumentNullException> ).  
  
- Soubor neexistuje ( <xref:System.IO.FileNotFoundException> ).  
  
- Soubor je používán jiným procesem nebo dojde k vstupně-výstupní chybě ( <xref:System.IO.IOException> ).  
  
- Cesta přesahuje maximální povolenou délku () definovanou systémem <xref:System.IO.PathTooLongException> .  
  
- Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo má neplatnou hodnotu Format ( <xref:System.NotSupportedException> ).  
  
- K zápisu řetězce do vyrovnávací paměti () není dostatek paměti <xref:System.OutOfMemoryException> .  
  
- Uživatel nemá potřebná oprávnění k zobrazení cesty ( <xref:System.Security.SecurityException> ).  
  
 Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu. Například soubor Form1. vb nemusí být Visual Basic zdrojový soubor.  
  
 Před použitím dat ve své aplikaci ověřte všechny vstupy. Soubor nemusí mít obsah, jaký očekáváte, a metody pro čtení z tohoto souboru mohou selhat.  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [Čtení ze souborů](reading-from-files.md)
- [Postupy: Čtení z textových souborů ve více formátech](how-to-read-from-text-files-with-multiple-formats.md)
- [Ukládání dat do schránky a čtení ze schránky](../computer-resources/storing-data-to-and-reading-from-the-clipboard.md)
