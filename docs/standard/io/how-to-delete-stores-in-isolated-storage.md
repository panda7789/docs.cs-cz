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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cfb6111b080b7c8c359458e3fd1dc99cb0ff3c36
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43877317"
---
# <a name="how-to-delete-stores-in-isolated-storage"></a><span data-ttu-id="15039-102">Postupy: Odstraňování úložišť v izolovaném úložišti</span><span class="sxs-lookup"><span data-stu-id="15039-102">How to: Delete Stores in Isolated Storage</span></span>
<span data-ttu-id="15039-103"><xref:System.IO.IsolatedStorage.IsolatedStorageFile> Třída poskytuje dvě metody pro odstranění souborů izolovaného úložiště:</span><span class="sxs-lookup"><span data-stu-id="15039-103">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class supplies two methods for deleting isolated storage files:</span></span>  
  
-   <span data-ttu-id="15039-104">Metoda instance <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> nepřijímá žádné argumenty a odstranění úložiště, která je volá.</span><span class="sxs-lookup"><span data-stu-id="15039-104">The instance method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> does not take any arguments and deletes the store that calls it.</span></span> <span data-ttu-id="15039-105">Nejsou žádná oprávnění požadovaná pro tuto operaci.</span><span class="sxs-lookup"><span data-stu-id="15039-105">No permissions are required for this operation.</span></span> <span data-ttu-id="15039-106">Veškerý kód, který můžete získat přístup k úložišti data můžete odstranit některé nebo všechny dovnitř.</span><span class="sxs-lookup"><span data-stu-id="15039-106">Any code that can access the store can delete any or all the data inside it.</span></span>  
  
-   <span data-ttu-id="15039-107">Statická metoda <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> přijímá <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> hodnotu výčtu a odstraní všechna úložiště pro uživatele, který spouští kód.</span><span class="sxs-lookup"><span data-stu-id="15039-107">The static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> takes the <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> enumeration value, and deletes all the stores for the user who is running the code.</span></span> <span data-ttu-id="15039-108">Tato operace vyžaduje <xref:System.Security.Permissions.IsolatedStorageFilePermission> oprávnění <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="15039-108">This operation requires <xref:System.Security.Permissions.IsolatedStorageFilePermission> permission for the <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15039-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="15039-109">Example</span></span>  
 <span data-ttu-id="15039-110">Následující příklad kódu ukazuje použití statické a instance <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="15039-110">The following code example demonstrates the use of the static and instance <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> methods.</span></span> <span data-ttu-id="15039-111">Třída získá dvě úložiště; jeden je izolováno podle uživatele a sestavení a druhý je izolováno podle uživatele, domény a sestavení.</span><span class="sxs-lookup"><span data-stu-id="15039-111">The class obtains two stores; one is isolated for user and assembly and the other is isolated for user, domain, and assembly.</span></span> <span data-ttu-id="15039-112">Úložišti uživatele, domény a sestavení se pak odstraní voláním <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> metoda souboru izolovaného úložiště `isoStore1`.</span><span class="sxs-lookup"><span data-stu-id="15039-112">The user, domain, and assembly store is then deleted by calling the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> method of the isolated storage file  `isoStore1`.</span></span> <span data-ttu-id="15039-113">Potom se odstraní všechny zbývající úložiště pro uživatele voláním statické metody <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>.</span><span class="sxs-lookup"><span data-stu-id="15039-113">Then, all remaining stores for the user are deleted by calling the static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.IsolatedStorage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source3.cs#3)]
 [!code-vb[Conceptual.IsolatedStorage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="15039-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="15039-114">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
- [<span data-ttu-id="15039-115">Izolované úložiště</span><span class="sxs-lookup"><span data-stu-id="15039-115">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
