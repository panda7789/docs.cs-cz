---
title: Soubor je pro načtení do bajtového pole příliš velký.
ms.date: 07/20/2015
ms.assetid: 686630a6-a439-46c7-8d7b-34613ae4c5d8
ms.openlocfilehash: 1b04d47cab77269a0ce84ef77c162a4401d99d9e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="file-is-too-large-to-read-into-a-byte-array"></a>Soubor je pro načtení do bajtového pole příliš velký.
Velikost souboru, který se pokoušíte načíst do bajtového pole překračuje 4 GB. `My.Computer.FileSystem.ReadAllBytes` Metoda nemůže přečíst soubor, který překračuje této velikosti.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Použití <xref:System.IO.StreamReader> pro čtení tohoto souboru. Další informace najdete v tématu [základní informace o rozhraní .NET Framework souboru vstupně-výstupních operací a systému souborů (Visual Basic)](../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>  
 <xref:System.IO.StreamReader>  
 [Přístup k souborům v jazyce Visual Basic](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)  
 [Postupy: Čtení textu ze souborů pomocí třídy StreamReader](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-text-from-files-with-a-streamreader.md)
