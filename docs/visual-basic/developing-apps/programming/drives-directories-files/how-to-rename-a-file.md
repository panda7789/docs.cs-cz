---
title: 'Postupy: Přejmenování souboru'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], renaming files
- files [Visual Basic], renaming
ms.assetid: 0ea7e0c8-2cb2-4bf5-a00d-7b6e3c08a3bc
ms.openlocfilehash: e69dad9ad7f59002ad62b7a06299ff012488e534
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74334542"
---
# <a name="how-to-rename-a-file-in-visual-basic"></a>Postupy: Přejmenování souboru v jazyce Visual Basic

Použijte metodu `RenameFile` objektu `My.Computer.FileSystem` k přejmenování souboru zadáním aktuálního umístění, názvu souboru a nového názvu souboru. Tuto metodu nelze použít k přesunutí souboru. k přesunutí a přejmenování souboru použijte metodu `MoveFile`.  
  
### <a name="to-rename-a-file"></a>Přejmenování souboru  
  
- K přejmenování souboru použijte metodu `My.Computer.FileSystem.RenameFile`. Tento příklad přejmenuje soubor s názvem `Test.txt` na `SecondTest.txt`.  
  
     [!code-vb[VbVbcnMyFileSystem#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#9)]  
  
 Tento příklad kódu je také k dispozici jako fragment kódu technologie IntelliSense. Ve výběru fragmentu kódu je fragment kódu umístěný v **systému souborů, ve kterém se zpracovávají jednotky, složky a soubory**. Další informace naleznete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).  
  
## <a name="robust-programming"></a>Robustní programování  

 Následující podmínky mohou způsobit výjimku:  
  
- Cesta není platná z některého z následujících důvodů: Jedná se o řetězec o nulové délce, obsahuje pouze prázdné znaky, obsahuje neplatné znaky nebo se jedná o cestu k zařízení (začíná na \\\\.\\) (<xref:System.ArgumentException>).  
  
- `newName` obsahuje informace o cestě (<xref:System.ArgumentException>).  
  
- Cesta není platná, protože je `Nothing` (<xref:System.ArgumentNullException>).  
  
- `newName` je `Nothing` nebo prázdný řetězec (<xref:System.ArgumentNullException>).  
  
- Zdrojový soubor není platný nebo neexistuje (<xref:System.IO.FileNotFoundException>).  
  
- Existuje existující soubor nebo adresář s názvem zadaným v `newName` (<xref:System.IO.IOException>).  
  
- Cesta překračuje maximální povolenou délku systému (<xref:System.IO.PathTooLongException>).  
  
- Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo má neplatný formát (<xref:System.NotSupportedException>).  
  
- Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).  
  
- Uživatel nemá požadované oprávnění (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.RenameFile%2A>
- [Postupy: Přesunutí souboru](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-move-a-file.md)
- [Vytváření, odstraňování a přesouvání souborů a adresářů](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)
- [Postupy: Vytvoření kopie souboru ve stejném adresáři](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)
- [Postupy: Vytvoření kopie souboru v jiném adresáři](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
