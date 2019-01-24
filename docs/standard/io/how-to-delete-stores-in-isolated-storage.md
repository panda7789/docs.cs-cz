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
ms.openlocfilehash: 19a671cac609e79088956ecb4324ebb0a25fb941
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54547396"
---
# <a name="how-to-delete-stores-in-isolated-storage"></a>Postupy: Odstraňování úložišť v izolovaném úložišti
<xref:System.IO.IsolatedStorage.IsolatedStorageFile> Třída poskytuje dvě metody pro odstranění souborů izolovaného úložiště:  
  
-   Metoda instance <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> nepřijímá žádné argumenty a odstranění úložiště, která je volá. Nejsou žádná oprávnění požadovaná pro tuto operaci. Veškerý kód, který můžete získat přístup k úložišti data můžete odstranit některé nebo všechny dovnitř.  
  
-   Statická metoda <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29> přijímá <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> hodnotu výčtu a odstraní všechna úložiště pro uživatele, který spouští kód. Tato operace vyžaduje <xref:System.Security.Permissions.IsolatedStorageFilePermission> oprávnění <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> hodnotu.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje použití statické a instance <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%2A> metody. Třída získá dvě úložiště; jeden je izolováno podle uživatele a sestavení a druhý je izolováno podle uživatele, domény a sestavení. Úložišti uživatele, domény a sestavení se pak odstraní voláním <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove> metoda souboru izolovaného úložiště `isoStore1`. Potom se odstraní všechny zbývající úložiště pro uživatele voláním statické metody <xref:System.IO.IsolatedStorage.IsolatedStorageFile.Remove%28System.IO.IsolatedStorage.IsolatedStorageScope%29>.  
  
 [!code-cpp[Conceptual.IsolatedStorage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source3.cpp#3)]
 [!code-csharp[Conceptual.IsolatedStorage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source3.cs#3)]
 [!code-vb[Conceptual.IsolatedStorage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source3.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [Izolované úložiště](../../../docs/standard/io/isolated-storage.md)
