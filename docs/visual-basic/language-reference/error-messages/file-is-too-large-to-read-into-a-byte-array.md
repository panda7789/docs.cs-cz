---
title: Soubor je pro načtení do bajtového pole příliš velký.
ms.date: 07/20/2015
ms.assetid: 686630a6-a439-46c7-8d7b-34613ae4c5d8
ms.openlocfilehash: 90db5214ff26cfacf3a832c904d742c9caf853d6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54728932"
---
# <a name="file-is-too-large-to-read-into-a-byte-array"></a>Soubor je pro načtení do bajtového pole příliš velký.
Velikost souboru, který se pokoušíte načtení do bajtového pole překračuje 4 GB. `My.Computer.FileSystem.ReadAllBytes` Metoda nemůže přečíst soubor, který je větší než tato velikost.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Použití <xref:System.IO.StreamReader> ke čtení souboru. Další informace najdete v tématu [základní informace o rozhraní .NET Framework vstup a výstup souborů a systému souborů (Visual Basic)](../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:System.IO.StreamReader>
- [Přístup k souborům v jazyce Visual Basic](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
- [Postupy: Čtení textu ze souborů pomocí třídy StreamReader](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-text-from-files-with-a-streamreader.md)
