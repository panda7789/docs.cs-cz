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
ms.openlocfilehash: 741f0c80ba268369ebdd598460e9d5fa13d09571
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401677"
---
# <a name="how-to-create-a-copy-of-a-file-in-the-same-directory-in-visual-basic"></a>Postupy: Vytvoření kopie souboru ve stejném adresáři v jazyce Visual Basic

`My.Computer.FileSystem.CopyFile`K kopírování souborů použijte metodu. Parametry umožňují přepsat existující soubory, přejmenovat soubor, zobrazit průběh operace a nechat uživatele operaci zrušit.  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder"></a>Vytvoření kopie souboru ve stejné složce  
  
- Použijte `CopyFile` metodu, zadejte cílový soubor a umístění. Následující příklad vytvoří kopii s `test.txt` názvem `test2.txt` .  
  
     [!code-vb[VbVbcnMyFileSystem#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#51)]  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder-overwriting-existing-files"></a>Vytvoření kopie souboru ve stejné složce, při které se přepíší stávající soubory  
  
- Použijte `CopyFile` metodu, zadejte cílový soubor a umístění a nastavení `overwrite` na `True` . Následující příklad vytvoří kopii s `test.txt` názvem `test2.txt` a přepíše všechny existující soubory s tímto názvem.  
  
     [!code-vb[VbVbcnMyFileSystem#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#52)]  
  
## <a name="robust-programming"></a>Robustní programování  

 Následující podmínky mohou způsobit vyvolání výjimky:  
  
- Cesta není platná z některého z následujících důvodů: Jedná se o řetězec o nulové délce, obsahuje pouze prázdné znaky, obsahuje neplatné znaky nebo se jedná o cestu k zařízení (začíná na \\ \\ . \\ ) (<xref:System.ArgumentException>).  
  
- Systém nemůže načíst absolutní cestu ( <xref:System.ArgumentException> ).  
  
- Cesta není platná, protože je `Nothing` ( <xref:System.ArgumentNullException> ).  
  
- Zdrojový soubor není platný nebo neexistuje ( <xref:System.IO.FileNotFoundException> ).  
  
- Kombinovaná cesta odkazuje na existující adresář ( <xref:System.IO.IOException> ).  
  
- Cílový soubor existuje a `overwrite` je nastaven na hodnotu `False` ( <xref:System.IO.IOException> ).  
  
- Uživatel nemá dostatečná oprávnění pro přístup k souboru ( <xref:System.IO.IOException> ).  
  
- Soubor v cílové složce se stejným názvem se používá ( <xref:System.IO.IOException> ).  
  
- Název souboru nebo složky v cestě obsahuje dvojtečku (:) nebo má neplatnou hodnotu Format ( <xref:System.NotSupportedException> ).  
  
- `ShowUI`je nastaven na `True` , `onUserCancel` je nastaven na `ThrowException` a uživatel zrušil operaci ( <xref:System.OperationCanceledException> ).  
  
- `ShowUI`je nastaven na `True` , `onUserCancel` je nastaven na `ThrowException` a dojde k nespecifikované vstupně-výstupní chybě ( <xref:System.OperationCanceledException> ).  
  
- Cesta přesahuje maximální povolenou délku () definovanou systémem <xref:System.IO.PathTooLongException> .  
  
- Uživatel nemá požadovaná oprávnění ( <xref:System.UnauthorizedAccessException> ).  
  
- Uživatel nemá potřebná oprávnění k zobrazení cesty ( <xref:System.Security.SecurityException> ).  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- [Postupy: Kopírování souborů vyhovujících určitému vzoru do jiného adresáře](how-to-copy-files-with-a-specific-pattern-to-a-directory.md)
- [Postupy: Vytvoření kopie souboru v jiném adresáři](how-to-create-a-copy-of-a-file-in-a-different-directory.md)
- [Postupy: Zkopírování adresáře do jiného adresáře](how-to-copy-a-directory-to-another-directory.md)
- [Postupy: Přejmenování souboru](how-to-rename-a-file.md)
