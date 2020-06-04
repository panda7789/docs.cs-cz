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
ms.openlocfilehash: d5e086e77ab6309fa0757ef32b620e0fdbc1f627
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413037"
---
# <a name="how-to-create-files-and-directories-in-isolated-storage"></a><span data-ttu-id="0a947-102">Postupy: Vytváření souborů a adresářů v izolovaném úložišti</span><span class="sxs-lookup"><span data-stu-id="0a947-102">How to: Create Files and Directories in Isolated Storage</span></span>
<span data-ttu-id="0a947-103">Po získání izolovaného úložiště můžete vytvářet adresáře a soubory pro ukládání dat.</span><span class="sxs-lookup"><span data-stu-id="0a947-103">After you have obtained an isolated store, you can create directories and files for storing data.</span></span> <span data-ttu-id="0a947-104">V rámci úložiště jsou zadány názvy souborů a adresářů s ohledem na kořen virtuálního systému souborů.</span><span class="sxs-lookup"><span data-stu-id="0a947-104">Within a store, file and directory names are specified with respect to the root of the virtual file system.</span></span>  
  
 <span data-ttu-id="0a947-105">Chcete-li vytvořit adresář, použijte <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> metodu instance.</span><span class="sxs-lookup"><span data-stu-id="0a947-105">To create a directory, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> instance method.</span></span> <span data-ttu-id="0a947-106">Pokud zadáte podadresář adresáře, který neexistuje, vytvoří se oba adresáře.</span><span class="sxs-lookup"><span data-stu-id="0a947-106">If you specify a subdirectory of an directory that doesn't exist, both directories are created.</span></span> <span data-ttu-id="0a947-107">Pokud zadáte adresář, který již existuje, metoda se vrátí bez vytvoření adresáře a není vyvolána žádná výjimka.</span><span class="sxs-lookup"><span data-stu-id="0a947-107">If you specify a directory that already exists, the method returns without creating a directory, and no exception is thrown.</span></span> <span data-ttu-id="0a947-108">Pokud však zadáte název adresáře, který obsahuje neplatné znaky, <xref:System.IO.IsolatedStorage.IsolatedStorageException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="0a947-108">However, if you specify a directory name that contains invalid characters, an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown.</span></span>  
  
 <span data-ttu-id="0a947-109">Chcete-li vytvořit soubor, použijte <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> metodu.</span><span class="sxs-lookup"><span data-stu-id="0a947-109">To create a file, use  the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="0a947-110">V operačním systému Windows se v názvech souborů a adresářů izolovaného úložiště nerozlišují velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="0a947-110">In the Windows operating system, isolated storage file and directory names are case-insensitive.</span></span> <span data-ttu-id="0a947-111">To znamená, že pokud vytvoříte soubor s názvem `ThisFile.txt` a pak vytvoříte jiný soubor s názvem `THISFILE.TXT` , vytvoří se pouze jeden soubor.</span><span class="sxs-lookup"><span data-stu-id="0a947-111">That is, if you create a file named `ThisFile.txt`, and then create another file named `THISFILE.TXT`, only one file is created.</span></span> <span data-ttu-id="0a947-112">Název souboru uchovává původní velikost písmen pro účely zobrazení.</span><span class="sxs-lookup"><span data-stu-id="0a947-112">The file name keeps its original casing for display purposes.</span></span>  

 <span data-ttu-id="0a947-113">Při vytvoření souboru izolovaného úložiště dojde k vyvolání <xref:System.IO.IsolatedStorage.IsolatedStorageException> , pokud cesta obsahuje adresář, který neexistuje.</span><span class="sxs-lookup"><span data-stu-id="0a947-113">Isolated storage file creation will throw an <xref:System.IO.IsolatedStorage.IsolatedStorageException> if the path contains a directory that does not exist.</span></span>
  
## <a name="example"></a><span data-ttu-id="0a947-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="0a947-114">Example</span></span>  
 <span data-ttu-id="0a947-115">Následující příklad kódu ukazuje, jak vytvořit soubory a adresáře v izolovaném úložišti.</span><span class="sxs-lookup"><span data-stu-id="0a947-115">The following code example illustrates how to create files and directories in an isolated store.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source.cs#1)]
 [!code-vb[Conceptual.IsolatedStorage#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="0a947-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="0a947-116">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>
- [<span data-ttu-id="0a947-117">Izolované úložiště</span><span class="sxs-lookup"><span data-stu-id="0a947-117">Isolated Storage</span></span>](isolated-storage.md)
