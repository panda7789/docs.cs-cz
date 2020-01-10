---
title: 'Postupy: Odstraňování úložišť v izolovaném úložišti'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- stores, deleting
- data stores, deleting
- deleting stores
- removing stores
- isolated storage, deleting stores
- storing data using isolated storage, deleting stores
- data storage using isolated storage, deleting stores
ms.assetid: 3947e333-5af6-4601-b2f1-24d4d6129cf3
ms.openlocfilehash: 6b1e8e651fd8e18c79dd629c154fb6c4d74243e3
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75707824"
---
# <a name="how-to-delete-stores-in-isolated-storage"></a><span data-ttu-id="95b72-102">Postupy: Odstraňování úložišť v izolovaném úložišti</span><span class="sxs-lookup"><span data-stu-id="95b72-102">How to: Delete Stores in Isolated Storage</span></span>
<span data-ttu-id="95b72-103">Třída <xref:System.IO.IsolatedStorage.IsolatedStorageFile> poskytuje dvě metody pro odstranění souborů izolovaného úložiště:</span><span class="sxs-lookup"><span data-stu-id="95b72-103">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class supplies two methods for deleting isolated storage files:</span></span>  
  
- <span data-ttu-id="95b72-104">Metoda instance <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> nepřijímá žádné argumenty a odstraňuje úložiště, které ho volá.</span><span class="sxs-lookup"><span data-stu-id="95b72-104">The instance method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> does not take any arguments and deletes the store that calls it.</span></span> <span data-ttu-id="95b72-105">Pro tuto operaci nejsou požadována žádná oprávnění.</span><span class="sxs-lookup"><span data-stu-id="95b72-105">No permissions are required for this operation.</span></span> <span data-ttu-id="95b72-106">Jakýkoli kód, který má přístup k úložišti, může odstranit všechna data, která v něm jsou.</span><span class="sxs-lookup"><span data-stu-id="95b72-106">Any code that can access the store can delete any or all the data inside it.</span></span>  
  
- <span data-ttu-id="95b72-107">Statická metoda <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> přebírá hodnotu <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> výčtu a odstraní všechna úložiště pro uživatele, který spouští kód.</span><span class="sxs-lookup"><span data-stu-id="95b72-107">The static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> takes the <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> enumeration value, and deletes all the stores for the user who is running the code.</span></span> <span data-ttu-id="95b72-108">Tato operace vyžaduje oprávnění <xref:System.Security.Permissions.IsolatedStorageFilePermission> pro hodnotu <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser>.</span><span class="sxs-lookup"><span data-stu-id="95b72-108">This operation requires <xref:System.Security.Permissions.IsolatedStorageFilePermission> permission for the <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95b72-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="95b72-109">Example</span></span>  
 <span data-ttu-id="95b72-110">Následující příklad kódu ukazuje použití metod statického a instančního <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A>.</span><span class="sxs-lookup"><span data-stu-id="95b72-110">The following code example demonstrates the use of the static and instance <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> methods.</span></span> <span data-ttu-id="95b72-111">Třída získá dvě obchody; jeden je izolovaný pro uživatele a sestavení a druhý je izolovaný pro uživatele, doménu a sestavení.</span><span class="sxs-lookup"><span data-stu-id="95b72-111">The class obtains two stores; one is isolated for user and assembly and the other is isolated for user, domain, and assembly.</span></span> <span data-ttu-id="95b72-112">Pak se odstraní úložiště uživatel, doména a sestavení voláním metody <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> souboru izolovaného úložiště `isoStore1`.</span><span class="sxs-lookup"><span data-stu-id="95b72-112">The user, domain, and assembly store is then deleted by calling the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> method of the isolated storage file  `isoStore1`.</span></span> <span data-ttu-id="95b72-113">Všechna zbývající úložiště pro uživatele jsou pak odstraněna voláním statické metody <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>.</span><span class="sxs-lookup"><span data-stu-id="95b72-113">Then, all remaining stores for the user are deleted by calling the static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.IsolatedStorage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source3.cs#3)]
 [!code-vb[Conceptual.IsolatedStorage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="95b72-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="95b72-114">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [<span data-ttu-id="95b72-115">Izolované úložiště</span><span class="sxs-lookup"><span data-stu-id="95b72-115">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
