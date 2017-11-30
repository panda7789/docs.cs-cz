---
title: "Soubor je pro načtení do bajtového pole příliš velký."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: 686630a6-a439-46c7-8d7b-34613ae4c5d8
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2bbdb5a4dcaa22ca84428ef28c8838a6d9a0ee1b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="file-is-too-large-to-read-into-a-byte-array"></a>Soubor je pro načtení do bajtového pole příliš velký.
Velikost souboru, který se pokoušíte načíst do bajtového pole překračuje 4 GB. `My.Computer.FileSystem.ReadAllBytes` Metoda nemůže přečíst soubor, který překračuje této velikosti.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Použití <xref:System.IO.StreamReader> pro čtení tohoto souboru. Další informace najdete v tématu [základní informace o rozhraní .NET Framework souboru vstupně-výstupních operací a systému souborů (Visual Basic)](../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>  
 <xref:System.IO.StreamReader>  
 [Přístup k souborům v jazyce Visual Basic](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)  
 [Postupy: čtení textu ze souborů pomocí třídy StreamReader](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-text-from-files-with-a-streamreader.md)
