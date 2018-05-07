---
title: 'Postupy: Zápis textu do souborů v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic]
- examples [Visual Basic], text files
ms.assetid: 304956eb-530d-4df7-b48f-9b4d1f2581a0
ms.openlocfilehash: e8d0fa0a3705fa843c9209c6959ddc9a453b8807
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-write-text-to-files-in-visual-basic"></a>Postupy: Zápis textu do souborů v jazyce Visual Basic
<xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> Metoda slouží k zapsání textu do souborů. Pokud zadaný soubor neexistuje, vytvoří se.  
  
## <a name="procedure"></a>Postup  
  
#### <a name="to-write-text-to-a-file"></a>Zápis textu do souboru  
  
-   Použití `WriteAllText` metodu pro zápis textu do souboru, soubor a text, který má být zapsána. V tomto příkladu je zapsán řádek `"This is new text."` do souboru s názvem `test.txt`, přidání textu k existujícího textu v souboru.  
  
     [!code-vb[VbFileIOWrite#3](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files_1.vb)]  
  
#### <a name="to-write-a-series-of-strings-to-a-file"></a>Pro zápis do souboru řad řetězců  
  
-   Projděte kolekci řetězec. Použití `WriteAllText` metodu pro zápis textu do souboru, cílový soubor a řetězec, který má být přidán a nastavení `append` k `True`.  
  
     Zapíše názvy souborů v tomto příkladu `Documents and Settings` do adresáře `FileList.txt`, vkládání znaků CR vrátit mezi jednotlivými pro lepší čitelnost.  
  
     [!code-vb[VbFileIOWrite#4](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files_2.vb)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
-   Cesta není platná pro jednu z následujících důvodů: Jedná se o řetězec nulové délky, obsahuje jenom prázdné znaky, obsahuje neplatné znaky nebo je cesta zařízení (začíná \\ \\.\\) (<xref:System.ArgumentException>).  
  
-   Cesta není platná, protože se jedná `Nothing` (<xref:System.ArgumentNullException>).  
  
-   `File` odkazuje na cestu, která neexistuje (<xref:System.IO.FileNotFoundException> nebo <xref:System.IO.DirectoryNotFoundException>).  
  
-   Soubor je používán jiným procesem nebo dojde k chybě vstupně-výstupní operace (<xref:System.IO.IOException>).  
  
-   Cesta přesahuje maximální délka definovaná systémem (<xref:System.IO.PathTooLongException>).  
  
-   Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).  
  
-   Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).  
  
-   Disk je plný a volání `WriteAllText` selže (<xref:System.IO.IOException>).  
  
 Pokud používáte v kontextu částečným vztahem důvěryhodnosti, kód může vyvolat výjimku z důvodu nedostatečných oprávnění. Další informace najdete v tématu [Základy zabezpečení přístupu kódu](../../../../framework/misc/code-access-security-basics.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>  
 [Postupy: čtení z textových souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)
