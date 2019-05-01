---
title: 'Postupy: Připojování k textovým souborům v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], appending to files
- I/O [Visual Basic], My.Computer.FileSystem.WriteAllText method
- I/O [Visual Basic], WriteAllText method
ms.assetid: bbbd7fb5-f169-41a9-b53f-520ea9613913
ms.openlocfilehash: 83f34e9cb669e8d2e841b13875b5237626164dd9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61960131"
---
# <a name="how-to-append-to-text-files-in-visual-basic"></a>Postupy: Připojování k textovým souborům v jazyce Visual Basic
<xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> Metodu lze použít k připojení do textového souboru, který zadáte `append` parametr je nastaven na `True`.  
  
### <a name="to-append-to-a-text-file"></a>K připojení do textového souboru  
  
- Použití `WriteAllText` způsob určení cílového souboru a řetězce, které se mají připojit a nastavení `append` parametr `True`.  
  
     Tento příklad zapíše řetězec `"This is a test string."` do souboru s názvem `Testfile.txt`.  
  
     [!code-vb[VbFileIOWrite#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#6)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
- Cesta není platná pro jednu z následujících důvodů: Jedná se o řetězec nulové délky, obsahuje pouze mezeru, obsahuje neplatné znaky nebo je cesta zařízení (začíná \\ \\.\\) (<xref:System.ArgumentException>).  
  
- Cesta není platná, protože se jedná `Nothing` (<xref:System.ArgumentNullException>).  
  
- `File` odkazuje na cestu, která neexistuje (<xref:System.IO.FileNotFoundException> nebo <xref:System.IO.DirectoryNotFoundException>).  
  
- Soubor je používán jiným procesem nebo dojde k chybě vstupně-výstupních operací (<xref:System.IO.IOException>).  
  
- Cesta přesahuje maximální délka definovaná systémem (<xref:System.IO.PathTooLongException>).  
  
- Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).  
  
- Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- [Zápis do souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
