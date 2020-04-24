---
title: 'Postupy: Zápis textu do souborů'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic]
- examples [Visual Basic], text files
ms.assetid: 304956eb-530d-4df7-b48f-9b4d1f2581a0
ms.openlocfilehash: ce1ee59ba71af6bb13e05a5bce37a2f7eee37712
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334464"
---
# <a name="how-to-write-text-to-files-in-visual-basic"></a>Postupy: Zápis textu do souborů v jazyce Visual Basic

<xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> Metodu lze použít k zápisu textu do souborů. Pokud zadaný soubor neexistuje, vytvoří se.  
  
## <a name="procedure"></a>Postup  
  
#### <a name="to-write-text-to-a-file"></a>Zápis textu do souboru  
  
- Použijte `WriteAllText` metodu k zápisu textu do souboru, zadání souboru a textu, který se má zapsat. Tento příklad zapíše řádek `"This is new text."` do souboru s názvem `test.txt`a připojí text k jakémukoli existujícímu textu v souboru.  
  
     [!code-vb[VbFileIOWrite#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#3)]  
  
#### <a name="to-write-a-series-of-strings-to-a-file"></a>Zápis řady řetězců do souboru  
  
- Smyčka prostřednictvím kolekce řetězců. Použijte `WriteAllText` metodu k zápisu textu do souboru, určení cílového souboru a řetězce, který chcete přidat a nastavení `append` na. `True`  
  
     Tento příklad zapíše názvy souborů v `Documents and Settings` adresáři do, do `FileList.txt`kterého se vloží znak pro lepší čitelnost.  
  
     [!code-vb[VbFileIOWrite#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#4)]  
  
## <a name="robust-programming"></a>Robustní programování  

 Následující podmínky mohou způsobit výjimku:  
  
- Cesta není platná z některého z následujících důvodů: Jedná se o řetězec o nulové délce, obsahuje pouze prázdné znaky, obsahuje neplatné znaky nebo se jedná o cestu k zařízení (začíná \\ \\na.\\) (<xref:System.ArgumentException>).  
  
- Cesta není platná, protože je `Nothing` (<xref:System.ArgumentNullException>).  
  
- `File`odkazuje na cestu, která neexistuje (<xref:System.IO.FileNotFoundException> nebo <xref:System.IO.DirectoryNotFoundException>).  
  
- Soubor je používán jiným procesem nebo dojde k vstupně-výstupní chybě (<xref:System.IO.IOException>).  
  
- Cesta přesahuje maximální povolenou délku (<xref:System.IO.PathTooLongException>) definovanou systémem.  
  
- Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo má neplatnou hodnotu format<xref:System.NotSupportedException>().  
  
- Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).  
  
- Disk je plný a volání metody `WriteAllText` selžou (<xref:System.IO.IOException>).  
  
 Pokud používáte v kontextu s částečným vztahem důvěryhodnosti, může kód vyvolat výjimku z důvodu nedostatečných oprávnění. Další informace najdete v tématu [Základy zabezpečení přístupu ke kódu](../../../../framework/misc/code-access-security-basics.md).  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- [Postupy: čtení z textových souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)
