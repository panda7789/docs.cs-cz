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
# <a name="how-to-enumerate-stores-for-isolated-storage"></a>Postupy: Vytvoření výčtu úložišť pro izolované úložiště
Pomocí statické metody <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> můžete zobrazit výčet všech izolovaných úložišť pro aktuálního uživatele. Tato metoda přebírá hodnotu <xref:System.IO.IsolatedStorage.IsolatedStorageScope> a vrací enumerátor <xref:System.IO.IsolatedStorage.IsolatedStorageFile>. Chcete-li vytvořit výčet úložišť, je nutné mít oprávnění <xref:System.Security.Permissions.IsolatedStorageFilePermission>, které určuje hodnotu <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser>. Pokud voláte metodu <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> s hodnotou <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User>, vrátí pole objektů <xref:System.IO.IsolatedStorage.IsolatedStorageFile>, které jsou definovány pro aktuálního uživatele.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu získá úložiště izolované uživatelem a sestavením, vytvoří několik souborů a načte tyto soubory pomocí metody <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A>.  
  
 [!code-csharp[Conceptual.IsolatedStorage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source2.cs#2)]
 [!code-vb[Conceptual.IsolatedStorage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [Izolované úložiště](../../../docs/standard/io/isolated-storage.md)
