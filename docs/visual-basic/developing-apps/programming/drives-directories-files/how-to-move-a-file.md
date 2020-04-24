---
title: 'Postupy: Přesunutí souboru'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], moving
ms.assetid: 53a7457b-5815-41ad-b37d-28537c1fb77a
ms.openlocfilehash: 29c64a7a81028d47bf489212e6d8faec5e8dda75
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74335356"
---
# <a name="how-to-move-a-file-in-visual-basic"></a>Postupy: Přesunutí souboru v jazyce Visual Basic

`My.Computer.FileSystem.MoveFile` Metodu lze použít k přesunutí souboru do jiné složky. Pokud cílová struktura neexistuje, vytvoří se.  
  
### <a name="to-move-a-file"></a>Přesunutí souboru  
  
- Použijte `MoveFile` metodu k přesunutí souboru, zadáním názvu a umístění souboru pro zdrojový soubor a cílový soubor. Tento příklad přesune soubor s názvem `test.txt` z `TestDir1` do `TestDir2`. Všimněte si, že název cílového souboru je zadán, i když je stejný jako název zdrojového souboru.  
  
     [!code-vb[VbVbcnMyFileSystem#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#24)]  
  
### <a name="to-move-a-file-and-rename-it"></a>Přesunutí souboru a jeho přejmenování  
  
- Použijte `MoveFile` metodu pro přesunutí souboru, zadání názvu a umístění zdrojového souboru, cílového umístění a nového názvu v cílovém umístění. Tento příklad přesune soubor s názvem `test.txt` z `TestDir1` na `TestDir2` a přejmenuje ho `nexttest.txt`.  
  
     [!code-vb[VbVbcnMyFileSystem#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#25)]  
  
## <a name="robust-programming"></a>Robustní programování  

 Následující podmínky mohou způsobit výjimku:  
  
- Cesta není platná z některého z následujících důvodů: Jedná se o řetězec o nulové délce, obsahuje pouze prázdné znaky, obsahuje neplatné znaky nebo se jedná o cestu k zařízení (začíná \\ \\na.\\) (<xref:System.ArgumentException>).  
  
- Cesta není platná, protože je `Nothing` (<xref:System.ArgumentNullException>).  
  
- `destinationFileName`je `Nothing` nebo prázdný řetězec (<xref:System.ArgumentNullException>).  
  
- Zdrojový soubor není platný nebo neexistuje (<xref:System.IO.FileNotFoundException>).  
  
- Kombinovaná cesta odkazuje na existující adresář, cílový soubor existuje a `overwrite` je nastaven na `False`, je používán soubor v cílovém adresáři se stejným názvem nebo uživatel nemá dostatečná oprávnění pro přístup k souboru (<xref:System.IO.IOException>).  
  
- Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo má neplatnou hodnotu format<xref:System.NotSupportedException>().  
  
- `showUI`je nastaven na `True`, `onUserCancel` je nastaven na `ThrowException`a buď uživatel zrušil operaci, nebo dojde k nespecifikované vstupně-výstupní chybě (<xref:System.OperationCanceledException>).  
  
- Cesta přesahuje maximální povolenou délku (<xref:System.IO.PathTooLongException>) definovanou systémem.  
  
- Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).  
  
- Uživatel nemá požadovaná oprávnění (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.MoveFile%2A>
- [Postupy: Přejmenování souboru](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
- [Postupy: Vytvoření kopie souboru v jiném adresáři](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
- [Postupy: Analýza cest k souborům](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
