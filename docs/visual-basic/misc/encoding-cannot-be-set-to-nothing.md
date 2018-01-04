---
title: "Kódování nelze nastavit na hodnotu Nothing"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: 59f7c731-8291-4a85-bf51-c225e48cdc84
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 42baef6e0634849004290dce3db32e47f103282d
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="encoding-cannot-be-set-to-nothing"></a>Kódování nelze nastavit na hodnotu Nothing
Pokus o číst nebo zapisovat do souboru se nezdařila, protože parametr `encoding` byla nastavena na `Nothing` , ale vyžaduje platnou hodnotu.  
  
 <xref:System.Text.Encoding>slouží k určení, jaké kódování určené k použití při zápisu do souboru. Výchozí hodnota je UTF-8.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Zadejte platnou hodnotu `encoding` parametr.  
  
## <a name="see-also"></a>Viz také  
 [Kódování souborů](../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)  
 [Čtení ze souborů](../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 [Zápis do souborů](../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)  
 [My.Computer.FileSystem.ReadAllText](xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A)  
 [My.Computer.FileSystem.WriteAllText –](xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A)
