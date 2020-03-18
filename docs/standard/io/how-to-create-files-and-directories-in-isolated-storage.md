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
ms.openlocfilehash: 83e8c800dc74d9689f1bfdb506a6b454e87b36ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75707867"
---
# <a name="how-to-create-files-and-directories-in-isolated-storage"></a><span data-ttu-id="ff9d1-102">Postupy: Vytváření souborů a adresářů v izolovaném úložišti</span><span class="sxs-lookup"><span data-stu-id="ff9d1-102">How to: Create Files and Directories in Isolated Storage</span></span>
<span data-ttu-id="ff9d1-103">Po získání izolovaného úložiště můžete vytvořit adresáře a soubory pro ukládání dat.</span><span class="sxs-lookup"><span data-stu-id="ff9d1-103">After you have obtained an isolated store, you can create directories and files for storing data.</span></span> <span data-ttu-id="ff9d1-104">V rámci úložiště jsou názvy souborů a adresářů určeny s ohledem na kořenový adresář virtuálního systému souborů.</span><span class="sxs-lookup"><span data-stu-id="ff9d1-104">Within a store, file and directory names are specified with respect to the root of the virtual file system.</span></span>  
  
 <span data-ttu-id="ff9d1-105">Chcete-li vytvořit adresář, použijte metodu <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> instance.</span><span class="sxs-lookup"><span data-stu-id="ff9d1-105">To create a directory, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> instance method.</span></span> <span data-ttu-id="ff9d1-106">Pokud zadáte podadresář adresáře, který neexistuje, budou vytvořeny oba adresáře.</span><span class="sxs-lookup"><span data-stu-id="ff9d1-106">If you specify a subdirectory of an directory that doesn't exist, both directories are created.</span></span> <span data-ttu-id="ff9d1-107">Pokud zadáte adresář, který již existuje, metoda se vrátí bez vytvoření adresáře a není vyvolána žádná výjimka.</span><span class="sxs-lookup"><span data-stu-id="ff9d1-107">If you specify a directory that already exists, the method returns without creating a directory, and no exception is thrown.</span></span> <span data-ttu-id="ff9d1-108">Pokud však zadáte název adresáře, který <xref:System.IO.IsolatedStorage.IsolatedStorageException> obsahuje neplatné znaky, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="ff9d1-108">However, if you specify a directory name that contains invalid characters, an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown.</span></span>  
  
 <span data-ttu-id="ff9d1-109">Chcete-li vytvořit soubor, použijte metodu. <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="ff9d1-109">To create a file, use  the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="ff9d1-110">V operačním systému Windows izolované úložiště soubor a názvy adresářů jsou malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="ff9d1-110">In the Windows operating system, isolated storage file and directory names are case-insensitive.</span></span> <span data-ttu-id="ff9d1-111">To znamená, že pokud `ThisFile.txt`vytvoříte soubor s `THISFILE.TXT`názvem a potom vytvoříte další soubor s názvem , bude vytvořen pouze jeden soubor.</span><span class="sxs-lookup"><span data-stu-id="ff9d1-111">That is, if you create a file named `ThisFile.txt`, and then create another file named `THISFILE.TXT`, only one file is created.</span></span> <span data-ttu-id="ff9d1-112">Název souboru zachová původní velikost písmen pro účely zobrazení.</span><span class="sxs-lookup"><span data-stu-id="ff9d1-112">The file name keeps its original casing for display purposes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff9d1-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="ff9d1-113">Example</span></span>  
 <span data-ttu-id="ff9d1-114">Následující příklad kódu ukazuje, jak vytvořit soubory a adresáře v izolovaném úložišti.</span><span class="sxs-lookup"><span data-stu-id="ff9d1-114">The following code example illustrates how to create files and directories in an isolated store.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source.cs#1)]
 [!code-vb[Conceptual.IsolatedStorage#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ff9d1-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="ff9d1-115">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>
- [<span data-ttu-id="ff9d1-116">Izolované úložiště</span><span class="sxs-lookup"><span data-stu-id="ff9d1-116">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
