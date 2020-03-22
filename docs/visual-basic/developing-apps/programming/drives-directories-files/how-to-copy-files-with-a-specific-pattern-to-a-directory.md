---
title: 'Postupy: Kopírování souborů vyhovujících určitému vzoru do jiného adresáře'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: f205d2ad-bbe5-4d55-8a40-acda21aa82dd
ms.openlocfilehash: ee3951e967436a1b8aec09b8e42dc6d1b547bc02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348842"
---
# <a name="how-to-copy-files-with-a-specific-pattern-to-a-directory-in-visual-basic"></a>Postupy: Kopírování souborů vyhovujících určitému vzoru do jiného adresáře v jazyce Visual Basic

Metoda <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> vrátí kolekci řetězců jen pro čtení představující názvy cest pro soubory. `wildCards` Parametr můžete použít k určení určitého vzoru.  
  
 Prázdná kolekce je vrácena, pokud nejsou nalezeny žádné odpovídající soubory.  
  
 Tuto metodu <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A> můžete použít ke kopírování souborů do adresáře.  
  
### <a name="to-copy-files-with-a-specific-pattern-to-a-directory"></a>Kopírování souborů s určitým vzorkem do adresáře  
  
1. Pomocí `GetFiles` této metody vraťte seznam souborů. Tento příklad vrátí všechny soubory RTF v zadaném adresáři.  
  
     [!code-vb[VbFileIOMisc#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#36)]  
  
2. Pomocí `CopyFile` metody zkopírujte soubory. Tento příklad zkopíruje soubory `testdirectory`do adresáře s názvem .  
  
     [!code-vb[VbVbcnMyFileSystem#88](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#88)]  
  
3. Zavřete `For` příkaz `Next` příkazem.  
  
     [!code-vb[VbVbcnMyFileSystem#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#89)]  
  
## <a name="example"></a>Příklad  

 Následující příklad, který představuje výše uvedené výstřižky v úplné podobě, zkopíruje všechny `testdirectory`soubory RTF v zadaném adresáři do adresáře s názvem .  
  
 [!code-vb[VbFileIOMisc#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#37)]  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  

 Následující podmínky mohou způsobit výjimku:  
  
- Cesta není platná z jednoho z následujících důvodů: jedná se o řetězec nulové délky, obsahuje pouze prázdné znaky, \\ \\\\obsahuje neplatné znaky nebo se jedná o cestu zařízení (začíná na . ) (<xref:System.ArgumentException>).  
  
- Cesta není platná, protože `Nothing` <xref:System.ArgumentNullException>je ( ).  
  
- Adresář neexistuje (<xref:System.IO.DirectoryNotFoundException>).  
  
- Adresář odkazuje na existující<xref:System.IO.IOException>soubor ( ).  
  
- Cesta překračuje maximální délku definovanou<xref:System.IO.PathTooLongException>systémem ( ).  
  
- Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).  
  
- Uživatel nemá potřebná oprávnění k<xref:System.Security.SecurityException>zobrazení cesty ( ). Uživatel nemá potřebná<xref:System.UnauthorizedAccessException>oprávnění ( ).  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>
- [Postupy: Hledání podadresářů pomocí specifického vzoru](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [Řešení potíží: Čtení z textových souborů a zápis do nich](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [Postupy: Získání kolekce souborů z adresáře](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
