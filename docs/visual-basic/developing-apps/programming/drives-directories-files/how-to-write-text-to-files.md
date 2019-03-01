---
title: 'Postupy: Zápis textu do souborů v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic]
- examples [Visual Basic], text files
ms.assetid: 304956eb-530d-4df7-b48f-9b4d1f2581a0
ms.openlocfilehash: 7862e9b471808c2d01771acacefef15bdb31dda5
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975066"
---
# <a name="how-to-write-text-to-files-in-visual-basic"></a>Postupy: Zápis textu do souborů v jazyce Visual Basic
<xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> Metoda usnadňují zápis textu do souborů. Pokud zadaný soubor neexistuje, vytvoří se.  
  
## <a name="procedure"></a>Postup  
  
#### <a name="to-write-text-to-a-file"></a>Zápis textu do souboru  
  
-   Použití `WriteAllText` způsob zápisu textu do souboru, soubor a text, který má být zapsána. Tento příklad zapíše řádek `"This is new text."` do souboru s názvem `test.txt`, přidání textu k jakýkoli existující text v souboru.  
  
     [!code-vb[VbFileIOWrite#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#3)]  
  
#### <a name="to-write-a-series-of-strings-to-a-file"></a>Pro zápis do souboru řad řetězců  
  
-   Smyčky přes kolekce řetězců. Použití `WriteAllText` způsob zápisu textu do souboru, zadávání cílový soubor a řetězec, který má být přidán a nastavení `append` k `True`.  
  
     Tento příklad zapíše názvy souborů v `Documents and Settings` do adresáře `FileList.txt`, vkládání zalomení řádku vrátit mezi jednotlivými pro lepší čitelnost.  
  
     [!code-vb[VbFileIOWrite#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#4)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
-   Cesta není platná pro jednu z následujících důvodů: Jedná se o řetězec nulové délky, obsahuje pouze mezeru, obsahuje neplatné znaky nebo je cesta zařízení (začíná \\ \\.\\) (<xref:System.ArgumentException>).  
  
-   Cesta není platná, protože se jedná `Nothing` (<xref:System.ArgumentNullException>).  
  
-   `File` odkazuje na cestu, která neexistuje (<xref:System.IO.FileNotFoundException> nebo <xref:System.IO.DirectoryNotFoundException>).  
  
-   Soubor je používán jiným procesem nebo dojde k chybě vstupně-výstupních operací (<xref:System.IO.IOException>).  
  
-   Cesta přesahuje maximální délka definovaná systémem (<xref:System.IO.PathTooLongException>).  
  
-   Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).  
  
-   Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).  
  
-   Disk je plný a volání `WriteAllText` selže (<xref:System.IO.IOException>).  
  
 Pokud používáte v kontextu částečným vztahem důvěryhodnosti, kód může vyvolat výjimku, protože nedostatečná oprávnění. Další informace najdete v tématu [Základy zabezpečení přístupu kódu](../../../../framework/misc/code-access-security-basics.md).  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- [Postupy: Čtení z textových souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)
