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

Metodu `My.Computer.FileSystem.MoveFile` lze použít k přesunutí souboru do jiné složky. Pokud cílová struktura neexistuje, bude vytvořena.  
  
### <a name="to-move-a-file"></a>Přesunutí souboru  
  
- Pomocí `MoveFile` metody přesuňte soubor a zadejte název souboru a umístění zdrojového i cílového souboru. Tento příklad přesune `test.txt` soubor `TestDir1` `TestDir2`pojmenovaný z do . Všimněte si, že název cílového souboru je určen, i když je stejný jako název zdrojového souboru.  
  
     [!code-vb[VbVbcnMyFileSystem#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#24)]  
  
### <a name="to-move-a-file-and-rename-it"></a>Přesunutí souboru a jeho přejmenování  
  
- Pomocí `MoveFile` metody přesuňte soubor a zadejte název a umístění zdrojového souboru, cílové umístění a nový název v cílovém umístění. Tento příklad přesune `test.txt` soubor `TestDir1` `TestDir2` pojmenovaný z `nexttest.txt`do a přejmenuje jej .  
  
     [!code-vb[VbVbcnMyFileSystem#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#25)]  
  
## <a name="robust-programming"></a>Robustní programování  

 Následující podmínky mohou způsobit výjimku:  
  
- Cesta není platná z jednoho z následujících důvodů: jedná se o řetězec nulové délky, obsahuje pouze prázdné znaky, \\ \\\\obsahuje neplatné znaky nebo se jedná o cestu zařízení (začíná na . ) (<xref:System.ArgumentException>).  
  
- Cesta není platná, protože `Nothing` <xref:System.ArgumentNullException>je ( ).  
  
- `destinationFileName`je `Nothing` nebo prázdný<xref:System.ArgumentNullException>řetězec ( ).  
  
- Zdrojový soubor není platný nebo neexistuje<xref:System.IO.FileNotFoundException>( ).  
  
- Kombinovaná cesta odkazuje na existující adresář, cílový `overwrite` soubor existuje `False`a je nastaven na soubor v cílovém adresáři se stejným názvem nebo uživatel<xref:System.IO.IOException>nemá dostatečná oprávnění pro přístup k souboru ( .  
  
- Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).  
  
- `showUI`je `True`nastavena `onUserCancel` na `ThrowException`, je nastavena na , a buď uživatel zrušil operaci<xref:System.OperationCanceledException>nebo dojde k nespecifikované chybě vstupně-out ( ).  
  
- Cesta překračuje maximální délku definovanou<xref:System.IO.PathTooLongException>systémem ( ).  
  
- Uživatel nemá potřebná oprávnění k<xref:System.Security.SecurityException>zobrazení cesty ( ).  
  
- Uživatel nemá požadované oprávnění<xref:System.UnauthorizedAccessException>( ).  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.MoveFile%2A>
- [Postupy: Přejmenování souboru](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
- [Postupy: Vytvoření kopie souboru v jiném adresáři](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
- [Postupy: Analýza cest k souborům](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
