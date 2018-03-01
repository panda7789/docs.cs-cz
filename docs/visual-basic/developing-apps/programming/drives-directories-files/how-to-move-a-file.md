---
title: "Postupy: Přesunutí souboru v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- files [Visual Basic], moving
ms.assetid: 53a7457b-5815-41ad-b37d-28537c1fb77a
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 96c6d1d89c0dfe4720637202b42414047e96f146
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-move-a-file-in-visual-basic"></a>Postupy: Přesunutí souboru v jazyce Visual Basic
`My.Computer.FileSystem.MoveFile` Metoda slouží k přesunutí souboru do jiné složky. Pokud cílová struktura neexistuje, bude vytvořen.  
  
### <a name="to-move-a-file"></a>Chcete-li přesunout soubor  
  
-   Použití `MoveFile` metoda přesunout soubor, zadáte název souboru a umístění pro cílový i zdrojový soubor. Tento příklad přesune soubor s názvem `test.txt` z `TestDir1` k `TestDir2`. Všimněte si, zda je zadán název cílového souboru, i když je stejný jako název zdrojového souboru.  
  
     [!code-vb[VbVbcnMyFileSystem#24](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-move-a-file_1.vb)]  
  
### <a name="to-move-a-file-and-rename-it"></a>Přesunout soubor a přejmenujte ji  
  
-   Použití `MoveFile` metoda souboru, název zdrojového souboru a umístění, cílové umístění a název nového v cílovém umístění. Tento příklad přesune soubor s názvem `test.txt` z `TestDir1` k `TestDir2` a přejmenuje ho `nexttest.txt`.  
  
     [!code-vb[VbVbcnMyFileSystem#25](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-move-a-file_2.vb)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
-   Cesta není platná pro jednu z následujících důvodů: Jedná se o řetězec nulové délky, obsahuje jenom prázdné znaky, obsahuje neplatné znaky nebo je cesta zařízení (začíná \\ \\.\\) (<xref:System.ArgumentException>).  
  
-   Cesta není platná, protože se jedná `Nothing` (<xref:System.ArgumentNullException>).  
  
-   `destinationFileName`je `Nothing` nebo prázdný řetězec (<xref:System.ArgumentNullException>).  
  
-   Zdrojový soubor je neplatný nebo neexistuje (<xref:System.IO.FileNotFoundException>).  
  
-   Kombinovaná cesta odkazuje na existující adresář, cílový soubor existuje a `overwrite` je nastaven na `False`, nepoužívá soubor v cílovém adresáři se stejným názvem, nebo uživatel nemá dostatečná oprávnění k přístupu k souboru (<xref:System.IO.IOException> ).  
  
-   Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).  
  
-   `showUI`je nastavena na `True`, `onUserCancel` je nastaven na `ThrowException`a buď uživatel zrušil operaci nebo dojde k nespecifikované chybě vstupně-výstupní operace (<xref:System.OperationCanceledException>).  
  
-   Cesta přesahuje maximální délka definovaná systémem (<xref:System.IO.PathTooLongException>).  
  
-   Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).  
  
-   Uživatel nemá požadované oprávnění (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.MoveFile%2A>  
 [Postupy: přejmenování souboru](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)  
 [Postupy: vytvoření kopie souboru v jiném adresáři](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)  
 [Postupy: Analýza cest k souborům](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
