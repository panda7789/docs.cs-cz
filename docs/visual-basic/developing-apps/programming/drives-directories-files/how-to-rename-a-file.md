---
title: 'Postupy: Přejmenování souboru'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], renaming files
- files [Visual Basic], renaming
ms.assetid: 0ea7e0c8-2cb2-4bf5-a00d-7b6e3c08a3bc
ms.openlocfilehash: 3de41ee6627315f0e26964b75f564ff98fe472ec
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411587"
---
# <a name="how-to-rename-a-file-in-visual-basic"></a>Postupy: Přejmenování souboru v jazyce Visual Basic

Použijte `RenameFile` metodu `My.Computer.FileSystem` objektu k přejmenování souboru zadáním aktuálního umístění, názvu souboru a nového názvu souboru. Tuto metodu nelze použít k přesunutí souboru. `MoveFile`k přesunutí a přejmenování souboru použijte metodu.  
  
### <a name="to-rename-a-file"></a>Přejmenování souboru  
  
- `My.Computer.FileSystem.RenameFile`K přejmenování souboru použijte metodu. Tento příklad přejmenuje soubor s názvem `Test.txt` na `SecondTest.txt` .  
  
     [!code-vb[VbVbcnMyFileSystem#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#9)]  
  
 Tento příklad kódu je také k dispozici jako fragment kódu technologie IntelliSense. Ve výběru fragmentu kódu je fragment kódu umístěný v **systému souborů, ve kterém se zpracovávají jednotky, složky a soubory**. Další informace naleznete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).  
  
## <a name="robust-programming"></a>Robustní programování  

 Následující podmínky mohou způsobit výjimku:  
  
- Cesta není platná z některého z následujících důvodů: Jedná se o řetězec o nulové délce, obsahuje pouze prázdné znaky, obsahuje neplatné znaky nebo se jedná o cestu k zařízení (začíná na \\ \\ . \\ ) (<xref:System.ArgumentException>).  
  
- `newName`obsahuje informace o cestě ( <xref:System.ArgumentException> ).  
  
- Cesta není platná, protože je `Nothing` ( <xref:System.ArgumentNullException> ).  
  
- `newName`je `Nothing` nebo prázdný řetězec ( <xref:System.ArgumentNullException> ).  
  
- Zdrojový soubor není platný nebo neexistuje ( <xref:System.IO.FileNotFoundException> ).  
  
- Existuje existující soubor nebo adresář s názvem zadaným v `newName` ( <xref:System.IO.IOException> ).  
  
- Cesta přesahuje maximální povolenou délku () definovanou systémem <xref:System.IO.PathTooLongException> .  
  
- Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo má neplatnou hodnotu Format ( <xref:System.NotSupportedException> ).  
  
- Uživatel nemá potřebná oprávnění k zobrazení cesty ( <xref:System.Security.SecurityException> ).  
  
- Uživatel nemá požadovaná oprávnění ( <xref:System.UnauthorizedAccessException> ).  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.RenameFile%2A>
- [Postupy: Přesunutí souboru](how-to-move-a-file.md)
- [Vytváření, odstraňování a přesouvání souborů a adresářů](creating-deleting-and-moving-files-and-directories.md)
- [Postupy: Vytvoření kopie souboru ve stejném adresáři](how-to-create-a-copy-of-a-file-in-the-same-directory.md)
- [Postupy: Vytvoření kopie souboru v jiném adresáři](how-to-create-a-copy-of-a-file-in-a-different-directory.md)
