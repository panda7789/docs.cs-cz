---
title: Chybný režim souboru
ms.date: 07/20/2015
f1_keywords:
- vbrID54
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
ms.openlocfilehash: d3d0ebd003f178567ec9e9b19d6baccb8bc15f60
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58819980"
---
# <a name="bad-file-mode"></a><span data-ttu-id="b5288-102">Chybný režim souboru</span><span class="sxs-lookup"><span data-stu-id="b5288-102">Bad file mode</span></span>
<span data-ttu-id="b5288-103">Příkazy používané práce s obsahem souboru musí být příslušný režim, ve kterém soubor byl otevřen.</span><span class="sxs-lookup"><span data-stu-id="b5288-103">Statements used in manipulating file contents must be appropriate to the mode in which the file was opened.</span></span> <span data-ttu-id="b5288-104">Mezi možné příčiny patří:</span><span class="sxs-lookup"><span data-stu-id="b5288-104">Possible causes include:</span></span>  
  
-   <span data-ttu-id="b5288-105">A `FilePutObject` nebo `FileGetObject` příkaz určuje sekvenčního souboru.</span><span class="sxs-lookup"><span data-stu-id="b5288-105">A `FilePutObject` or `FileGetObject` statement specifies a sequential file.</span></span>  
  
-   <span data-ttu-id="b5288-106">A `Print` příkaz určuje soubor otevřen pro přístupový režim jiné než `Output` nebo `Append`.</span><span class="sxs-lookup"><span data-stu-id="b5288-106">A `Print` statement specifies a file opened for an access mode other than `Output` or `Append`.</span></span>  
  
-   <span data-ttu-id="b5288-107">`Input` Příkaz určuje soubor otevřen pro přístupový režim jiné než `Input`</span><span class="sxs-lookup"><span data-stu-id="b5288-107">An `Input` statement specifies a file opened for an access mode other than `Input`</span></span>  
  
-   <span data-ttu-id="b5288-108">Pokus o zápis do souboru jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="b5288-108">An attempt to write to a read-only file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b5288-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="b5288-109">To correct this error</span></span>  
  
-   <span data-ttu-id="b5288-110">Ujistěte se, že `FilePutObject` a `FileGetObject` pouze odkazují na soubory otevřené pro `Random` nebo `Binary` přístup.</span><span class="sxs-lookup"><span data-stu-id="b5288-110">Make sure `FilePutObject` and `FileGetObject` are only referring to files open for `Random` or `Binary` access.</span></span>  
  
-   <span data-ttu-id="b5288-111">Ujistěte se, že `Print` Určuje soubor otevřen pro buď `Output` nebo `Append` přístupovém režimu.</span><span class="sxs-lookup"><span data-stu-id="b5288-111">Make sure `Print` specifies a file opened for either `Output` or `Append` access mode.</span></span> <span data-ttu-id="b5288-112">V opačném případě použijte jiný příkaz umístit data v souboru nebo znovu otevřete soubor v odpovídající režim.</span><span class="sxs-lookup"><span data-stu-id="b5288-112">If not, use a different statement to place data in the file, or reopen the file in an appropriate mode.</span></span>  
  
-   <span data-ttu-id="b5288-113">Ujistěte se, že `Input` Určuje soubor otevřen pro `Input`.</span><span class="sxs-lookup"><span data-stu-id="b5288-113">Make sure `Input` specifies a file opened for `Input`.</span></span> <span data-ttu-id="b5288-114">Pokud ne, použijte jiný příkaz umístit data souboru nebo znovu otevřete soubor v odpovídající režim.</span><span class="sxs-lookup"><span data-stu-id="b5288-114">If not, use a different statement to place data in the file or reopen the file in an appropriate mode.</span></span>  
  
-   <span data-ttu-id="b5288-115">Při psaní do souboru jen pro čtení, změňte stav čtení a zápis souboru nebo Nepokoušejte se do ní zapisovat.</span><span class="sxs-lookup"><span data-stu-id="b5288-115">If you are writing to a read-only file, change the read/write status of the file or do not try to write to it.</span></span>  
  
-   <span data-ttu-id="b5288-116">Použití funkce, která je dostupná v `My.Computer.FileSystem` objektu.</span><span class="sxs-lookup"><span data-stu-id="b5288-116">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5288-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b5288-117">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem>
- [<span data-ttu-id="b5288-118">Odstraňování potíží: Čtení a zápis do textových souborů</span><span class="sxs-lookup"><span data-stu-id="b5288-118">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
