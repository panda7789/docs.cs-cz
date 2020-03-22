---
title: 'Postupy: Vytvoření kopie souboru v jiném adresáři'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: 88e2145c-d414-45a5-ad03-6f5d58ecca26
ms.openlocfilehash: e9a14e1f3743979548b92a3db653d09a470a1875
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348833"
---
# <a name="how-to-create-a-copy-of-a-file-in-a-different-directory-in-visual-basic"></a>Postupy: Vytvoření kopie souboru v jiném adresáři v jazyce Visual Basic

Metoda `My.Computer.FileSystem.CopyFile` umožňuje kopírovat soubory. Jeho parametry umožňují přepsat existující soubory, přejmenovat soubor, zobrazit průběh operace a umožnit uživateli operaci zrušit.  
  
### <a name="to-copy-a-text-file-to-another-folder"></a>Kopírování textového souboru do jiné složky  
  
- Pomocí `CopyFile` této metody zkopírujte soubor a určete zdrojový soubor a cílový adresář. Parametr `overwrite` umožňuje určit, zda chcete přepsat existující soubory. Následující příklady kódu ukazují, `CopyFile`jak používat .  
  
     [!code-vb[VbFileIOMisc#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#24)]  
  
## <a name="robust-programming"></a>Robustní programování  

 Následující podmínky mohou způsobit, že bude vyvolána výjimka:  
  
- Cesta není platná z jednoho z následujících důvodů: jedná se o řetězec nulové délky, obsahuje pouze prázdné znaky, \\ \\\\obsahuje neplatné znaky nebo se jedná o cestu zařízení (začíná na . ) (<xref:System.ArgumentException>).  
  
- Systém nemohl načíst absolutní<xref:System.ArgumentException>cestu ( ).  
  
- Cesta není platná, protože `Nothing` <xref:System.ArgumentNullException>je ( ).  
  
- Zdrojový soubor není platný nebo neexistuje<xref:System.IO.FileNotFoundException>( ).  
  
- Kombinovaná cesta odkazuje na existující<xref:System.IO.IOException>adresář ( ).  
  
- Cílový soubor existuje `overwrite` a je `False` <xref:System.IO.IOException>nastaven na ( ).  
  
- Uživatel nemá dostatečná oprávnění pro přístup<xref:System.IO.IOException>k souboru ( ).  
  
- Soubor v cílové složce se stejným názvem<xref:System.IO.IOException>se používá ( ).  
  
- Název souboru nebo složky v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).  
  
- `ShowUI`je `True`nastavena `onUserCancel` na `ThrowException`, je nastavena na ,<xref:System.OperationCanceledException>a uživatel zrušil operaci ( ).  
  
- `ShowUI`je `True`nastavena `onUserCancel` na `ThrowException`, je nastavena na , a<xref:System.OperationCanceledException>dojde k nespecifikované chybě vstupně-out ( ).  
  
- Cesta překračuje maximální délku definovanou<xref:System.IO.PathTooLongException>systémem ( ).  
  
- Uživatel nemá požadované oprávnění<xref:System.UnauthorizedAccessException>( ).  
  
- Uživatel nemá potřebná oprávnění k<xref:System.Security.SecurityException>zobrazení cesty ( ).  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- [Postupy: Kopírování souborů vyhovujících určitému vzoru do jiného adresáře](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md)
- [Postupy: Vytvoření kopie souboru ve stejném adresáři](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)
- [Postupy: Zkopírování adresáře do jiného adresáře](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)
- [Postupy: Přejmenování souboru](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
