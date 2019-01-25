---
title: 'Postupy: Kopírování souborů vyhovujících určitému vzoru do jiného adresáře v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: f205d2ad-bbe5-4d55-8a40-acda21aa82dd
ms.openlocfilehash: 9c2ed926d21bf73b9b93863e5c3a3ed9ccc950aa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54634074"
---
# <a name="how-to-copy-files-with-a-specific-pattern-to-a-directory-in-visual-basic"></a>Postupy: Kopírování souborů vyhovujících určitému vzoru do jiného adresáře v jazyce Visual Basic
<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> Metoda vrátí kolekci řetězců, které představují názvy cest souborů jen pro čtení. Můžete použít `wildCards` parametr k určení určitému vzoru.  
  
 Prázdná kolekce je vrácena, pokud nejsou nalezeny žádné odpovídající soubory.  
  
 Můžete použít <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A> metoda kopírování souborů do jiného adresáře.  
  
### <a name="to-copy-files-with-a-specific-pattern-to-a-directory"></a>Pro kopírování souborů vyhovujících určitému vzoru do jiného adresáře  
  
1.  Použití `GetFiles` metody, která vrátí seznam souborů. V tomto příkladu vrátí všechny soubory ve formátu RTF v zadaném adresáři.  
  
     [!code-vb[VbFileIOMisc#36](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-files-with-a-specific-pattern-to-a-directory_1.vb)]  
  
2.  Použití `CopyFile` metoda kopírování souborů. Tento příklad zkopíruje soubory do adresáře s názvem `testdirectory`.  
  
     [!code-vb[VbVbcnMyFileSystem#88](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-files-with-a-specific-pattern-to-a-directory_2.vb)]  
  
3.  Zavřít `For` příkazem `Next` příkazu.  
  
     [!code-vb[VbVbcnMyFileSystem#89](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-files-with-a-specific-pattern-to-a-directory_3.vb)]  
  
## <a name="example"></a>Příklad  
 Následujícím příkladu, který představuje výše uvedené fragmenty kódu v celý formulář, zkopíruje všechny soubory ve formátu RTF v zadaném adresáři k adresáři s názvem `testdirectory`.  
  
 [!code-vb[VbFileIOMisc#37](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-files-with-a-specific-pattern-to-a-directory_4.vb)]  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Následující podmínky mohou způsobit výjimku:  
  
-   Cesta není platná pro jednu z následujících důvodů: Jedná se o řetězec nulové délky, obsahuje pouze mezeru, obsahuje neplatné znaky nebo je cesta zařízení (začíná \\ \\.\\) (<xref:System.ArgumentException>).  
  
-   Cesta není platná, protože se jedná `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Adresáři neexistuje (<xref:System.IO.DirectoryNotFoundException>).  
  
-   Adresář odkazuje na existující soubor (<xref:System.IO.IOException>).  
  
-   Cesta přesahuje maximální délka definovaná systémem (<xref:System.IO.PathTooLongException>).  
  
-   Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).  
  
-   Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>). Uživatel nemá potřebná oprávnění (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>
- [Postupy: Hledání podadresářů pomocí specifického vzoru](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [Řešení potíží: Čtení a zápis do textových souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [Postupy: Získání kolekce souborů v adresáři](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
