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
ms.openlocfilehash: dc84fefbde1177993b17e9ec687a1ef759b74735
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291900"
---
# <a name="how-to-delete-files-and-directories-in-isolated-storage"></a><span data-ttu-id="cab56-102">Postupy: Odstraňování souborů a adresářů v izolovaném úložišti</span><span class="sxs-lookup"><span data-stu-id="cab56-102">How to: Delete Files and Directories in Isolated Storage</span></span>
<span data-ttu-id="cab56-103">V souboru izolovaného úložiště můžete odstraňovat adresáře a soubory.</span><span class="sxs-lookup"><span data-stu-id="cab56-103">You can delete directories and files within an isolated storage file.</span></span> <span data-ttu-id="cab56-104">V rámci úložiště jsou názvy souborů a adresářů závislé na operačním systému a jsou určené jako relativní ke kořenu virtuálního systému souborů.</span><span class="sxs-lookup"><span data-stu-id="cab56-104">Within a store, file and directory names are operating-system dependent and are specified as relative to the root of the virtual file system.</span></span> <span data-ttu-id="cab56-105">V operačních systémech Windows nerozlišují velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="cab56-105">They are not case-sensitive on Windows operating systems.</span></span>  
  
 <span data-ttu-id="cab56-106"><xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>Třída poskytuje dvě metody pro odstraňování adresářů a souborů: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> a <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> .</span><span class="sxs-lookup"><span data-stu-id="cab56-106">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> class supplies two methods for deleting directories and files: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>.</span></span> <span data-ttu-id="cab56-107"><xref:System.IO.IsolatedStorage.IsolatedStorageException>Pokud se pokusíte odstranit soubor nebo adresář, který neexistuje, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="cab56-107">An <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown if you try to delete a file or directory that does not exist.</span></span> <span data-ttu-id="cab56-108">Pokud zahrnete zástupný znak do názvu, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> vyvolá <xref:System.IO.IsolatedStorage.IsolatedStorageException> výjimku a <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> vyvolá <xref:System.ArgumentException> výjimku.</span><span class="sxs-lookup"><span data-stu-id="cab56-108">If you include a wildcard character in the name, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> throws an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception, and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> throws an <xref:System.ArgumentException> exception.</span></span>  
  
 <span data-ttu-id="cab56-109"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A>Metoda se nezdařila, pokud adresář obsahuje nějaké soubory nebo podadresáře.</span><span class="sxs-lookup"><span data-stu-id="cab56-109">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> method fails if the directory contains any files or subdirectories.</span></span> <span data-ttu-id="cab56-110">Můžete použít <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> metody a k načtení existujících souborů a adresářů.</span><span class="sxs-lookup"><span data-stu-id="cab56-110">You can use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> methods to retrieve the existing files and directories.</span></span> <span data-ttu-id="cab56-111">Další informace o hledání ve virtuálním systému souborů v úložišti naleznete v tématu [How to: Find existující soubory a adresáře v izolovaném úložišti](how-to-find-existing-files-and-directories-in-isolated-storage.md).</span><span class="sxs-lookup"><span data-stu-id="cab56-111">For more information about searching the virtual file system of a store, see [How to: Find Existing Files and Directories in Isolated Storage](how-to-find-existing-files-and-directories-in-isolated-storage.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cab56-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="cab56-112">Example</span></span>  
 <span data-ttu-id="cab56-113">Následující příklad kódu vytvoří a pak odstraní několik adresářů a souborů.</span><span class="sxs-lookup"><span data-stu-id="cab56-113">The following code example creates and then deletes several directories and files.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.IsolatedStorage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source4.cs#4)]
 [!code-vb[Conceptual.IsolatedStorage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="cab56-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="cab56-114">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>
- [<span data-ttu-id="cab56-115">Izolované úložiště</span><span class="sxs-lookup"><span data-stu-id="cab56-115">Isolated Storage</span></span>](isolated-storage.md)
