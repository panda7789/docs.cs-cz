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
# <a name="file-is-too-large-to-read-into-a-byte-array"></a><span data-ttu-id="c915a-102">Soubor je pro načtení do bajtového pole příliš velký.</span><span class="sxs-lookup"><span data-stu-id="c915a-102">File is too large to read into a byte array</span></span>
<span data-ttu-id="c915a-103">Velikost souboru, který se pokoušíte načíst do pole bajtů, je větší než 4 GB.</span><span class="sxs-lookup"><span data-stu-id="c915a-103">The size of the file you are attempting to read into a byte array exceeds 4 GB.</span></span> <span data-ttu-id="c915a-104">`My.Computer.FileSystem.ReadAllBytes`Metoda nemůže přečíst soubor, který překračuje tuto velikost.</span><span class="sxs-lookup"><span data-stu-id="c915a-104">The `My.Computer.FileSystem.ReadAllBytes` method cannot read a file that exceeds this size.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c915a-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="c915a-105">To correct this error</span></span>  
  
- <span data-ttu-id="c915a-106">Pro <xref:System.IO.StreamReader> čtení souboru použijte.</span><span class="sxs-lookup"><span data-stu-id="c915a-106">Use a <xref:System.IO.StreamReader> to read the file.</span></span> <span data-ttu-id="c915a-107">Další informace najdete v tématu [základy .NET Frameworkch vstupně-výstupních operací souborů a systému souborů (Visual Basic)](../../developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).</span><span class="sxs-lookup"><span data-stu-id="c915a-107">For more information, see [Basics of .NET Framework File I/O and the File System (Visual Basic)](../../developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c915a-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="c915a-108">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:System.IO.StreamReader>
- [<span data-ttu-id="c915a-109">Přístup k souborům v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c915a-109">File Access with Visual Basic</span></span>](../../developing-apps/programming/drives-directories-files/file-access.md)
- [<span data-ttu-id="c915a-110">Postupy: Čtení textu ze souborů pomocí třídy StreamReader</span><span class="sxs-lookup"><span data-stu-id="c915a-110">How to: Read Text from Files with a StreamReader</span></span>](../../developing-apps/programming/drives-directories-files/how-to-read-text-from-files-with-a-streamreader.md)
