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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75707824"
---
# <a name="how-to-delete-stores-in-isolated-storage"></a><span data-ttu-id="f694e-102">Postupy: Odstraňování úložišť v izolovaném úložišti</span><span class="sxs-lookup"><span data-stu-id="f694e-102">How to: Delete Stores in Isolated Storage</span></span>
<span data-ttu-id="f694e-103">Třída <xref:System.IO.IsolatedStorage.IsolatedStorageFile> poskytuje dvě metody pro odstranění souborů izolovaného úložiště:</span><span class="sxs-lookup"><span data-stu-id="f694e-103">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class supplies two methods for deleting isolated storage files:</span></span>  
  
- <span data-ttu-id="f694e-104">Metoda <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> instance nepřevezme žádné argumenty a odstraní úložiště, které ji volá.</span><span class="sxs-lookup"><span data-stu-id="f694e-104">The instance method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> does not take any arguments and deletes the store that calls it.</span></span> <span data-ttu-id="f694e-105">Pro tuto operaci nejsou vyžadována žádná oprávnění.</span><span class="sxs-lookup"><span data-stu-id="f694e-105">No permissions are required for this operation.</span></span> <span data-ttu-id="f694e-106">Jakýkoli kód, který může přistupovat k úložišti můžete odstranit některá nebo všechna data uvnitř něj.</span><span class="sxs-lookup"><span data-stu-id="f694e-106">Any code that can access the store can delete any or all the data inside it.</span></span>  
  
- <span data-ttu-id="f694e-107">Statická <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> metoda <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> přebírá hodnotu výčtu a odstraní všechna úložiště pro uživatele, který je spuštěn kód.</span><span class="sxs-lookup"><span data-stu-id="f694e-107">The static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> takes the <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> enumeration value, and deletes all the stores for the user who is running the code.</span></span> <span data-ttu-id="f694e-108">Tato operace <xref:System.Security.Permissions.IsolatedStorageFilePermission> vyžaduje <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> oprávnění pro hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f694e-108">This operation requires <xref:System.Security.Permissions.IsolatedStorageFilePermission> permission for the <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f694e-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="f694e-109">Example</span></span>  
 <span data-ttu-id="f694e-110">Následující příklad kódu ukazuje použití statických <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> metod a metod instance.</span><span class="sxs-lookup"><span data-stu-id="f694e-110">The following code example demonstrates the use of the static and instance <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> methods.</span></span> <span data-ttu-id="f694e-111">Třída získá dva obchody; jeden je izolován pro uživatele a sestavení a druhý je izolován pro uživatele, doménu a sestavení.</span><span class="sxs-lookup"><span data-stu-id="f694e-111">The class obtains two stores; one is isolated for user and assembly and the other is isolated for user, domain, and assembly.</span></span> <span data-ttu-id="f694e-112">Úložiště uživatele, domény a sestavení je pak <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> odstraněno voláním `isoStore1`metody izolovaného souboru úložiště .</span><span class="sxs-lookup"><span data-stu-id="f694e-112">The user, domain, and assembly store is then deleted by calling the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> method of the isolated storage file  `isoStore1`.</span></span> <span data-ttu-id="f694e-113">Potom všechny zbývající obchody pro uživatele jsou odstraněny <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>voláním statické metody .</span><span class="sxs-lookup"><span data-stu-id="f694e-113">Then, all remaining stores for the user are deleted by calling the static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.IsolatedStorage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source3.cs#3)]
 [!code-vb[Conceptual.IsolatedStorage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="f694e-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="f694e-114">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [<span data-ttu-id="f694e-115">Izolované úložiště</span><span class="sxs-lookup"><span data-stu-id="f694e-115">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
