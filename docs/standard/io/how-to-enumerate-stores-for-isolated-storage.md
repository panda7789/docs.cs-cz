---
title: 'Postupy: Vytvoření výčtu úložišť pro izolované úložiště'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- enumerating stores
- data storage using isolated storage, enumerating stores
- storing data using isolated storage, enumerating stores
- stores, enumerating
- isolated storage, enumerating stores
- data stores, enumerating
ms.assetid: 0fcf279a-f241-48f0-8034-2e3d331f1fcb
ms.openlocfilehash: 3ba38093e9e978c89cdb2bb7a584ed9e04c1096d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75707525"
---
# <a name="how-to-enumerate-stores-for-isolated-storage"></a><span data-ttu-id="b55e6-102">Postupy: Vytvoření výčtu úložišť pro izolované úložiště</span><span class="sxs-lookup"><span data-stu-id="b55e6-102">How to: Enumerate Stores for Isolated Storage</span></span>
<span data-ttu-id="b55e6-103">Pomocí statické metody <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> můžete zobrazit výčet všech izolovaných úložišť pro aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="b55e6-103">You can enumerate all isolated stores for the current user by using the  <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> static method.</span></span> <span data-ttu-id="b55e6-104">Tato metoda přebírá hodnotu <xref:System.IO.IsolatedStorage.IsolatedStorageScope> a vrací enumerátor <xref:System.IO.IsolatedStorage.IsolatedStorageFile>.</span><span class="sxs-lookup"><span data-stu-id="b55e6-104">This  method takes an <xref:System.IO.IsolatedStorage.IsolatedStorageScope> value and returns an <xref:System.IO.IsolatedStorage.IsolatedStorageFile> enumerator.</span></span> <span data-ttu-id="b55e6-105">Chcete-li vytvořit výčet úložišť, je nutné mít oprávnění <xref:System.Security.Permissions.IsolatedStorageFilePermission>, které určuje hodnotu <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser>.</span><span class="sxs-lookup"><span data-stu-id="b55e6-105">To enumerate stores, you must have the <xref:System.Security.Permissions.IsolatedStorageFilePermission> permission that specifies the <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> value.</span></span> <span data-ttu-id="b55e6-106">Pokud voláte metodu <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> s hodnotou <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User>, vrátí pole objektů <xref:System.IO.IsolatedStorage.IsolatedStorageFile>, které jsou definovány pro aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="b55e6-106">If you call the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method with the <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> value, it returns an array of <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that are defined for the current user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b55e6-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="b55e6-107">Example</span></span>  
 <span data-ttu-id="b55e6-108">Následující příklad kódu získá úložiště izolované uživatelem a sestavením, vytvoří několik souborů a načte tyto soubory pomocí metody <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A>.</span><span class="sxs-lookup"><span data-stu-id="b55e6-108">The following code example obtains a store that is isolated by user and assembly, creates a few files, and retrieves those files by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source2.cs#2)]
 [!code-vb[Conceptual.IsolatedStorage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="b55e6-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b55e6-109">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [<span data-ttu-id="b55e6-110">Izolované úložiště</span><span class="sxs-lookup"><span data-stu-id="b55e6-110">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
