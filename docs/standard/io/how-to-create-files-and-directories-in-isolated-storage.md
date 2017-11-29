---
title: "Postupy: Vytváření souborů a adresářů v izolovaném úložišti"
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
helpviewer_keywords:
- directories [.NET Framework], isolated storage
- files [.NET Framework], isolated storage
- isolated storage, creating files and directories
- data stores, creating files and directories
- data storage using isolated storage, creating files and directories
- stores, creating files and directories
- storing data using isolated storage, creating files and directories
ms.assetid: 2ca4d2a4-809b-4f00-bc08-bf4a64d3a5c3
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8b8a48473bf9ac91b89657d00d27031255491353
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-files-and-directories-in-isolated-storage"></a><span data-ttu-id="30fdc-102">Postupy: Vytváření souborů a adresářů v izolovaném úložišti</span><span class="sxs-lookup"><span data-stu-id="30fdc-102">How to: Create Files and Directories in Isolated Storage</span></span>
<span data-ttu-id="30fdc-103">Po získání izolované úložiště, můžete vytvořit adresářů a souborů pro ukládání dat.</span><span class="sxs-lookup"><span data-stu-id="30fdc-103">After you have obtained an isolated store, you can create directories and files for storing data.</span></span> <span data-ttu-id="30fdc-104">V rámci úložiště jsou s ohledem na kořenovém virtuálním souborovém systému zadat názvy souborů a adresářů.</span><span class="sxs-lookup"><span data-stu-id="30fdc-104">Within a store, file and directory names are specified with respect to the root of the virtual file system.</span></span>  
  
 <span data-ttu-id="30fdc-105">Chcete-li vytvořit adresář, použijte <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> metodu instance.</span><span class="sxs-lookup"><span data-stu-id="30fdc-105">To create a directory, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> instance method.</span></span> <span data-ttu-id="30fdc-106">Když zadáte podadresáři adresář, který neexistuje, vytvoří se oba adresáře.</span><span class="sxs-lookup"><span data-stu-id="30fdc-106">If you specify a subdirectory of an directory that doesn't exist, both directories are created.</span></span> <span data-ttu-id="30fdc-107">Pokud určíte adresář, který již existuje, vrátí metoda bez vytvoření adresáře a nedojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="30fdc-107">If you specify a directory that already exists, the method returns without creating a directory, and no exception is thrown.</span></span> <span data-ttu-id="30fdc-108">Ale pokud zadáte název adresáře, který obsahuje neplatné znaky, <xref:System.IO.IsolatedStorage.IsolatedStorageException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="30fdc-108">However, if you specify a directory name that contains invalid characters, an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown.</span></span>  
  
 <span data-ttu-id="30fdc-109">Pokud chcete vytvořit soubor, použijte <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="30fdc-109">To create a file, use  the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="30fdc-110">Operační systém Windows, souboru izolovaného úložiště a adresáře jsou názvy velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="30fdc-110">In the Windows operating system, isolated storage file and directory names are case-insensitive.</span></span> <span data-ttu-id="30fdc-111">To znamená když vytvoříte soubor s názvem `ThisFile.txt`a pak vytvořte jiný soubor s názvem `THISFILE.TXT`, je vytvořen pouze jeden soubor.</span><span class="sxs-lookup"><span data-stu-id="30fdc-111">That is, if you create a file named `ThisFile.txt`, and then create another file named `THISFILE.TXT`, only one file is created.</span></span> <span data-ttu-id="30fdc-112">Název souboru udržuje jeho původní velká a malá písmena pro účely zobrazení.</span><span class="sxs-lookup"><span data-stu-id="30fdc-112">The file name keeps its original casing for display purposes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30fdc-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="30fdc-113">Example</span></span>  
 <span data-ttu-id="30fdc-114">Následující příklad kódu ukazuje postup vytvoření souborů a adresářů v izolovaném úložišti.</span><span class="sxs-lookup"><span data-stu-id="30fdc-114">The following code example illustrates how to create files and directories in an isolated store.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source.cs#1)]
 [!code-vb[Conceptual.IsolatedStorage#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="30fdc-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="30fdc-115">See Also</span></span>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>  
 [<span data-ttu-id="30fdc-116">Izolovaná úložiště</span><span class="sxs-lookup"><span data-stu-id="30fdc-116">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
