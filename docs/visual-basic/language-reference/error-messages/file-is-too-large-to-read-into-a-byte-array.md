---
title: Soubor je pro načtení do bajtového pole příliš velký.
ms.date: 07/20/2015
ms.assetid: 686630a6-a439-46c7-8d7b-34613ae4c5d8
ms.openlocfilehash: b81fc9332d5f1347404fcdd73bce72b6b09778b9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363121"
---
# <a name="file-is-too-large-to-read-into-a-byte-array"></a>Soubor je pro načtení do bajtového pole příliš velký.
Velikost souboru, který se pokoušíte načíst do pole bajtů, je větší než 4 GB. `My.Computer.FileSystem.ReadAllBytes`Metoda nemůže přečíst soubor, který překračuje tuto velikost.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Pro <xref:System.IO.StreamReader> čtení souboru použijte. Další informace najdete v tématu [základy .NET Frameworkch vstupně-výstupních operací souborů a systému souborů (Visual Basic)](../../developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:System.IO.StreamReader>
- [Přístup k souborům v jazyce Visual Basic](../../developing-apps/programming/drives-directories-files/file-access.md)
- [Postupy: Čtení textu ze souborů pomocí třídy StreamReader](../../developing-apps/programming/drives-directories-files/how-to-read-text-from-files-with-a-streamreader.md)
