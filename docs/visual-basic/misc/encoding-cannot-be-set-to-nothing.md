---
title: Kódování nelze nastavit na hodnotu Nothing
ms.date: 07/20/2015
ms.assetid: 59f7c731-8291-4a85-bf51-c225e48cdc84
ms.openlocfilehash: 99dbd1a068cabca7f57b6d5e8dd13e1069aede65
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54691326"
---
# <a name="encoding-cannot-be-set-to-nothing"></a>Kódování nelze nastavit na hodnotu Nothing
Pokus o čtení nebo zápis do souboru se nezdařil, protože parametr `encoding` byla nastavena na `Nothing` , ale vyžaduje platnou hodnotu.  
  
 <xref:System.Text.Encoding> slouží k určení, jaké kódování určené k použití při zápisu do souboru. Výchozí hodnota je UTF-8.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Zadejte platnou hodnotu pro `encoding` parametru.  
  
## <a name="see-also"></a>Viz také:
- [Kódování souborů](../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)
- [Čtení ze souborů](../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [Zápis do souborů](../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
- [My.Computer.FileSystem.ReadAllText](xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A)
- [My.Computer.FileSystem.WriteAllText](xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A)
