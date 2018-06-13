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
ms.openlocfilehash: 776984cf1cc17d5c1becc91d4491fa6dbc9e2c17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572324"
---
# <a name="how-to-delete-stores-in-isolated-storage"></a><span data-ttu-id="47ac9-102">Postupy: Odstraňování úložišť v izolovaném úložišti</span><span class="sxs-lookup"><span data-stu-id="47ac9-102">How to: Delete Stores in Isolated Storage</span></span>
<span data-ttu-id="47ac9-103"><xref:System.IO.IsolatedStorage.IsolatedStorageFile> Třída poskytuje dvě metody pro odstraňování souborů izolovaného úložiště:</span><span class="sxs-lookup"><span data-stu-id="47ac9-103">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class supplies two methods for deleting isolated storage files:</span></span>  
  
-   <span data-ttu-id="47ac9-104">Metoda instance <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> nepřijímá žádné argumenty a odstraní úložiště, který volá ho.</span><span class="sxs-lookup"><span data-stu-id="47ac9-104">The instance method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> does not take any arguments and deletes the store that calls it.</span></span> <span data-ttu-id="47ac9-105">Nejsou žádná oprávnění požadovaná pro tuto operaci.</span><span class="sxs-lookup"><span data-stu-id="47ac9-105">No permissions are required for this operation.</span></span> <span data-ttu-id="47ac9-106">Kód, který může přistupovat k úložišti data můžete odstranit nebo všemi uvnitř ho.</span><span class="sxs-lookup"><span data-stu-id="47ac9-106">Any code that can access the store can delete any or all the data inside it.</span></span>  
  
-   <span data-ttu-id="47ac9-107">Statickou metodu <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> trvá <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> hodnota výčtu a odstranění všech úložišť pro uživatele, který běží kódu.</span><span class="sxs-lookup"><span data-stu-id="47ac9-107">The static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> takes the <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> enumeration value, and deletes all the stores for the user who is running the code.</span></span> <span data-ttu-id="47ac9-108">Tato operace vyžaduje <xref:System.Security.Permissions.IsolatedStorageFilePermission> oprávnění <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="47ac9-108">This operation requires <xref:System.Security.Permissions.IsolatedStorageFilePermission> permission for the <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47ac9-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="47ac9-109">Example</span></span>  
 <span data-ttu-id="47ac9-110">Následující příklad kódu ukazuje použití statické a instance <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="47ac9-110">The following code example demonstrates the use of the static and instance <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> methods.</span></span> <span data-ttu-id="47ac9-111">Třída získá dvě úložiště; jedna je pro uživatele a sestavení izolované a druhá je pro uživatele, domény a sestavení izolované.</span><span class="sxs-lookup"><span data-stu-id="47ac9-111">The class obtains two stores; one is isolated for user and assembly and the other is isolated for user, domain, and assembly.</span></span> <span data-ttu-id="47ac9-112">Úložiště uživatele, domény a sestavení je pak odstraní volání <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> metoda souboru izolovaného úložiště `isoStore1`.</span><span class="sxs-lookup"><span data-stu-id="47ac9-112">The user, domain, and assembly store is then deleted by calling the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> method of the isolated storage file  `isoStore1`.</span></span> <span data-ttu-id="47ac9-113">Poté jsou odstraněny všechny zbývající úložiště pro uživatele voláním statickou metodu <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>.</span><span class="sxs-lookup"><span data-stu-id="47ac9-113">Then, all remaining stores for the user are deleted by calling the static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.IsolatedStorage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source3.cs#3)]
 [!code-vb[Conceptual.IsolatedStorage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="47ac9-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="47ac9-114">See Also</span></span>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 [<span data-ttu-id="47ac9-115">Izolované úložiště</span><span class="sxs-lookup"><span data-stu-id="47ac9-115">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
