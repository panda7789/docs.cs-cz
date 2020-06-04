---
title: 'Postupy: Kopírování souborů vyhovujících určitému vzoru do jiného adresáře'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: f205d2ad-bbe5-4d55-8a40-acda21aa82dd
ms.openlocfilehash: 7e263e2c9035db54dbb58c6c78c0647d5442504e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401703"
---
# <a name="how-to-copy-files-with-a-specific-pattern-to-a-directory-in-visual-basic"></a>Postupy: Kopírování souborů vyhovujících určitému vzoru do jiného adresáře v jazyce Visual Basic

<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>Metoda vrátí kolekci řetězců jen pro čtení, které představují názvy cest pro soubory. `wildCards`K určení konkrétního vzoru můžete použít parametr.  
  
 Je-li nalezena žádná vyhovující soubory, je vrácena prázdná kolekce.  
  
 Můžete použít <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A> metodu ke zkopírování souborů do adresáře.  
  
### <a name="to-copy-files-with-a-specific-pattern-to-a-directory"></a>Kopírování souborů s určitým vzorem do adresáře  
  
1. `GetFiles`K vrácení seznamu souborů použijte metodu. Tento příklad vrátí všechny soubory. RTF v zadaném adresáři.  
  
     [!code-vb[VbFileIOMisc#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#36)]  
  
2. `CopyFile`K kopírování souborů použijte metodu. V tomto příkladu se zkopírují soubory do adresáře s názvem `testdirectory` .  
  
     [!code-vb[VbVbcnMyFileSystem#88](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#88)]  
  
3. Uzavřete `For` příkaz s `Next` příkazem.  
  
     [!code-vb[VbVbcnMyFileSystem#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#89)]  
  
## <a name="example"></a>Příklad  

 Následující příklad, který prezentuje výše uvedené fragmenty kódu v úplné podobě, zkopíruje všechny soubory. RTF v zadaném adresáři do adresáře s názvem `testdirectory` .  
  
 [!code-vb[VbFileIOMisc#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#37)]  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  

 Následující podmínky mohou způsobit výjimku:  
  
- Cesta není platná z některého z následujících důvodů: Jedná se o řetězec o nulové délce, obsahuje pouze prázdné znaky, obsahuje neplatné znaky nebo se jedná o cestu k zařízení (začíná na \\ \\ . \\ ) (<xref:System.ArgumentException>).  
  
- Cesta není platná, protože je `Nothing` ( <xref:System.ArgumentNullException> ).  
  
- Adresář neexistuje ( <xref:System.IO.DirectoryNotFoundException> ).  
  
- Adresář odkazuje na existující soubor ( <xref:System.IO.IOException> ).  
  
- Cesta přesahuje maximální povolenou délku () definovanou systémem <xref:System.IO.PathTooLongException> .  
  
- Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo má neplatnou hodnotu Format ( <xref:System.NotSupportedException> ).  
  
- Uživatel nemá potřebná oprávnění k zobrazení cesty ( <xref:System.Security.SecurityException> ). Uživatel nemá potřebná oprávnění ( <xref:System.UnauthorizedAccessException> ).  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>
- [Postupy: Hledání podadresářů pomocí specifického vzoru](how-to-find-subdirectories-with-a-specific-pattern.md)
- [Řešení potíží: Čtení z textových souborů a zápis do nich](troubleshooting-reading-from-and-writing-to-text-files.md)
- [Postupy: Získání kolekce souborů z adresáře](how-to-get-the-collection-of-files-in-a-directory.md)
