---
title: Kódování nelze nastavit na hodnotu Nothing
ms.date: 07/20/2015
ms.assetid: 59f7c731-8291-4a85-bf51-c225e48cdc84
ms.openlocfilehash: 99dbd1a068cabca7f57b6d5e8dd13e1069aede65
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54691326"
---
# <a name="encoding-cannot-be-set-to-nothing"></a><span data-ttu-id="9a553-102">Kódování nelze nastavit na hodnotu Nothing</span><span class="sxs-lookup"><span data-stu-id="9a553-102">Encoding cannot be set to Nothing</span></span>
<span data-ttu-id="9a553-103">Pokus o čtení nebo zápis do souboru se nezdařil, protože parametr `encoding` byla nastavena na `Nothing` , ale vyžaduje platnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="9a553-103">An attempt to read from or write to a file has failed because the parameter `encoding` has been set to `Nothing` but requires a valid value.</span></span>  
  
 <span data-ttu-id="9a553-104"><xref:System.Text.Encoding> slouží k určení, jaké kódování určené k použití při zápisu do souboru.</span><span class="sxs-lookup"><span data-stu-id="9a553-104"><xref:System.Text.Encoding> is used to determine what encoding to use when writing to a file.</span></span> <span data-ttu-id="9a553-105">Výchozí hodnota je UTF-8.</span><span class="sxs-lookup"><span data-stu-id="9a553-105">The default is UTF-8.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9a553-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="9a553-106">To correct this error</span></span>  
  
-   <span data-ttu-id="9a553-107">Zadejte platnou hodnotu pro `encoding` parametru.</span><span class="sxs-lookup"><span data-stu-id="9a553-107">Supply a valid value for the `encoding` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a553-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9a553-108">See also</span></span>
- [<span data-ttu-id="9a553-109">Kódování souborů</span><span class="sxs-lookup"><span data-stu-id="9a553-109">File Encodings</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)
- [<span data-ttu-id="9a553-110">Čtení ze souborů</span><span class="sxs-lookup"><span data-stu-id="9a553-110">Reading from Files</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [<span data-ttu-id="9a553-111">Zápis do souborů</span><span class="sxs-lookup"><span data-stu-id="9a553-111">Writing to Files</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
- [<span data-ttu-id="9a553-112">My.Computer.FileSystem.ReadAllText</span><span class="sxs-lookup"><span data-stu-id="9a553-112">My.Computer.FileSystem.ReadAllText</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A)
- [<span data-ttu-id="9a553-113">My.Computer.FileSystem.WriteAllText</span><span class="sxs-lookup"><span data-stu-id="9a553-113">My.Computer.FileSystem.WriteAllText</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A)
