---
title: 'Postupy: Odstraňování souborů a adresářů v izolovaném úložišti'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data storage using isolated storage, deleting files and directories
- directories [.NET Framework], isolated storage
- files [.NET Framework], isolated storage
- isolated storage, deleting files and directories
- data stores, deleting files and directories
- stores, creating files and directories
- deleting files within isolated stage file
- storing data using isolated storage, deleting files and directories
- deleting directories within isolated stage file
ms.assetid: 8fcc0dea-435b-4d40-ba4d-ba056265c202
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d05b7fa3010ab089d1a97e9a0516096326fd4bb6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797173"
---
# <a name="how-to-delete-files-and-directories-in-isolated-storage"></a><span data-ttu-id="30c26-102">Postupy: Odstraňování souborů a adresářů v izolovaném úložišti</span><span class="sxs-lookup"><span data-stu-id="30c26-102">How to: Delete Files and Directories in Isolated Storage</span></span>
<span data-ttu-id="30c26-103">Můžete odstranit adresářů a souborů v souboru izolovaného úložiště.</span><span class="sxs-lookup"><span data-stu-id="30c26-103">You can delete directories and files within an isolated storage file.</span></span> <span data-ttu-id="30c26-104">Názvy souborů a adresářů v rámci úložiště, jsou závislé na operační systém a jsou určené kořeni virtuálním souborovém systému.</span><span class="sxs-lookup"><span data-stu-id="30c26-104">Within a store, file and directory names are operating-system dependent and are specified as relative to the root of the virtual file system.</span></span> <span data-ttu-id="30c26-105">Nejsou malá a velká písmena v operačních systémech Windows.</span><span class="sxs-lookup"><span data-stu-id="30c26-105">They are not case-sensitive on Windows operating systems.</span></span>  
  
 <span data-ttu-id="30c26-106"><xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> Třída poskytuje dvě metody pro odstranění adresářů a souborů: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> a <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>.</span><span class="sxs-lookup"><span data-stu-id="30c26-106">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> class supplies two methods for deleting directories and files: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>.</span></span> <span data-ttu-id="30c26-107"><xref:System.IO.IsolatedStorage.IsolatedStorageException> Je vyvolána výjimka, pokud se pokusíte odstranit soubor nebo adresář, který neexistuje.</span><span class="sxs-lookup"><span data-stu-id="30c26-107">An <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown if you try to delete a file or directory that does not exist.</span></span> <span data-ttu-id="30c26-108">Pokud zahrnete zástupných znaků v názvu, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> vyvolá <xref:System.IO.IsolatedStorage.IsolatedStorageException> výjimky, a <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> vyvolá <xref:System.ArgumentException> výjimky.</span><span class="sxs-lookup"><span data-stu-id="30c26-108">If you include a wildcard character in the name, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> throws an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception, and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> throws an <xref:System.ArgumentException> exception.</span></span>  
  
 <span data-ttu-id="30c26-109"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> Metoda selže, pokud adresář obsahuje všechny soubory a podadresáře.</span><span class="sxs-lookup"><span data-stu-id="30c26-109">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> method fails if the directory contains any files or subdirectories.</span></span> <span data-ttu-id="30c26-110">Můžete použít <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> a <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> metody pro načtení existujících souborů a adresářů.</span><span class="sxs-lookup"><span data-stu-id="30c26-110">You can use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> methods to retrieve the existing files and directories.</span></span> <span data-ttu-id="30c26-111">Další informace o hledání virtuálním souborovém systému úložiště najdete v tématu [jak: Hledání existujících souborů a adresářů v izolovaném úložišti](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md).</span><span class="sxs-lookup"><span data-stu-id="30c26-111">For more information about searching the virtual file system of a store, see [How to: Find Existing Files and Directories in Isolated Storage](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="30c26-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="30c26-112">Example</span></span>  
 <span data-ttu-id="30c26-113">Následující příklad kódu vytvoří a odstraní několik adresářů a souborů.</span><span class="sxs-lookup"><span data-stu-id="30c26-113">The following code example creates and then deletes several directories and files.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.IsolatedStorage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source4.cs#4)]
 [!code-vb[Conceptual.IsolatedStorage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="30c26-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="30c26-114">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>
- [<span data-ttu-id="30c26-115">Izolované úložiště</span><span class="sxs-lookup"><span data-stu-id="30c26-115">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
