---
title: "Postupy: Odstraňování souborů a adresářů v izolovaném úložišti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: cd17b85dbdc9315654d042e18d28fbfd0e2dcc52
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-delete-files-and-directories-in-isolated-storage"></a><span data-ttu-id="f8a2d-102">Postupy: Odstraňování souborů a adresářů v izolovaném úložišti</span><span class="sxs-lookup"><span data-stu-id="f8a2d-102">How to: Delete Files and Directories in Isolated Storage</span></span>
<span data-ttu-id="f8a2d-103">Můžete odstranit adresářů a souborů v souboru izolovaného úložiště.</span><span class="sxs-lookup"><span data-stu-id="f8a2d-103">You can delete directories and files within an isolated storage file.</span></span> <span data-ttu-id="f8a2d-104">Názvy souborů a adresářů v rámci úložiště, jsou závislé na operačním systému a je zadána jako relativní vůči kořenovému adresáři virtuálním souborovém systému.</span><span class="sxs-lookup"><span data-stu-id="f8a2d-104">Within a store, file and directory names are operating-system dependent and are specified as relative to the root of the virtual file system.</span></span> <span data-ttu-id="f8a2d-105">Nejsou malá a velká písmena v operačních systémech Windows.</span><span class="sxs-lookup"><span data-stu-id="f8a2d-105">They are not case-sensitive on Windows operating systems.</span></span>  
  
 <span data-ttu-id="f8a2d-106"><xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> Třída poskytuje dvě metody pro odstranění adresářů a souborů: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> a <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>.</span><span class="sxs-lookup"><span data-stu-id="f8a2d-106">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> class supplies two methods for deleting directories and files: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>.</span></span> <span data-ttu-id="f8a2d-107"><xref:System.IO.IsolatedStorage.IsolatedStorageException> Je vyvolána výjimka, pokud se pokusíte odstranit soubor nebo adresář, který neexistuje.</span><span class="sxs-lookup"><span data-stu-id="f8a2d-107">An <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown if you try to delete a file or directory that does not exist.</span></span> <span data-ttu-id="f8a2d-108">Pokud zahrnete zástupný znak v názvu, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> vyvolá <xref:System.IO.IsolatedStorage.IsolatedStorageException> výjimka, a <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> vyvolá <xref:System.ArgumentException> výjimka.</span><span class="sxs-lookup"><span data-stu-id="f8a2d-108">If you include a wildcard character in the name, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> throws an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception, and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> throws an <xref:System.ArgumentException> exception.</span></span>  
  
 <span data-ttu-id="f8a2d-109"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> Metoda selže, pokud adresář obsahuje nějaké soubory nebo podadresáře.</span><span class="sxs-lookup"><span data-stu-id="f8a2d-109">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> method fails if the directory contains any files or subdirectories.</span></span> <span data-ttu-id="f8a2d-110">Můžete použít <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> a <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> metody se načíst existující soubory a adresáře.</span><span class="sxs-lookup"><span data-stu-id="f8a2d-110">You can use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> methods to retrieve the existing files and directories.</span></span> <span data-ttu-id="f8a2d-111">Další informace o hledání virtuálním souborovém systému úložiště najdete v tématu [postupy: hledání existujících souborů a adresářů v izolovaném úložišti](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md).</span><span class="sxs-lookup"><span data-stu-id="f8a2d-111">For more information about searching the virtual file system of a store, see [How to: Find Existing Files and Directories in Isolated Storage](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8a2d-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="f8a2d-112">Example</span></span>  
 <span data-ttu-id="f8a2d-113">Následující příklad kódu vytvoří a odstraní několik adresářů a souborů.</span><span class="sxs-lookup"><span data-stu-id="f8a2d-113">The following code example creates and then deletes several directories and files.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.IsolatedStorage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source4.cs#4)]
 [!code-vb[Conceptual.IsolatedStorage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="f8a2d-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="f8a2d-114">See Also</span></span>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>  
 [<span data-ttu-id="f8a2d-115">Izolované úložiště</span><span class="sxs-lookup"><span data-stu-id="f8a2d-115">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
