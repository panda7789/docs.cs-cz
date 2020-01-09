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
# <a name="how-to-delete-stores-in-isolated-storage"></a>Postupy: Odstraňování úložišť v izolovaném úložišti
Třída <xref:System.IO.IsolatedStorage.IsolatedStorageFile> poskytuje dvě metody pro odstranění souborů izolovaného úložiště:  
  
- Metoda instance <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> nepřijímá žádné argumenty a odstraňuje úložiště, které ho volá. Pro tuto operaci nejsou požadována žádná oprávnění. Jakýkoli kód, který má přístup k úložišti, může odstranit všechna data, která v něm jsou.  
  
- Statická metoda <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> přebírá hodnotu <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> výčtu a odstraní všechna úložiště pro uživatele, který spouští kód. Tato operace vyžaduje oprávnění <xref:System.Security.Permissions.IsolatedStorageFilePermission> pro hodnotu <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser>.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje použití metod statického a instančního <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A>. Třída získá dvě obchody; jeden je izolovaný pro uživatele a sestavení a druhý je izolovaný pro uživatele, doménu a sestavení. Pak se odstraní úložiště uživatel, doména a sestavení voláním metody <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> souboru izolovaného úložiště `isoStore1`. Všechna zbývající úložiště pro uživatele jsou pak odstraněna voláním statické metody <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>.  
  
 [!code-cpp[Conceptual.IsolatedStorage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.IsolatedStorage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source3.cs#3)]
 [!code-vb[Conceptual.IsolatedStorage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source3.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [Izolované úložiště](../../../docs/standard/io/isolated-storage.md)
