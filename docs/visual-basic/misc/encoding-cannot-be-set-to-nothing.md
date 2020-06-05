---
title: Kódování nelze nastavit na hodnotu Nothing.
ms.date: 07/20/2015
ms.assetid: 59f7c731-8291-4a85-bf51-c225e48cdc84
ms.openlocfilehash: 41565d1aa3b69f6ad92d4bbf2b2f2170014aef87
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84394476"
---
# <a name="encoding-cannot-be-set-to-nothing"></a><span data-ttu-id="0232b-102">Kódování nelze nastavit na hodnotu Nothing.</span><span class="sxs-lookup"><span data-stu-id="0232b-102">Encoding cannot be set to Nothing</span></span>
<span data-ttu-id="0232b-103">Pokus o čtení nebo zápis do souboru se nezdařil, protože parametr byl `encoding` nastaven na, `Nothing` ale vyžaduje platnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0232b-103">An attempt to read from or write to a file has failed because the parameter `encoding` has been set to `Nothing` but requires a valid value.</span></span>  
  
 <span data-ttu-id="0232b-104"><xref:System.Text.Encoding>slouží k určení, jaké kódování se má použít při zápisu do souboru.</span><span class="sxs-lookup"><span data-stu-id="0232b-104"><xref:System.Text.Encoding> is used to determine what encoding to use when writing to a file.</span></span> <span data-ttu-id="0232b-105">Výchozí kódování je UTF-8.</span><span class="sxs-lookup"><span data-stu-id="0232b-105">The default is UTF-8.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0232b-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="0232b-106">To correct this error</span></span>  
  
- <span data-ttu-id="0232b-107">Zadejte platnou hodnotu `encoding` parametru.</span><span class="sxs-lookup"><span data-stu-id="0232b-107">Supply a valid value for the `encoding` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0232b-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="0232b-108">See also</span></span>

- [<span data-ttu-id="0232b-109">Kódování souborů</span><span class="sxs-lookup"><span data-stu-id="0232b-109">File Encodings</span></span>](../developing-apps/programming/drives-directories-files/file-encodings.md)
- [<span data-ttu-id="0232b-110">Čtení ze souborů</span><span class="sxs-lookup"><span data-stu-id="0232b-110">Reading from Files</span></span>](../developing-apps/programming/drives-directories-files/reading-from-files.md)
- [<span data-ttu-id="0232b-111">Zápis do souborů</span><span class="sxs-lookup"><span data-stu-id="0232b-111">Writing to Files</span></span>](../developing-apps/programming/drives-directories-files/writing-to-files.md)
- [<span data-ttu-id="0232b-112">My. Computer. FileSystem. ReadAllText</span><span class="sxs-lookup"><span data-stu-id="0232b-112">My.Computer.FileSystem.ReadAllText</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A)
- [<span data-ttu-id="0232b-113">My. Computer. FileSystem. WriteAllText –</span><span class="sxs-lookup"><span data-stu-id="0232b-113">My.Computer.FileSystem.WriteAllText</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A)
