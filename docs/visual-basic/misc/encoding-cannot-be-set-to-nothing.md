---
title: "Kódování nelze nastavit na hodnotu Nothing"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: 59f7c731-8291-4a85-bf51-c225e48cdc84
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: daa3567e47f170c64b45cbb9e49d7fa0026b8903
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="encoding-cannot-be-set-to-nothing"></a><span data-ttu-id="ce8f9-102">Kódování nelze nastavit na hodnotu Nothing</span><span class="sxs-lookup"><span data-stu-id="ce8f9-102">Encoding cannot be set to Nothing</span></span>
<span data-ttu-id="ce8f9-103">Pokus o číst nebo zapisovat do souboru se nezdařila, protože parametr `encoding` byla nastavena na `Nothing` , ale vyžaduje platnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ce8f9-103">An attempt to read from or write to a file has failed because the parameter `encoding` has been set to `Nothing` but requires a valid value.</span></span>  
  
 <span data-ttu-id="ce8f9-104"><xref:System.Text.Encoding>slouží k určení, jaké kódování určené k použití při zápisu do souboru.</span><span class="sxs-lookup"><span data-stu-id="ce8f9-104"><xref:System.Text.Encoding> is used to determine what encoding to use when writing to a file.</span></span> <span data-ttu-id="ce8f9-105">Výchozí hodnota je UTF-8.</span><span class="sxs-lookup"><span data-stu-id="ce8f9-105">The default is UTF-8.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ce8f9-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="ce8f9-106">To correct this error</span></span>  
  
-   <span data-ttu-id="ce8f9-107">Zadejte platnou hodnotu `encoding` parametr.</span><span class="sxs-lookup"><span data-stu-id="ce8f9-107">Supply a valid value for the `encoding` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce8f9-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="ce8f9-108">See Also</span></span>  
 [<span data-ttu-id="ce8f9-109">Kódování souborů</span><span class="sxs-lookup"><span data-stu-id="ce8f9-109">File Encodings</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)  
 [<span data-ttu-id="ce8f9-110">Čtení ze souborů</span><span class="sxs-lookup"><span data-stu-id="ce8f9-110">Reading from Files</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 [<span data-ttu-id="ce8f9-111">Zápis do souborů</span><span class="sxs-lookup"><span data-stu-id="ce8f9-111">Writing to Files</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)  
 [<span data-ttu-id="ce8f9-112">My.Computer.FileSystem.ReadAllText – metoda</span><span class="sxs-lookup"><span data-stu-id="ce8f9-112">My.Computer.FileSystem.ReadAllText Method</span></span>](http://msdn.microsoft.com/en-us/3a7ac8be-fb1d-4087-bc65-167d6754d57f)  
 [<span data-ttu-id="ce8f9-113">My.Computer.FileSystem.WriteAllText – metoda</span><span class="sxs-lookup"><span data-stu-id="ce8f9-113">My.Computer.FileSystem.WriteAllText Method</span></span>](http://msdn.microsoft.com/en-us/f507460c-87d9-4504-b74f-3ff825c7d5c4)
