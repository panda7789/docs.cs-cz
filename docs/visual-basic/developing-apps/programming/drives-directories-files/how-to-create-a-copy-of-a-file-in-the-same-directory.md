---
title: 'Postupy: Vytvoření kopie souboru ve stejném adresáři'
ms.date: 07/20/2015
f1_keywords:
- File.Copy
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: b2fdda86-e666-42c2-9706-9527e9fa68ff
ms.openlocfilehash: 33a4f5424ac50de7b5dc988034ca15127dc1ed02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348825"
---
# <a name="how-to-create-a-copy-of-a-file-in-the-same-directory-in-visual-basic"></a>Postupy: Vytvoření kopie souboru ve stejném adresáři v jazyce Visual Basic

Pomocí `My.Computer.FileSystem.CopyFile` této metody zkopírujte soubory. Parametry umožňují přepsat existující soubory, přejmenovat soubor, zobrazit průběh operace a umožnit uživateli operaci zrušit.  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder"></a>Vytvoření kopie souboru ve stejné složce  
  
- Použijte `CopyFile` metodu, zadání cílového souboru a umístění. Následující příklad vytvoří `test.txt` kopii `test2.txt`s názvem .  
  
     [!code-vb[VbVbcnMyFileSystem#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#51)]  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder-overwriting-existing-files"></a>Chcete-li vytvořit kopii souboru ve stejné složce, přepsání existujících souborů  
  
- Použijte `CopyFile` metodu, zadání cílového souboru `overwrite` a `True`umístění a nastavení . Následující příklad vytvoří `test.txt` kopii `test2.txt` volané a přepíše všechny existující soubory tímto názvem.  
  
     [!code-vb[VbVbcnMyFileSystem#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#52)]  
  
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
- [Postupy: Vytvoření kopie souboru v jiném adresáři](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
- [Postupy: Zkopírování adresáře do jiného adresáře](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)
- [Postupy: Přejmenování souboru](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
