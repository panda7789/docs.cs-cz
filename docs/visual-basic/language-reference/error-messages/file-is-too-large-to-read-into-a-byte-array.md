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
# <a name="file-is-too-large-to-read-into-a-byte-array"></a><span data-ttu-id="7066a-102">Soubor je pro načtení do bajtového pole příliš velký.</span><span class="sxs-lookup"><span data-stu-id="7066a-102">File is too large to read into a byte array</span></span>
<span data-ttu-id="7066a-103">Velikost souboru, který se pokoušíte načíst do bajtového pole překračuje 4 GB.</span><span class="sxs-lookup"><span data-stu-id="7066a-103">The size of the file you are attempting to read into a byte array exceeds 4 GB.</span></span> <span data-ttu-id="7066a-104">`My.Computer.FileSystem.ReadAllBytes` Metoda nemůže přečíst soubor, který překračuje této velikosti.</span><span class="sxs-lookup"><span data-stu-id="7066a-104">The `My.Computer.FileSystem.ReadAllBytes` method cannot read a file that exceeds this size.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7066a-105">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="7066a-105">To correct this error</span></span>  
  
-   <span data-ttu-id="7066a-106">Použití <xref:System.IO.StreamReader> pro čtení tohoto souboru.</span><span class="sxs-lookup"><span data-stu-id="7066a-106">Use a <xref:System.IO.StreamReader> to read the file.</span></span> <span data-ttu-id="7066a-107">Další informace najdete v tématu [základní informace o rozhraní .NET Framework souboru vstupně-výstupních operací a systému souborů (Visual Basic)](../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).</span><span class="sxs-lookup"><span data-stu-id="7066a-107">For more information, see [Basics of .NET Framework File I/O and the File System (Visual Basic)](../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7066a-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="7066a-108">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>  
 <xref:System.IO.StreamReader>  
 [<span data-ttu-id="7066a-109">Přístup k souborům v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7066a-109">File Access with Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)  
 [<span data-ttu-id="7066a-110">Postupy: čtení textu ze souborů pomocí třídy StreamReader</span><span class="sxs-lookup"><span data-stu-id="7066a-110">How to: Read Text from Files with a StreamReader</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-text-from-files-with-a-streamreader.md)
