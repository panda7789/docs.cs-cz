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
# <a name="how-to-delete-stores-in-isolated-storage"></a>Postupy: Odstraňování úložišť v izolovaném úložišti
Třída <xref:System.IO.IsolatedStorage.IsolatedStorageFile> poskytuje dvě metody pro odstranění souborů izolovaného úložiště:  
  
- Metoda <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> instance nepřevezme žádné argumenty a odstraní úložiště, které ji volá. Pro tuto operaci nejsou vyžadována žádná oprávnění. Jakýkoli kód, který může přistupovat k úložišti můžete odstranit některá nebo všechna data uvnitř něj.  
  
- Statická <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> metoda <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> přebírá hodnotu výčtu a odstraní všechna úložiště pro uživatele, který je spuštěn kód. Tato operace <xref:System.Security.Permissions.IsolatedStorageFilePermission> vyžaduje <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> oprávnění pro hodnotu.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje použití statických <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> metod a metod instance. Třída získá dva obchody; jeden je izolován pro uživatele a sestavení a druhý je izolován pro uživatele, doménu a sestavení. Úložiště uživatele, domény a sestavení je pak <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> odstraněno voláním `isoStore1`metody izolovaného souboru úložiště . Potom všechny zbývající obchody pro uživatele jsou odstraněny <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>voláním statické metody .  
  
 [!code-cpp[Conceptual.IsolatedStorage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.IsolatedStorage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source3.cs#3)]
 [!code-vb[Conceptual.IsolatedStorage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source3.vb#3)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [Izolované úložiště](../../../docs/standard/io/isolated-storage.md)
