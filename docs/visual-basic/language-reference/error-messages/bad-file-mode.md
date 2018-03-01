---
title: "Chybný režim souboru"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID54
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a540135727eb97f4df5027e2ded7271e21bb4648
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="bad-file-mode"></a><span data-ttu-id="90206-102">Chybný režim souboru</span><span class="sxs-lookup"><span data-stu-id="90206-102">Bad file mode</span></span>
<span data-ttu-id="90206-103">Příkazy, které jsou používány práce s obsahem souboru musí být vhodné pro režim, ve kterém byl soubor otevřít.</span><span class="sxs-lookup"><span data-stu-id="90206-103">Statements used in manipulating file contents must be appropriate to the mode in which the file was opened.</span></span> <span data-ttu-id="90206-104">Možné příčiny:</span><span class="sxs-lookup"><span data-stu-id="90206-104">Possible causes include:</span></span>  
  
-   <span data-ttu-id="90206-105">A `FilePutObject` nebo `FileGetObject` příkaz určuje sekvenční soubor.</span><span class="sxs-lookup"><span data-stu-id="90206-105">A `FilePutObject` or `FileGetObject` statement specifies a sequential file.</span></span>  
  
-   <span data-ttu-id="90206-106">A `Print` příkaz určuje soubor otevřít pro přístupovém režimu jiné než `Output` nebo `Append`.</span><span class="sxs-lookup"><span data-stu-id="90206-106">A `Print` statement specifies a file opened for an access mode other than `Output` or `Append`.</span></span>  
  
-   <span data-ttu-id="90206-107">`Input` Příkaz určuje soubor otevřít pro přístupovém režimu jiné než`Input`</span><span class="sxs-lookup"><span data-stu-id="90206-107">An `Input` statement specifies a file opened for an access mode other than `Input`</span></span>  
  
-   <span data-ttu-id="90206-108">Pokus o zápis do souboru jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="90206-108">An attempt to write to a read-only file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="90206-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="90206-109">To correct this error</span></span>  
  
-   <span data-ttu-id="90206-110">Zajistěte, aby `FilePutObject` a `FileGetObject` jsou pouze odkazy na soubory otevřené pro `Random` nebo `Binary` přístup.</span><span class="sxs-lookup"><span data-stu-id="90206-110">Make sure `FilePutObject` and `FileGetObject` are only referring to files open for `Random` or `Binary` access.</span></span>  
  
-   <span data-ttu-id="90206-111">Zajistěte, aby `Print` Určuje soubor otevřít pro buď `Output` nebo `Append` režim přístupu.</span><span class="sxs-lookup"><span data-stu-id="90206-111">Make sure `Print` specifies a file opened for either `Output` or `Append` access mode.</span></span> <span data-ttu-id="90206-112">Pokud ne, použít jiný příkaz umístit data v souboru nebo znovu otevřete soubor v odpovídající režim.</span><span class="sxs-lookup"><span data-stu-id="90206-112">If not, use a different statement to place data in the file, or reopen the file in an appropriate mode.</span></span>  
  
-   <span data-ttu-id="90206-113">Zajistěte, aby `Input` Určuje soubor otevřít pro `Input`.</span><span class="sxs-lookup"><span data-stu-id="90206-113">Make sure `Input` specifies a file opened for `Input`.</span></span> <span data-ttu-id="90206-114">Pokud ne, použijte jiný příkaz umístit data v souboru nebo znovu otevřete soubor v odpovídající režim.</span><span class="sxs-lookup"><span data-stu-id="90206-114">If not, use a different statement to place data in the file or reopen the file in an appropriate mode.</span></span>  
  
-   <span data-ttu-id="90206-115">Pokud píšete do souboru jen pro čtení, změňte stav pro čtení a zápis souboru nebo Nepokoušejte se do něj zapisovat.</span><span class="sxs-lookup"><span data-stu-id="90206-115">If you are writing to a read-only file, change the read/write status of the file or do not try to write to it.</span></span>  
  
-   <span data-ttu-id="90206-116">Používat funkce, které jsou k dispozici v `My.Computer.FileSystem` objektu.</span><span class="sxs-lookup"><span data-stu-id="90206-116">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90206-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="90206-117">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileSystem>  
 [<span data-ttu-id="90206-118">Řešení potíží: Čtení a zápis do textových souborů</span><span class="sxs-lookup"><span data-stu-id="90206-118">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
