---
title: Soubor je pro načtení do bajtového pole příliš velký.
ms.date: 07/20/2015
ms.assetid: 686630a6-a439-46c7-8d7b-34613ae4c5d8
ms.openlocfilehash: a842205e9184355e4ea750ea2eb32e4bcf05a14d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665105"
---
# <a name="file-is-too-large-to-read-into-a-byte-array"></a><span data-ttu-id="fcea5-102">Soubor je pro načtení do bajtového pole příliš velký.</span><span class="sxs-lookup"><span data-stu-id="fcea5-102">File is too large to read into a byte array</span></span>
<span data-ttu-id="fcea5-103">Velikost souboru, který se pokoušíte načtení do bajtového pole překračuje 4 GB.</span><span class="sxs-lookup"><span data-stu-id="fcea5-103">The size of the file you are attempting to read into a byte array exceeds 4 GB.</span></span> <span data-ttu-id="fcea5-104">`My.Computer.FileSystem.ReadAllBytes` Metoda nemůže přečíst soubor, který je větší než tato velikost.</span><span class="sxs-lookup"><span data-stu-id="fcea5-104">The `My.Computer.FileSystem.ReadAllBytes` method cannot read a file that exceeds this size.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fcea5-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="fcea5-105">To correct this error</span></span>  
  
- <span data-ttu-id="fcea5-106">Použití <xref:System.IO.StreamReader> ke čtení souboru.</span><span class="sxs-lookup"><span data-stu-id="fcea5-106">Use a <xref:System.IO.StreamReader> to read the file.</span></span> <span data-ttu-id="fcea5-107">Další informace najdete v tématu [základní informace o rozhraní .NET Framework vstup a výstup souborů a systému souborů (Visual Basic)](../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).</span><span class="sxs-lookup"><span data-stu-id="fcea5-107">For more information, see [Basics of .NET Framework File I/O and the File System (Visual Basic)](../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcea5-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fcea5-108">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:System.IO.StreamReader>
- [<span data-ttu-id="fcea5-109">Přístup k souborům v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fcea5-109">File Access with Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
- [<span data-ttu-id="fcea5-110">Postupy: Čtení textu ze souborů pomocí třídy StreamReader</span><span class="sxs-lookup"><span data-stu-id="fcea5-110">How to: Read Text from Files with a StreamReader</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-text-from-files-with-a-streamreader.md)
