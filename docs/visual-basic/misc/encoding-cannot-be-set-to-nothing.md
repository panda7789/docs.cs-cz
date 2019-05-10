---
title: Kódování nelze nastavit na hodnotu Nothing
ms.date: 07/20/2015
ms.assetid: 59f7c731-8291-4a85-bf51-c225e48cdc84
ms.openlocfilehash: 492db7755e8b2b75ea8c60d7f4e1ccc1a5ded865
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64598353"
---
# <a name="encoding-cannot-be-set-to-nothing"></a>Kódování nelze nastavit na hodnotu Nothing
Pokus o čtení nebo zápis do souboru se nezdařil, protože parametr `encoding` byla nastavena na `Nothing` , ale vyžaduje platnou hodnotu.  
  
 <xref:System.Text.Encoding> slouží k určení, jaké kódování určené k použití při zápisu do souboru. Výchozí hodnota je UTF-8.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Zadejte platnou hodnotu pro `encoding` parametru.  
  
## <a name="see-also"></a>Viz také:

- [Kódování souborů](../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)
- [Čtení ze souborů](../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [Zápis do souborů](../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
- [My.Computer.FileSystem.ReadAllText](xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A)
- [My.Computer.FileSystem.WriteAllText](xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A)
