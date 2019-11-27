---
title: 'Postupy: Odstranění souboru'
ms.date: 07/20/2015
helpviewer_keywords:
- Delete method [Visual Basic]
- files [Visual Basic], deleting
- files [Visual Basic], manipulating
- File object
ms.assetid: 4b721769-3e45-4be7-b7fe-b08dc4141b44
ms.openlocfilehash: 57182f1a1d92b7fe954fd26b32c5e4b1107823ee
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348784"
---
# <a name="how-to-delete-a-file-in-visual-basic"></a>Postupy: Odstranění souboru v jazyce Visual Basic

Metoda `DeleteFile` objektu `My.Computer.FileSystem` umožňuje odstranit soubor. Mezi možnosti, které nabízí, patří: bez ohledu na to, jestli se má odstraněný soubor poslat do **koše**, jestli se má uživatel položit, aby zkontroloval, jestli by se měl soubor odstranit, a co dělat, když uživatel operaci zruší.  
  
### <a name="to-delete-a-text-file"></a>Odstranění textového souboru  
  
- K odstranění souboru použijte metodu `DeleteFile`. Následující kód ukazuje, jak odstranit soubor s názvem `test.txt`.  
  
     [!code-vb[VbVbcnMyFileSystem#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#22)]  
  
### <a name="to-delete-a-text-file-and-ask-the-user-to-confirm-that-the-file-should-be-deleted"></a>Odstranění textového souboru a požádejte uživatele o potvrzení, že by se měl soubor odstranit  
  
- Pomocí metody `DeleteFile` odstraňte soubor a nastavte `showUI` na `AllDialogs`. Následující kód ukazuje, jak odstranit soubor s názvem `test.txt` a umožní uživateli potvrdit, že by měl být soubor smazán.  
  
     [!code-vb[VbFileIOMisc#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#9)]  
  
### <a name="to-delete-a-text-file-and-send-it-to-the-recycle-bin"></a>Odstranění textového souboru a jeho odeslání do odpadkového koše  
  
- Použijte metodu `DeleteFile` k odstranění souboru, zadáním `SendToRecycleBin` parametru `recycle`. Následující kód ukazuje, jak odstranit soubor s názvem `test.txt` a odeslat ho do **odpadkového**koše.  
  
     [!code-vb[VbFileIOMisc#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#10)]  
  
## <a name="robust-programming"></a>Robustní programování  

 Následující podmínky mohou způsobit výjimku:  
  
- Cesta není platná z některého z následujících důvodů: Jedná se o řetězec o nulové délce, obsahuje pouze prázdné znaky, obsahuje neplatné znaky nebo se jedná o cestu k zařízení (začíná na \\\\.\\) (<xref:System.ArgumentException>).  
  
- Cesta není platná, protože je `Nothing` (<xref:System.ArgumentNullException>).  
  
- Cesta překračuje maximální povolenou délku systému (<xref:System.IO.PathTooLongException>).  
  
- Název souboru nebo složky v cestě obsahuje dvojtečku (:) nebo má neplatný formát (<xref:System.NotSupportedException>).  
  
- Soubor se používá (<xref:System.IO.IOException>).  
  
- Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).  
  
- Soubor neexistuje (<xref:System.IO.FileNotFoundException>).  
  
- Uživatel nemá oprávnění k odstranění tohoto souboru, nebo je soubor jen pro čtení (<xref:System.UnauthorizedAccessException>).  
  
- V případě, že uživatel nemá dostatečná oprávnění (<xref:System.Security.SecurityException>), existuje situace s částečným vztahem důvěryhodnosti.  
  
- Uživatel operaci zrušil a `onUserCancel` je nastaven na `ThrowException` (<xref:System.OperationCanceledException>).  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.UIOption>
- <xref:Microsoft.VisualBasic.FileIO.RecycleOption>
- [Postupy: Získání kolekce souborů z adresáře](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
