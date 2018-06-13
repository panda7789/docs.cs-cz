---
title: Soubor je pro načtení do bajtového pole příliš velký.
ms.date: 07/20/2015
ms.assetid: 686630a6-a439-46c7-8d7b-34613ae4c5d8
ms.openlocfilehash: 1b04d47cab77269a0ce84ef77c162a4401d99d9e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585922"
---
# <a name="file-is-too-large-to-read-into-a-byte-array"></a><span data-ttu-id="f31ed-102">Soubor je pro načtení do bajtového pole příliš velký.</span><span class="sxs-lookup"><span data-stu-id="f31ed-102">File is too large to read into a byte array</span></span>
<span data-ttu-id="f31ed-103">Velikost souboru, který se pokoušíte načíst do bajtového pole překračuje 4 GB.</span><span class="sxs-lookup"><span data-stu-id="f31ed-103">The size of the file you are attempting to read into a byte array exceeds 4 GB.</span></span> <span data-ttu-id="f31ed-104">`My.Computer.FileSystem.ReadAllBytes` Metoda nemůže přečíst soubor, který překračuje této velikosti.</span><span class="sxs-lookup"><span data-stu-id="f31ed-104">The `My.Computer.FileSystem.ReadAllBytes` method cannot read a file that exceeds this size.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f31ed-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="f31ed-105">To correct this error</span></span>  
  
-   <span data-ttu-id="f31ed-106">Použití <xref:System.IO.StreamReader> pro čtení tohoto souboru.</span><span class="sxs-lookup"><span data-stu-id="f31ed-106">Use a <xref:System.IO.StreamReader> to read the file.</span></span> <span data-ttu-id="f31ed-107">Další informace najdete v tématu [základní informace o rozhraní .NET Framework souboru vstupně-výstupních operací a systému souborů (Visual Basic)](../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).</span><span class="sxs-lookup"><span data-stu-id="f31ed-107">For more information, see [Basics of .NET Framework File I/O and the File System (Visual Basic)](../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f31ed-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="f31ed-108">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>  
 <xref:System.IO.StreamReader>  
 [<span data-ttu-id="f31ed-109">Přístup k souborům v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f31ed-109">File Access with Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)  
 [<span data-ttu-id="f31ed-110">Postupy: Čtení textu ze souborů pomocí třídy StreamReader</span><span class="sxs-lookup"><span data-stu-id="f31ed-110">How to: Read Text from Files with a StreamReader</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-text-from-files-with-a-streamreader.md)
