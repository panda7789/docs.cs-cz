---
title: Chybný režim souboru
ms.date: 07/20/2015
f1_keywords:
- vbrID54
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
ms.openlocfilehash: 534ea2d8316dc29cace798c5ad9b7697a290026f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409866"
---
# <a name="bad-file-mode"></a><span data-ttu-id="5f46e-102">Chybný režim souboru</span><span class="sxs-lookup"><span data-stu-id="5f46e-102">Bad file mode</span></span>
<span data-ttu-id="5f46e-103">Příkazy používané při manipulaci s obsahem souboru musí být vhodné pro režim, ve kterém byl soubor otevřen.</span><span class="sxs-lookup"><span data-stu-id="5f46e-103">Statements used in manipulating file contents must be appropriate to the mode in which the file was opened.</span></span> <span data-ttu-id="5f46e-104">Mezi možné příčiny patří:</span><span class="sxs-lookup"><span data-stu-id="5f46e-104">Possible causes include:</span></span>  
  
- <span data-ttu-id="5f46e-105">`FilePutObject`Příkaz nebo `FileGetObject` určuje sekvenční soubor.</span><span class="sxs-lookup"><span data-stu-id="5f46e-105">A `FilePutObject` or `FileGetObject` statement specifies a sequential file.</span></span>  
  
- <span data-ttu-id="5f46e-106">`Print`Příkaz určuje soubor otevřený pro jiný režim přístupu než `Output` nebo `Append` .</span><span class="sxs-lookup"><span data-stu-id="5f46e-106">A `Print` statement specifies a file opened for an access mode other than `Output` or `Append`.</span></span>  
  
- <span data-ttu-id="5f46e-107">`Input`Příkaz určuje soubor otevřený pro jiný režim přístupu, než`Input`</span><span class="sxs-lookup"><span data-stu-id="5f46e-107">An `Input` statement specifies a file opened for an access mode other than `Input`</span></span>  
  
- <span data-ttu-id="5f46e-108">Pokus o zápis do souboru určeného jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="5f46e-108">An attempt to write to a read-only file.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5f46e-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="5f46e-109">To correct this error</span></span>  
  
- <span data-ttu-id="5f46e-110">Ujistěte se `FilePutObject` , že a že `FileGetObject` odkazují jenom na soubory otevřené pro `Random` nebo `Binary` Access.</span><span class="sxs-lookup"><span data-stu-id="5f46e-110">Make sure `FilePutObject` and `FileGetObject` are only referring to files open for `Random` or `Binary` access.</span></span>  
  
- <span data-ttu-id="5f46e-111">Zajistěte, aby byl `Print` soubor otevřen `Output` pro `Append` přístup nebo režim přístupu.</span><span class="sxs-lookup"><span data-stu-id="5f46e-111">Make sure `Print` specifies a file opened for either `Output` or `Append` access mode.</span></span> <span data-ttu-id="5f46e-112">V takovém případě použijte jiný příkaz k umístění dat do souboru nebo soubor znovu otevřete v příslušném režimu.</span><span class="sxs-lookup"><span data-stu-id="5f46e-112">If not, use a different statement to place data in the file, or reopen the file in an appropriate mode.</span></span>  
  
- <span data-ttu-id="5f46e-113">Ujistěte se, že `Input` Určuje soubor, který je otevřen pro `Input` .</span><span class="sxs-lookup"><span data-stu-id="5f46e-113">Make sure `Input` specifies a file opened for `Input`.</span></span> <span data-ttu-id="5f46e-114">V takovém případě použijte jiný příkaz k umístění dat do souboru nebo znovu otevřete soubor v odpovídajícím režimu.</span><span class="sxs-lookup"><span data-stu-id="5f46e-114">If not, use a different statement to place data in the file or reopen the file in an appropriate mode.</span></span>  
  
- <span data-ttu-id="5f46e-115">Pokud zapisujete do souboru určeného jen pro čtení, změňte stav čtení/zápisu souboru nebo se do něj nepokoušíte zapisovat.</span><span class="sxs-lookup"><span data-stu-id="5f46e-115">If you are writing to a read-only file, change the read/write status of the file or do not try to write to it.</span></span>  
  
- <span data-ttu-id="5f46e-116">Použijte funkce, které jsou k dispozici v `My.Computer.FileSystem` objektu.</span><span class="sxs-lookup"><span data-stu-id="5f46e-116">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f46e-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="5f46e-117">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem>
- [<span data-ttu-id="5f46e-118">Řešení potíží: Čtení z textových souborů a zápis do nich</span><span class="sxs-lookup"><span data-stu-id="5f46e-118">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
