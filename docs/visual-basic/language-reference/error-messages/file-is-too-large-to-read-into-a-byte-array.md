---
title: Soubor je pro načtení do bajtového pole příliš velký.
ms.date: 07/20/2015
ms.assetid: 686630a6-a439-46c7-8d7b-34613ae4c5d8
ms.openlocfilehash: 0c7d35e08eeb42e35c4c40e47434a64393d829b1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58831511"
---
# <a name="file-is-too-large-to-read-into-a-byte-array"></a><span data-ttu-id="2d551-102">Soubor je pro načtení do bajtového pole příliš velký.</span><span class="sxs-lookup"><span data-stu-id="2d551-102">File is too large to read into a byte array</span></span>
<span data-ttu-id="2d551-103">Velikost souboru, který se pokoušíte načtení do bajtového pole překračuje 4 GB.</span><span class="sxs-lookup"><span data-stu-id="2d551-103">The size of the file you are attempting to read into a byte array exceeds 4 GB.</span></span> <span data-ttu-id="2d551-104">`My.Computer.FileSystem.ReadAllBytes` Metoda nemůže přečíst soubor, který je větší než tato velikost.</span><span class="sxs-lookup"><span data-stu-id="2d551-104">The `My.Computer.FileSystem.ReadAllBytes` method cannot read a file that exceeds this size.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2d551-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="2d551-105">To correct this error</span></span>  
  
-   <span data-ttu-id="2d551-106">Použití <xref:System.IO.StreamReader> ke čtení souboru.</span><span class="sxs-lookup"><span data-stu-id="2d551-106">Use a <xref:System.IO.StreamReader> to read the file.</span></span> <span data-ttu-id="2d551-107">Další informace najdete v tématu [základní informace o rozhraní .NET Framework vstup a výstup souborů a systému souborů (Visual Basic)](../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).</span><span class="sxs-lookup"><span data-stu-id="2d551-107">For more information, see [Basics of .NET Framework File I/O and the File System (Visual Basic)](../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d551-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d551-108">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:System.IO.StreamReader>
- [<span data-ttu-id="2d551-109">Přístup k souborům v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2d551-109">File Access with Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
- [<span data-ttu-id="2d551-110">Postupy: Čtení textu ze souborů pomocí třídy StreamReader</span><span class="sxs-lookup"><span data-stu-id="2d551-110">How to: Read Text from Files with a StreamReader</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-text-from-files-with-a-streamreader.md)
