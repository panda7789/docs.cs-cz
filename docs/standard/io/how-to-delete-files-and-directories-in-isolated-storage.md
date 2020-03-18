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
ms.openlocfilehash: ec4de3e3a139cfcf66f1f6252c03c467f4ccfbc5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75707854"
---
# <a name="how-to-delete-files-and-directories-in-isolated-storage"></a><span data-ttu-id="b093a-102">Postupy: Odstraňování souborů a adresářů v izolovaném úložišti</span><span class="sxs-lookup"><span data-stu-id="b093a-102">How to: Delete Files and Directories in Isolated Storage</span></span>
<span data-ttu-id="b093a-103">Adresáře a soubory v izolovaném souboru úložiště můžete odstranit.</span><span class="sxs-lookup"><span data-stu-id="b093a-103">You can delete directories and files within an isolated storage file.</span></span> <span data-ttu-id="b093a-104">V rámci úložiště jsou názvy souborů a adresářů závislé na operačním systému a jsou určeny jako relativní ke kořenovému adresáři virtuálního systému souborů.</span><span class="sxs-lookup"><span data-stu-id="b093a-104">Within a store, file and directory names are operating-system dependent and are specified as relative to the root of the virtual file system.</span></span> <span data-ttu-id="b093a-105">V operačních systémech Windows nerozlišují malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="b093a-105">They are not case-sensitive on Windows operating systems.</span></span>  
  
 <span data-ttu-id="b093a-106">Třída <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> poskytuje dvě metody pro odstranění adresářů <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> a <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>souborů: a .</span><span class="sxs-lookup"><span data-stu-id="b093a-106">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> class supplies two methods for deleting directories and files: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>.</span></span> <span data-ttu-id="b093a-107">Pokud <xref:System.IO.IsolatedStorage.IsolatedStorageException> se pokusíte odstranit soubor nebo adresář, který neexistuje, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="b093a-107">An <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown if you try to delete a file or directory that does not exist.</span></span> <span data-ttu-id="b093a-108">Pokud do názvu zahrnete <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> zástupný <xref:System.IO.IsolatedStorage.IsolatedStorageException> znak, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> vyvolá výjimku a vyvolá výjimku. <xref:System.ArgumentException></span><span class="sxs-lookup"><span data-stu-id="b093a-108">If you include a wildcard character in the name, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> throws an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception, and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> throws an <xref:System.ArgumentException> exception.</span></span>  
  
 <span data-ttu-id="b093a-109">Metoda <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> se nezdaří, pokud adresář obsahuje soubory nebo podadresáře.</span><span class="sxs-lookup"><span data-stu-id="b093a-109">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> method fails if the directory contains any files or subdirectories.</span></span> <span data-ttu-id="b093a-110">Metody <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> a <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> můžete použít k načtení existujících souborů a adresářů.</span><span class="sxs-lookup"><span data-stu-id="b093a-110">You can use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> methods to retrieve the existing files and directories.</span></span> <span data-ttu-id="b093a-111">Další informace o prohledání virtuálního systému souborů v úložišti naleznete v tématu [How to: Najít existující soubory a adresáře v izolovaném úložišti](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md).</span><span class="sxs-lookup"><span data-stu-id="b093a-111">For more information about searching the virtual file system of a store, see [How to: Find Existing Files and Directories in Isolated Storage](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b093a-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="b093a-112">Example</span></span>  
 <span data-ttu-id="b093a-113">Následující příklad kódu vytvoří a odstraní několik adresářů a souborů.</span><span class="sxs-lookup"><span data-stu-id="b093a-113">The following code example creates and then deletes several directories and files.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.IsolatedStorage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source4.cs#4)]
 [!code-vb[Conceptual.IsolatedStorage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="b093a-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="b093a-114">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>
- [<span data-ttu-id="b093a-115">Izolované úložiště</span><span class="sxs-lookup"><span data-stu-id="b093a-115">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
