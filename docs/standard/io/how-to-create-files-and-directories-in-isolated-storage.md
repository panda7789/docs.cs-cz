---
title: 'Postupy: Vytváření souborů a adresářů v izolovaném úložišti'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- directories [.NET Framework], isolated storage
- files [.NET Framework], isolated storage
- isolated storage, creating files and directories
- data stores, creating files and directories
- data storage using isolated storage, creating files and directories
- stores, creating files and directories
- storing data using isolated storage, creating files and directories
ms.assetid: 2ca4d2a4-809b-4f00-bc08-bf4a64d3a5c3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 92f4b686a5a2bdc74ff3f0f68de4c6b2048da5a1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61751907"
---
# <a name="how-to-create-files-and-directories-in-isolated-storage"></a><span data-ttu-id="01c7f-102">Postupy: Vytváření souborů a adresářů v izolovaném úložišti</span><span class="sxs-lookup"><span data-stu-id="01c7f-102">How to: Create Files and Directories in Isolated Storage</span></span>
<span data-ttu-id="01c7f-103">Po získání izolovaného úložiště, můžete vytvořit adresářů a souborů k ukládání dat.</span><span class="sxs-lookup"><span data-stu-id="01c7f-103">After you have obtained an isolated store, you can create directories and files for storing data.</span></span> <span data-ttu-id="01c7f-104">V rámci úložiště jsou zadané názvy souborů a adresářů s ohledem na kořenovém virtuálním souborovém systému.</span><span class="sxs-lookup"><span data-stu-id="01c7f-104">Within a store, file and directory names are specified with respect to the root of the virtual file system.</span></span>  
  
 <span data-ttu-id="01c7f-105">Chcete-li vytvořit adresář, použijte <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> metodu instance.</span><span class="sxs-lookup"><span data-stu-id="01c7f-105">To create a directory, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> instance method.</span></span> <span data-ttu-id="01c7f-106">Pokud zadáte podadresáře adresáře, který neexistuje, vytvoří se oba adresáře.</span><span class="sxs-lookup"><span data-stu-id="01c7f-106">If you specify a subdirectory of an directory that doesn't exist, both directories are created.</span></span> <span data-ttu-id="01c7f-107">Pokud určíte adresář, který již existuje, metoda vrátí bez vytvoření adresáře a není vyvolána žádná výjimka.</span><span class="sxs-lookup"><span data-stu-id="01c7f-107">If you specify a directory that already exists, the method returns without creating a directory, and no exception is thrown.</span></span> <span data-ttu-id="01c7f-108">Nicméně, pokud zadáte název adresáře, který obsahuje neplatné znaky, <xref:System.IO.IsolatedStorage.IsolatedStorageException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="01c7f-108">However, if you specify a directory name that contains invalid characters, an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown.</span></span>  
  
 <span data-ttu-id="01c7f-109">Chcete-li vytvořit soubor, použijte <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="01c7f-109">To create a file, use  the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="01c7f-110">V operačním systému Windows, izolované úložiště souboru a adresáře názvy jsou malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="01c7f-110">In the Windows operating system, isolated storage file and directory names are case-insensitive.</span></span> <span data-ttu-id="01c7f-111">To znamená pokud vytvoříte soubor s názvem `ThisFile.txt`a pak vytvořte jiný soubor s názvem `THISFILE.TXT`, je vytvořen pouze jeden soubor.</span><span class="sxs-lookup"><span data-stu-id="01c7f-111">That is, if you create a file named `ThisFile.txt`, and then create another file named `THISFILE.TXT`, only one file is created.</span></span> <span data-ttu-id="01c7f-112">Název souboru udržuje jeho původní malých a velkých písmen pro účely zobrazení.</span><span class="sxs-lookup"><span data-stu-id="01c7f-112">The file name keeps its original casing for display purposes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01c7f-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="01c7f-113">Example</span></span>  
 <span data-ttu-id="01c7f-114">Následující příklad kódu ukazuje, jak vytváření souborů a adresářů v izolovaném úložišti.</span><span class="sxs-lookup"><span data-stu-id="01c7f-114">The following code example illustrates how to create files and directories in an isolated store.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source.cs#1)]
 [!code-vb[Conceptual.IsolatedStorage#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="01c7f-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="01c7f-115">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>
- [<span data-ttu-id="01c7f-116">Izolované úložiště</span><span class="sxs-lookup"><span data-stu-id="01c7f-116">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
